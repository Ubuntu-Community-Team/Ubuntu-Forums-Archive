---
title: "Tomcat native lib - libtcnative?"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by davclark on 2007-02-15
I don't know if the installation forums is the place for this, but as of Edgy, there seems to be no package for supporting the Tomcat native lib - which improves performance by using the Apache Portable Runtime.  A reference for this lib is here:

[http://tomcat.apache.org/tomcat-5.5-doc/apr.html](http://tomcat.apache.org/tomcat-5.5-doc/apr.html)

It should be pretty straightforward to include as a package, no?

Cheers,
Dav

---

### Post by vgillestad on 2007-05-08
Hi!

I've just upgraded to "Feisty Fawn", and I can't get the libtcnative working. This is what I have done:
apt-get install libssl-dev libapr1-dev
./configure --with-apr=/usr/bin/apr-config

and in the ..java-1.5.0-sun/jre/lib/i386 library I put a link to the "libtcnative" file:
ln -s /usr/local/apr/lib/libtcnative-1.so libtcnative-1.so

This all worked perfect when I worked on "Edgy". But when I now on "Feisty Fawn" start my tomcat server I get these errors:

java.lang.Exception: Socket bind failed: [22] Invalid argument
	at org.apache.tomcat.util.net.AprEndpoint.init(AprEndpoint.java:575)
	at org.apache.coyote.http11.Http11AprProtocol.init(Http11AprProtocol.java:115)
	at org.apache.catalina.connector.Connector.initialize(Connector.java:1016)
	at org.apache.catalina.core.StandardService.initialize(StandardService.java:580)
	at org.apache.catalina.core.StandardServer.initialize(StandardServer.java:791)
	at org.apache.catalina.startup.Catalina.load(Catalina.java:503)
	at org.apache.catalina.startup.Catalina.load(Catalina.java:523)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.apache.catalina.startup.Bootstrap.load(Bootstrap.java:266)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:431)
May 8, 2007 8:06:12 PM org.apache.catalina.startup.Catalina load
SEVERE: Catalina.start
LifecycleException:  Protocol handler initialization failed: java.lang.Exception: Socket bind failed: [22] Invalid argument
	at org.apache.catalina.connector.Connector.initialize(Connector.java:1018)
	at org.apache.catalina.core.StandardService.initialize(StandardService.java:580)
	at org.apache.catalina.core.StandardServer.initialize(StandardServer.java:791)
	at org.apache.catalina.startup.Catalina.load(Catalina.java:503)
	at org.apache.catalina.startup.Catalina.load(Catalina.java:523)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.apache.catalina.startup.Bootstrap.load(Bootstrap.java:266)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:431)

---

### Post by rked on 2007-05-10
I had this problem too - for me the issue was IPv6 was enabled.  Disabling IPv6 made this error go away.  There are a ton of forum posts about disabling IPv6, but the basic idea is to change the line:

alias net-pf-10 ipv6  (in /etc/modprobe.d/aliases)

to

alias net-pf-10 off

---

### Post by yunpu on 2007-05-11
Thanks ! 
I disabled ipv6. Now the Tomcat can run native library.

---

### Post by vgillestad on 2007-05-11
Thanks! after having ipv6 disabled it also worked for me. Note: I had to restart my computer.

---

### Post by candrewswpi on 2008-03-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/204005](https://bugs.launchpad.net/ubuntu/+bug/204005) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've entered a bug in launchpad asking for tomcat-native to be packaged. Anyone want to help?

---

