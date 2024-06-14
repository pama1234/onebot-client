
<div align="center">

# OneBot Client

_✨ 基于java开发的 [OneBot](https://github.com/howmanybots/onebot/blob/master/README.md) 协议客户端✨_

</div>
<hr>
<p align="center">
    <a href="https://github.com/cnlimiter/onebot-client/issues"><img src="https://img.shields.io/github/issues/cnlimiter/onebot-sdk?style=flat" alt="issues" /></a>
    <a href="https://maven.nova-committee.cn/#/releases/cn/evolvefield/oneBotClient/OneBot-Client"><img src="https://jitci.com/gh/cnlimiter/onebot-sdk/svg"></a>
    <a href="https://github.com/cnlimiter/onebot-client/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-GPLV3-green" alt="License"></a>
    <a href="https://github.com/howmanybots/onebot"><img src="https://img.shields.io/badge/OneBot-v11-blue?style=flat&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABABAMAAABYR2ztAAAAIVBMVEUAAAAAAAADAwMHBwceHh4UFBQNDQ0ZGRkoKCgvLy8iIiLWSdWYAAAAAXRSTlMAQObYZgAAAQVJREFUSMftlM0RgjAQhV+0ATYK6i1Xb+iMd0qgBEqgBEuwBOxU2QDKsjvojQPvkJ/ZL5sXkgWrFirK4MibYUdE3OR2nEpuKz1/q8CdNxNQgthZCXYVLjyoDQftaKuniHHWRnPh2GCUetR2/9HsMAXyUT4/3UHwtQT2AggSCGKeSAsFnxBIOuAggdh3AKTL7pDuCyABcMb0aQP7aM4AnAbc/wHwA5D2wDHTTe56gIIOUA/4YYV2e1sg713PXdZJAuncdZMAGkAukU9OAn40O849+0ornPwT93rphWF0mgAbauUrEOthlX8Zu7P5A6kZyKCJy75hhw1Mgr9RAUvX7A3csGqZegEdniCx30c3agAAAABJRU5ErkJggg=="></a>
</p>
<p align="center">
    <a href="#">文档</a> | 
    <a href="#">QuickStart</a>
</p>


# QuickStart

### 使用api进行请求
```java
public class WebSocketClientTest {
    public static OneBotClient onebot;
    public static void sendApi(String[] args) {
        onebot = OneBotClient.create(new BotConfig("ws://127.0.0.1:8080"))//创建websocket客户端
                .open()//连接onebot服务端
                .registerEvents(new EventListeners());//注册事件监听器

        onebot.getBot().sendGroupMsg(123456, MsgUtils.builder().text("123").build(), true);//发送群消息
        GroupMemberInfoResp sender = onebot.getBot().getGroupMemberInfo(123456, 123456, false).getData();//获取响应的群成员信息
        System.out.println(sender.toString());//打印
    }
}
```

### 事件监听示例
```java
public class EventListeners implements Listener{
    @SubscribeEvent
    public void onGroup(GroupMessageEvent event){
        System.out.println(event);
    }
}

public class WebSocketClientTest {
    public static OneBotClient onebot;
    public static void main(String[] args){
        onebot = OneBotClient.create(new BotConfig("ws://127.0.0.1:8080"))//创建websocket客户端
                .open()//连接onebot服务端
                .registerEvents(new EventListeners());//注册事件监听器
    }

    public static void stopped() {
        if (onebot != null) onebot.close();
    }
}
```

# Client

OneBot-Client 以 [OneBot-v11](https://github.com/howmanybots/onebot/tree/master/v11/specs) 标准协议进行开发，兼容所有支持正向WebSocket的OneBot协议端

| 项目地址                                                                              | 核心作者           | 备注                                                                    |
|-----------------------------------------------------------------------------------|----------------|-----------------------------------------------------------------------|
| [Overflow](https://github.com/MrXiaoM/Overflow)                                   | MrXiaoM        | 实现 mirai 的无缝迁移                                                        |
| [Lagrange.Core](https://github.com/LagrangeDev/Lagrange.Core)                     | NepPure        | C#实现 By Konata.Core                                                   |
| [OpenShamrock](https://github.com/whitechi73/OpenShamrock)                        | whitechi73     | Xposed框架hook实现                                                        |
| [Gensokyo](https://github.com/Hoshinonyaruko/Gensokyo)                            | Hoshinonyaruko | 基于官方api 轻量 原生跨平台                                                      |
| [LLOnebot](https://github.com/LLOneBot/LLOneBot)                                  | linyuchen      | 使用[LiteLoaderQQNT](https://github.com/LiteLoaderQQNT/LiteLoaderQQNT)  |

# Credits

* [OneBot](https://github.com/botuniverse/onebot)

# License

This product is licensed under the GNU General Public License version 3. The license is as published by the Free
Software Foundation published at https://www.gnu.org/licenses/gpl-3.0.html.

Alternatively, this product is licensed under the GNU Lesser General Public License version 3 for non-commercial use.
The license is as published by the Free Software Foundation published at https://www.gnu.org/licenses/lgpl-3.0.html.

Feel free to contact us if you have any questions about licensing or want to use the library in a commercial closed
source product.

# Thanks

Thanks [JetBrains](https://www.jetbrains.com/?from=onebot-client) Provide Free License Support OpenSource Project

[<img src="https://mikuac.com/images/jetbrains-variant-3.png" width="200"/>](https://www.jetbrains.com/?from=onebot-client)

## Stargazers over time

[![Stargazers over time](https://starchart.cc/cnlimiter/onebot-client.svg)](https://starchart.cc/cnlimiter/onebot-client)

