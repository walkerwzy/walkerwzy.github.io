---
layout: post
title: flash media stream server错误解决
categories:
- default
tags: []
published: true
comments: true
---
<p>别人电脑和公司服务器全都成功了，就是我电脑不行，一直报下面这个错误，折腾好久，找到一点解决方法，反正把我自己的问题是解决了<br />Asynchronous I/O operation failed (Failed to attach to completion port: Parameter incorrect. 87)<br /><br />相信一般会上网来搜的人，都是查了自己了防火墙才来的，但是假如你确实忘记了检查，请查一下你的防火墙先，是不是把1935端口挡住了，（假设你安装的时候没有更改端口，另外有的版本还默认了80端口）<br /><strong>解决方法一（不管原因，绕道解决）：</strong><br />1，打开安装目录下conf目录下的fms.ini文件，找到ADAPTOR.HOSTPORT，把80端口添加进去<br />2，直接在所有rtmp协议后面加个t，即变成rtmpt；<br />3，再次测试，成功<br />附，80端口大家都在抢，如果不想加，那么就这么使用rtmp://localhost/live=&gt;rtmpt://localhost:1935/live，我是通过了,<br />方法是死的，人是活的，写到这里应该明白根据自己的机器怎么去测试和修改了<br /><strong>解决方法二（只对本人而言）：</strong><br />不要忘了杀软也可能是帮凶，网上查了很多资料，其中有一个最大的罪魁祸首就是NOD32，假如你也碰到相同的问题，正好也在用NOD32，那么恭喜，可能你现在能解决了<br />打开NOD32，IMON，设定，其他，排除，把FMSEdge.exe写进去，基本上可以，笔者为了保险，同时把同目录下几个exe也全写进去了，<br />但跟踪端口，在我播放视频的时候确实只有FMSEdge有流量吞吐<br />此外还查到有人norton卸载了才能解决问题的，禁用什么的都无效，本人没用诺顿，所以不予评说，仅把其列出来作为您的参考<br />这种情况下，那个80端口也可以删掉，rtmp也不要改成rtmpt(用rtmpt据说速度会变慢，所以还是从根本解决的好)<br /><strong>解决方法三（官方）：</strong><br /><a href="http://kb2.adobe.com/cps/402/kb402920.html">http://kb2.adobe.com/cps/402/kb402920.html</a><br />官方说明Note: It is possible that RTMPT and RTMPS connections work fine, even on identical ports. 但下面有更详细的原因及解决，建议点进去，但是那是推测的socket错误，并不符合我的情况，但可能您碰到的是这样</p>
