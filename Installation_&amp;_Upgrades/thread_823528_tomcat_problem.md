---
title: "tomcat problem"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2008-06-09
```

root@server:/usr/local/apache-tomcat-4.1.34/conf# /etc/init.d/tomcat restart
Using CATALINA_BASE:   /usr/local/apache-tomcat-4.1.34
Using CATALINA_HOME:   /usr/local/apache-tomcat-4.1.34
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-4.1.34/temp
Using CATALINA_OUT:    /usr/local/apache-tomcat-4.1.34/logs/catalina.out
Using JAVA_HOME:       /usr/lib/jvm/java-1.5.0-sun
Catalina.stop: java.net.ConnectException: Connection refused
java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
        at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
        at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
        at java.net.Socket.connect(Socket.java:520)
        at java.net.Socket.connect(Socket.java:470)
        at java.net.Socket.<init>(Socket.java:367)
        at java.net.Socket.<init>(Socket.java:180)
        at org.apache.catalina.startup.Catalina.stop(Catalina.java:527)
        at org.apache.catalina.startup.Catalina.execute(Catalina.java:347)
        at org.apache.catalina.startup.Catalina.process(Catalina.java:129)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:150)
Using CATALINA_BASE:   /usr/local/apache-tomcat-4.1.34
Using CATALINA_HOME:   /usr/local/apache-tomcat-4.1.34
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-4.1.34/temp
Using CATALINA_OUT:    /usr/local/apache-tomcat-4.1.34/logs/catalina.out
Using JAVA_HOME:       /usr/lib/jvm/java-1.5.0-sun


```

what is wrong with this?

thx

---

### Post by mitjab on 2008-06-09
any idea?

---

### Post by sgordon on 2008-06-13
Hi

Quick thought, is Tomcat actually running??

Since you are using 'restart', the first thing it tries to do is 'stop' Tomcat, which you can see from the error stacktrace. The lower part of your log looks like Tomcat starts up afterwards ok!

What is the problem you are actually having, since the log itself isn't an issue in itself?

Si

---

