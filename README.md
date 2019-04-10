# ScriptDemo
一份 React Native 脚本


不知不觉用RN 开发了快有半年多时间了。
![alt](https://www.moretime.vip/upload/2019/04/2oi54vk44ah4tq69kp9m39ptkg.jpg)

-------笔者本身是做安卓的 。那么在安卓中都是习惯了命令打包。或者是adb 来操作。那么在rn 中有时候不是很习惯 就自己自定义了一套脚本。 脚本的名字和功能都是可以由大家随便改的 所以你可以改成你喜欢的名字来方便你记忆或者 少打几个字母。
   ![](https://www.moretime.vip/upload/2019/04/ucvgo604jcif5o523fr6d9bakb.jpg)

-------一般在我们 init 项目之后我们会有android ios app 等目录。在其中的根目录和android 他们同级别的目录有一个package.json 文件是一个编译配置的文件。其中有定义了
我们的项目名称 版本号 脚本命令 以及dependencies 里面 是属于在打包会打进去一些引用的库 以及devDependencies 中是我们开发运行是会打包进去的库。



---------我们的自定义脚本就在scripts 里面操作 。也许你稍微注意点就会发觉我们官方采用的npm start 就在里面 有一个"start": "node node_modules/react-native/local-cli/cli.js start",
![alt](https://www.moretime.vip/upload/2019/04/ut2cq2uhfqiedq0hj2ivr1tas1.jpg)

--------所以我自己又自定义了一些命令我们通过npm + 我们自定义的名称就可以启动了
1. npm bundle-ios  :将所以的文件打包成js 以及我们引入的html 资源和图片资源打包到ios 项目的realse 目录下
  "bundle-ios":"react-native bundle --entry-file index.js --platform ios --dev false --bundle-output ./ios/release_ios/main.jsbundle --assets-dest ./ios/release_ios/",
  
2. npm bundle-android : 打包安卓的debug 包 最后的目录会在android/app/build/output/debug/apk/目录下
    "bundle-android":"cd android&&./gradlew assemblerelease"

3. npm ios-list : 查看当前的ios  模拟器设备列表 可以选择你启动的ios 模拟器版本 因为默认启动的是iphone 6 我们可以查看到设备 然后启动的时候来指定版本 
 "ios-list":"xcrun simctl list devices",

4. npm android-list :查看链接到电脑上安卓的设备 
    "android-list":"cd android&&adb devices",
    
5.  npm ios: 打包运行到iphone x 模拟器上 我喜欢X   
    "ios":"react-native run-ios --simulator 'iPhone X'",
    
6. npm android: 打包安卓debug 包并且安装到手机上    
    "android":"cd android&&./gradlew assembledebug&&cd app/build/outputs/apk/debug&&adb install app-debug.apk",
    
7. npm i-android : 安装android的debug 包
   "i-android":"cd android/app/build/outputs/apk/debug&&adb install app-debug.apk",
  
8.  npm unandroid  卸载你的android包 需要你的安卓包名 在- - - - android/app/src/main/AndroidManifest.xml 文件中 头部 package 拷贝进来就行
    "unandroid":"adb uninstall  com.xxxx",
