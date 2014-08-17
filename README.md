gfwiptables
===========

A router script against GFW DNS pollution.

本脚本针对GFW的污染IP进行过滤

首先你要有一个路由器

然后你的路由器能加载脚本

本脚本可以完美解决GFW的DNS污染问题

不能解决IP封锁问题

必须关闭内置DNS功能

必须要有国外DNS(OpenDNS, Google DNS, etc)

推荐设置1国内+1国外DNS

设置为初始化脚本或者防火墙脚本

每行IP不得超过10个

发现新的污染IP请及时通知

具体原理和与DNSMASQ的区别：

正常的DNS查询
客户端发送DNS查询->（接受）服务器返回正确结果

污染的DNS查询
客户端发送DNS查询->（接受）GFW返回伪造结果->（丢弃）服务器返回正确结果

iptables过滤
客户端发送DNS查询->（过滤并丢弃）GFW返回伪造结果->（接受）服务器返回正确结果

dnsmasq过滤
客户端发送DNS查询->（接受并过滤）GFW返回伪造结果->（丢弃）服务器返回正确结果
