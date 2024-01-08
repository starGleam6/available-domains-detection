# 前置页部署说明

## 名词说明

- 前置页，也就是此项目。一般为轻量级没有特征的网站，不容易被封。一般只设一个稳定的域名。假设域名为 https://v2board.com
- 跳转页，是你通过此项目要跳转的目标网站。一般是机场或成人类这种容易被封的网站。一般会有多个域名。假设域名为 https://demo.v2board.com 、https://demo2.v2board.com

## 部署

本前置页是纯前端页面，在宝塔，网站，添加站点，新建一个站点即可。这里需要说明的是，PHP 版本选择纯静态。然后此文件夹下的所有文件拖到新建站点文件夹内即可。

## 添加和修改检测网址

data.json 文件中可以修改和添加你的网站地址。这里需要注意的是，如果你的跳转页的前端是 hash 路径，比如 https://demo.v2board.com/#/ 那么请把 /#/ 写上，后面如果有参数方便拼接。

增加了检测链接和跳转链接分开配置的功能，可以分别设置 checkUrl 和 jumpUrl。以应对网站首页设置了 CloudFlare 质询或者 CDN 之类的机器人拦截。checkUrl 建议配置不会出发质询的链接，比如接口 API Url，jumpUrl 建议配置站点首页。具体详细配置例子参见 data.json。

## 路径跳转

该前置页支持跳转路径。假设你的网站是 https://demo.v2board.com/#/ （注意，如果面板前端是有 hash 路径的，请加上方便跳转），跳转路径是 register，邀请码 9527。

你的前置页地址是： https://v2board.com ，那么可以让用户访问 https://v2board.com?path=register&code=9527 ，这样用户就会跳转到 https://demo.v2board.com/#/register?code=9527 。

## 跨域问题

如果部署后，想要跳转到的网站有跨域的问题。首先要确保跳转的这个网站是你的。需要在跳转的网站项目的 Nginx 配置中填写下面的配置以解决此问题。此处的 https://v2board.com 是你的前置页。

add_header 'Access-Control-Allow-Origin' 'https://v2board.com';

## Crisp 客服

前置页项目设定检测超过 60 秒会停止检测，并弹出提示框让其通过 Crisp 联系客服。Crisp ID 在 index.html 搜索 window.CRISP_WEBSITE_ID 进行填写。如果自己有使用其他客服系统，可以修改此处的客服对接代码，替换成自己的即可。

## 联系我

如果有跨域或其他问题不会解决，可以联系星闪 [https://t.me/StarGleam](https://t.me/StarGleam) 支付费用解决。
