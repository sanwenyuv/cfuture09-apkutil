Run on windows with JRE, it's used to get the application information of a apk file, include icon, package name, app name, permission needed, feature needed, and so on.

apkUtil是一个用来解析apk安装包的工具，通过它可以获取一个安装包的图标、程序名、所需android平台，权限等信息，并将其转换为java对象。该工具依赖于aapt.exe工具，目前仅支持在windows环境上运行。
程序在运行时，会创建一个进程，用于运行aapt。默认的aapt的路径为jar包相对目录的lib/aapt。如果路径更改，请使用setAaptPath方法。

新的版本使用方法如下：
```java

try {
String demo = "E:/androidApk/2012/05/百宝工具箱/1.0/signed/Toolbox-360.apk";
if (args.length > 0) {
demo = args[0];
}
ApkInfo apkInfo = new ApkUtil().getApkInfo(demo);
System.out.println(apkInfo);
} catch (Exception e) {
e.printStackTrace();
}
```
输出结果如下：
```


ApkInfo [versionCode=1,
versionName=1.0,
packageName=cfuture.xiaozhi.toolbox,
minSdkVersion=null,
usesPermissions=[android.permission.ACCESS_FINE_LOCATION, android.permission.ACCESS_NETWORK_STATE, android.permission.ACCESS_WIFI_STATE, android.permission.INTERNET, android.permission.MOUNT_UNMOUNT_FILESYSTEMS, android.permission.READ_LOGS, android.permission.READ_PHONE_STATE, android.permission.WRITE_EXTERNAL_STORAGE, android.permission.READ_EXTERNAL_STORAGE],
sdkVersion=4,
targetSdkVersion=null,
applicationLable=百宝工具箱,
applicationIcons={application-icon-240=res/drawable-hdpi/toolbox.png, application-icon-160=res/drawable-mdpi/toolbox.png, application-icon-120=res/drawable-ldpi/toolbox.png},
applicationIcon=res/drawable-mdpi/toolbox.png,
impliedFeatures=[Feature [feature=android.hardware.location, implied=requested a location access permission], Feature [feature=android.hardware.location.gps, implied=requested android.permission.ACCESS_FINE_LOCATION permission], Feature [feature=android.hardware.wifi, implied=requested android.permission.ACCESS_WIFI_STATE, android.permission.CHANGE_WIFI_STATE, or android.permission.CHANGE_WIFI_MULTICAST_STATE permission], Feature [feature=android.hardware.touchscreen, implied=assumed you require a touch screen unless explicitly made optional], Feature [feature=android.hardware.screen.landscape, implied=one or more activities have specified a landscape orientation], Feature [feature=android.hardware.screen.portrait, implied=one or more activities have specified a portrait orientation]],
features=[android.hardware.location, android.hardware.location.gps, android.hardware.wifi, android.hardware.touchscreen, android.hardware.screen.landscape, android.hardware.screen.portrait]]
```

注意：以前的apkUtil 0.x版本已经弃用，原因是其效率低下，且获得的信息较少。