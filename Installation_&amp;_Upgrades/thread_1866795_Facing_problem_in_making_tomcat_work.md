---
title: "Facing problem in making tomcat work"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by Sanjaya Kumar on 2011-10-21
Hi,
I am new to ubuntu and tomcat.
I have installed tomcat6 from ubuntu software center. Then I have added JAVA_HOME and PATH variable in .bashrc.
export JAV_HOME=/usr/lib/jvm/java-6-openjdk
export PATH=$PATH:$JAVA_HOME/bin

when i tried to run startup.sh in /usr/share/tomcat6/bin it shown an error /usr/share/tomcat6/logs/catalina.log is not present. Then i created the dir structure. Then I again run startup.sh. This time no error came. But, when i tried [http://localhost:8080](http://localhost:8080) in browser tomcat didn't come up. When i tried shutdown.sh it shown below message.

Using CATALINA_BASE:   /usr/share/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /usr/share/tomcat6/bin/bootstrap.jar
Oct 22, 2011 8:31:24 AM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop: 
java.io.FileNotFoundException: /usr/share/tomcat6/conf/server.xml (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:137)
	at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:393)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:338)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:416)


Kindly help me to make tomcat work.

---

