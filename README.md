Cordova 支付宝支付插件
======

## 最新更新

1. 增加callback
2. 默认使用自动安装的方法
3. 去除了对URL Scheme的依赖

## 支持的系统

* iOS
* Android

## 自动安装（Cordova > v5.1.1）

	cordova plugin add $CORDOVA_PLUGIN_DIR --variable PARTNER_ID=[你的商户PID可以在账户中查询] --variable SELLER_ACCOUNT=[你的商户支付宝帐号] --variable PRIVATE_KEY=[你生成的private key]

**注意**：PRIVATE_KEY的值是生成的key文件的内容，需要去掉——-BEGIN PRIVAT KEY——-和——-END PRIVATE KEY——-，以及**空格**和**换行**

## 使用方法
```
window.alipay.pay({
	tradeNo: tradeNo,
	subject: "测试标题",
	body: "我是测试内容",
	price: 0.02,
	notifyUrl: "http://your.server.notify.url"
}, function(){alert("success")}, function(errorMsg){alert(errorMsg)});
```
### 参数说明

* tradeNo 这个是支付宝需要的，应该是一个唯一的ID号
* subject 这个字段会显示在支付宝付款的页面
* body 订单详情，没找到会显示哪里
* price 价格，支持两位小数

第一个callback是成功之后的callback，第二个callback是失败之后的callback，会有errorMsg传出来。

## 手动安装
1. 使用git命令将插件下载到本地，并标记为$CORDOVA_PLUGIN_DIR

		git clone https://github.com/charleyw/cordova-plugin-alipay.git && cd cordova-plugin-alipay && export CORDOVA_PLUGIN_DIR=$(pwd)
		
2. 修改$CORDOVA_PLUGIN_DIR/plugin.xml，删除下面这一行：

		<preference name="PRIVATE_KEY"/>
		
2. 修改$CORDOVA_PLUGIN_DIR/plugin.xml，将

		<preference name="private_key" value="$PRIVATE_KEY" />
改成

		<preference name="PRIVATE_KEY" value="你生成的private key的内容"/>

	**注意**：总共有两处
3. 安装

		cordova plugin add $CORDOVA_PLUGIN_DIR --variable PARTNER_ID=[你的商户PID可以在账户中查询] --variable SELLER_ACCOUNT=[你的商户支付宝帐号]


## Liscense

© 2015 Wang Chao. This code is distributed under the MIT license.
