---
title: "tomcat connection refused"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by jas1291 on 2011-10-22
hi i need to install tomcat7........i am getting the following error
```
sudo /etc/init.d/tomcat7 restart
Using CATALINA_BASE:   /usr/local/tomcat7
Using CATALINA_HOME:   /usr/local/tomcat7
Using CATALINA_TMPDIR: /usr/local/tomcat7/temp
Using JRE_HOME:        /usr/lib/jvm/java-6-sun/jre
Using CLASSPATH:       /usr/local/tomcat7/bin/bootstrap.jar:/usr/local/tomcat7/bin/tomcat-juli.jar
22 Oct, 2011 6:52:59 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop: 
java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:351)
	at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:213)
	at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:200)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
	at java.net.Socket.connect(Socket.java:529)
	at java.net.Socket.connect(Socket.java:478)
	at java.net.Socket.<init>(Socket.java:375)
	at java.net.Socket.<init>(Socket.java:189)
	at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:457)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:371)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:452)
Using CATALINA_BASE:   /usr/local/tomcat7
Using CATALINA_HOME:   /usr/local/tomcat7
Using CATALINA_TMPDIR: /usr/local/tomcat7/temp
Using JRE_HOME:        /usr/lib/jvm/java-6-sun/jre
Using CLASSPATH:       /usr/local/tomcat7/bin/bootstrap.jar:/usr/local/tomcat7/bin/tomcat-juli.jar

```

---

