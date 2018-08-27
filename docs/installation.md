# 安装说明
该项目在 release 分支做了新项目的编译测试：[![build status][build-badge]][build]，可以作为参考。

## 引入项目
```bash
npm i react-native-baidumap-sdk
```
或
```bash
yarn add react-native-baidumap-sdk
```

## 配置

### Android
```bash
react-native link react-native-baidumap-sdk
```
[获取 Android 开发密钥](http://lbsyun.baidu.com/index.php?title=iossdk/guide/create-project/ak)，
在 AndroidManifest 中添加：
```xml
<application>
    <meta-data
      android:name="com.baidu.lbsapi.API_KEY"
      android:value="开发密钥" />
</application>
```

### iOS
1.添加百度项目文件。如果安装成功，下载本地址文件用react-native-baidumap-sdk/lib/ios，替换node_modules/react-native-baidumap-sdk/lib/ios文件夹，那么在node_modules/react-native-baidumap-sdk/lib/ios 文件夹下一定有一个.xcodeproj文件。把这个文件拖到你的 XCode 工程下（通常拖到 XCode 的Libraries分组里）.再点击你的主工程文件，选择General在linked Frameworks and Libraries 中，把刚才所添加进去的.xcodeproj对应的静态库(libRNBaiduMap.a 文件）添加进去。

2.把对应的对应百度地图库加入到主项目中（共10个），点击你的主工程文件，选择General，有linked Frameworks and Libraries ,点击下面【+】号。详细库有如下：MobileCoreServices.framework，CoreLocation.framework，QuartzCore.framework	，OpenGLES.framework	，SystemConfiguration.framework	统计信息，用于改善产品
，CoreGraphics.framework	，Security.framework	是为了统计app信息使用，libsqlite3.0.tbd（xcode7以前为 libsqlite3.0.dylib），	V2.9.0新增的系统库，使用V2.9.0及以上版本的地图SDK，务必增加，CoreTelephony.framework	V2.9.0新增的系统库，使用V2.9.0及以上版本的地图SDK，务必增加，libstdc++.6.0.9.tbd（xcode7以前为libstdc++.6.0.9.dylib）

3.添加百度库到主项目中，点击你的主工程文件，选择General，有linked Frameworks and Libraries ,点击下面【+】号，在弹出框中选择【Add Other】,弹出文件选择框，进到node_modules/react-native-baidumap-sdk/lib/ios目录中选中如下文件
BaiduMapAPI_Base.framework	基础包，使用SDK任何功能都需导入，其他分包可按需导入
BaiduMapAPI_Map.framework	地图功能包
BaiduMapAPI_Search.framework	检索功能包
BaiduMapAPI_Cloud.framework	云检索功能包
BaiduMapAPI_Utils.framework	工具功能包
BaiduMapAPI_Location.framework 定位
BaiduMapAPI_Radar.framework
点击【确定】。

4.添加对应的framework路径到项目中，选择General，有Build Settings 里面 有个Framework Search Paths,双击对应行的右边，弹出可以编辑内容，在新的一行中加入$(PROJECT_DIR)/../node_modules/react-native-baidumap-sdk/lib/ios  

以上操作完毕，即可运行，看是否能成功运行，若能运行，则添加成功。

其中 iOS 需要提供密钥作为参数（Android 密钥必须写在 Manifest），当然，你也可以用官方提供的方法进行初始化。

[获取 iOS 开发密钥](http://lbsyun.baidu.com/index.php?title=iossdk/guide/create-project/ak)。

```javascript
import { Initializer } from 'react-native-baidumap-sdk'

Initializer.init('iOS 开发密钥').catch(e => console.error(e))
```

android 下会自动忽略 init 的参数，如果应用只支持 android 则可以不带参数。

另外，android 错误码请参考[错误码对照表](http://lbsyun.baidu.com/index.php?title=androidsdk/guide/addition-func/errorcode)。

[build-badge]: https://travis-ci.org/qiuxiang/react-native-baidumap-sdk.svg?branch=release
[build]: https://travis-ci.org/qiuxiang/react-native-baidumap-sdk
