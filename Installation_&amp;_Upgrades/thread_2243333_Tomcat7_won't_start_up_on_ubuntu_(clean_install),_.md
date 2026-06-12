---
title: "Tomcat7 won't start up on ubuntu (clean install), permission denied"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by Varga_Edmond on 2014-09-08
I [COLOR=#000000][FONT=Arial]have a clean ubuntu installation (14) and try to run Tomcat7. I have installed it via terminal, run the "sudo service tomcat7 start" command which should start tomcat, but when I try to open: localhost:8080, the welcome index page is not loading and I get a 404 error (file not found). The 8080 port is not opened either, it seem like some kind of permission problem.

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Please help me out. 
Thanks!
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Catalina.out (log), gives the following error:

[/FONT][/COLOR]
```
Sep 08, 2014 9:52:46 AM org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat7/common/classes], exists: [false], isDirectory: [false], canRead: [false]
Sep 08, 2014 9:52:46 AM org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat7/common], exists: [false], isDirectory: [false], canRead: [false]
Sep 08, 2014 9:52:47 AM org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat7/server/classes], exists: [false], isDirectory: [false], canRead: [false]
Sep 08, 2014 9:52:47 AM org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat7/server], exists: [false], isDirectory: [false], canRead: [false]
Sep 08, 2014 9:52:47 AM org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat7/shared/classes], exists: [false], isDirectory: [false], canRead: [false]
Sep 08, 2014 9:52:47 AM org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat7/shared], exists: [false], isDirectory: [false], canRead: [false]
Sep 08, 2014 9:52:52 AM org.apache.coyote.AbstractProtocol init
INFO: Initializing ProtocolHandler ["http-bio-8080"]
Sep 08, 2014 9:52:52 AM org.apache.coyote.AbstractProtocol init
SEVERE: Failed to initialize end point associated with ProtocolHandler ["http-bio-8080"]
java.net.SocketException: Permission denied
    at java.net.ServerSocket.createImpl(ServerSocket.java:308)
    at java.net.ServerSocket.getImpl(ServerSocket.java:257)
    at java.net.ServerSocket.bind(ServerSocket.java:376)
    at java.net.ServerSocket.<init>(ServerSocket.java:237)
    at java.net.ServerSocket.<init>(ServerSocket.java:181)
    at org.apache.tomcat.util.net.DefaultServerSocketFactory.createSocket(DefaultServerSocketFactory.java:49)
    at org.apache.tomcat.util.net.JIoEndpoint.bind(JIoEndpoint.java:397)
    at org.apache.tomcat.util.net.AbstractEndpoint.init(AbstractEndpoint.java:640)
    at org.apache.coyote.AbstractProtocol.init(AbstractProtocol.java:434)
    at org.apache.coyote.http11.AbstractHttp11JsseProtocol.init(AbstractHttp11JsseProtocol.java:119)
    at org.apache.catalina.connector.Connector.initInternal(Connector.java:978)
    at org.apache.catalina.util.LifecycleBase.init(LifecycleBase.java:102)
    at org.apache.catalina.core.StandardService.initInternal(StandardService.java:559)
    at org.apache.catalina.util.LifecycleBase.init(LifecycleBase.java:102)
    at org.apache.catalina.core.StandardServer.initInternal(StandardServer.java:813)
    at org.apache.catalina.util.LifecycleBase.init(LifecycleBase.java:102)
    at org.apache.catalina.startup.Catalina.load(Catalina.java:638)
    at org.apache.catalina.startup.Catalina.load(Catalina.java:663)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:606)
    at org.apache.catalina.startup.Bootstrap.load(Bootstrap.java:280)
    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:454)


Sep 08, 2014 9:52:52 AM org.apache.catalina.core.StandardService initInternal
SEVERE: Failed to initialize connector [Connector[HTTP/1.1-8080]]
org.apache.catalina.LifecycleException: Failed to initialize component [Connector[HTTP/1.1-8080]]
    at org.apache.catalina.util.LifecycleBase.init(LifecycleBase.java:106)
    at org.apache.catalina.core.StandardService.initInternal(StandardService.java:559)
    at org.apache.catalina.util.LifecycleBase.init(LifecycleBase.java:102)
    at org.apache.catalina.core.StandardServer.initInternal(StandardServer.java:813)
    at org.apache.catalina.util.LifecycleBase.init(LifecycleBase.java:102)
    at org.apache.catalina.startup.Catalina.load(Catalina.java:638)
    at org.apache.catalina.startup.Catalina.load(Catalina.java:663)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:606)
    at org.apache.catalina.startup.Bootstrap.load(Bootstrap.java:280)
    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:454)
Caused by: org.apache.catalina.LifecycleException: Protocol handler initialization failed
    at org.apache.catalina.connector.Connector.initInternal(Connector.java:980)
    at org.apache.catalina.util.LifecycleBase.init(LifecycleBase.java:102)
    ... 12 more
Caused by: java.net.SocketException: Permission denied
    at java.net.ServerSocket.createImpl(ServerSocket.java:308)
    at java.net.ServerSocket.getImpl(ServerSocket.java:257)
    at java.net.ServerSocket.bind(ServerSocket.java:376)
    at java.net.ServerSocket.<init>(ServerSocket.java:237)
    at java.net.ServerSocket.<init>(ServerSocket.java:181)
    at org.apache.tomcat.util.net.DefaultServerSocketFactory.createSocket(DefaultServerSocketFactory.java:49)
    at org.apache.tomcat.util.net.JIoEndpoint.bind(JIoEndpoint.java:397)
    at org.apache.tomcat.util.net.AbstractEndpoint.init(AbstractEndpoint.java:640)
    at org.apache.coyote.AbstractProtocol.init(AbstractProtocol.java:434)
    at org.apache.coyote.http11.AbstractHttp11JsseProtocol.init(AbstractHttp11JsseProtocol.java:119)
    at org.apache.catalina.connector.Connector.initInternal(Connector.java:978)
    ... 13 more


Sep 08, 2014 9:52:52 AM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 4826 ms
Sep 08, 2014 9:52:52 AM org.apache.catalina.core.StandardService startInternal
INFO: Starting service Catalina
Sep 08, 2014 9:52:52 AM org.apache.catalina.core.StandardEngine startInternal
INFO: Starting Servlet Engine: Apache Tomcat/7.0.52 (Ubuntu)
Sep 08, 2014 9:52:52 AM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory /var/lib/tomcat7/webapps/ROOT
Sep 08, 2014 9:53:17 AM org.apache.catalina.startup.Catalina start
INFO: Server startup in 24972 ms
Sep 08, 2014 9:53:17 AM org.apache.catalina.core.StandardServer await
SEVERE: StandardServer.await: create[localhost:8005]: 
java.net.SocketException: Permission denied
    at java.net.ServerSocket.createImpl(ServerSocket.java:308)
    at java.net.ServerSocket.getImpl(ServerSocket.java:257)
    at java.net.ServerSocket.bind(ServerSocket.java:376)
    at java.net.ServerSocket.<init>(ServerSocket.java:237)
    at org.apache.catalina.core.StandardServer.await(StandardServer.java:426)
    at org.apache.catalina.startup.Catalina.await(Catalina.java:777)
    at org.apache.catalina.startup.Catalina.start(Catalina.java:723)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:606)
    at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:321)
    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:455)


Sep 08, 2014 9:53:17 AM org.apache.coyote.AbstractProtocol pause
INFO: Pausing ProtocolHandler ["http-bio-8080"]
Sep 08, 2014 9:53:17 AM org.apache.catalina.core.StandardService stopInternal
INFO: Stopping service Catalina
Sep 08, 2014 9:53:17 AM org.apache.coyote.AbstractProtocol stop
INFO: Stopping ProtocolHandler ["http-bio-8080"]
Sep 08, 2014 9:53:17 AM org.apache.coyote.AbstractProtocol destroy
INFO: Destroying ProtocolHandler ["http-bio-8080"]



```

---

### Post by nerdtron on 2014-09-08
404 means you have a missing page isn't it? Have you checked which is the root directory for tomcat and see it there is welcome page present?

Post the output of
```
sudo netstat -tulpn
sudo ufw status
telnet localhost 8080
```

---

