---
iOS Monkey配置
---
FastMonkey：https://github.com/zhangzhao4444/Fastmonkey
1.clone工程：
$ git clone https://github.com/zhangzhao4444/Fastmonkey.git
2.安装第三方库：
$ cd /Users/xxxxx/Fastmonkey/XCTestWD-master
$ carthage update
3.Xcode相关配置：
（1）导入缺失文件
（2）签名
（3）删除XCTestWD-Bridging-Header.h
（4）添加 #import "XCTestWDApplication.h" 

4.启动监听服务：
$ iproxy 8001 8001
5.运行工程：
$ cd /Users/xxxxx/Fastmonkey/XCTestWD-master/XCTestWD
$ xcodebuild -project XCTestWD.xcodeproj \
           -scheme XCTestWDUITests \
           -destination 'platform=iOS,name=test' \
           XCTESTWD_PORT=8001 \
           clean test
PS:需要修改name为测试设备名称
6.执行Monkey：
$ curl -X POST -H "Content-Type:application/json" \
              -d "{\"desiredCapabilities\":{\"deviceName\":\"test\",\"platformName\":\"iOS\", \"bundleId\":\"com.vipkid.vipkidParentDev\”,\”autoAcceptAlerts\":\"false\"}}" \
              http://127.0.0.1:8001/wd/hub/monkey
PS:需要修改bundleId和deviceName


 

