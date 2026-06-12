---
title: "jetty installation"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Miguel de Melo on 2010-01-14
I have been trying to install Jetty using apt-get for the last couple of days unsuccessfully on a Ubuntu 9.10 server. I have created a VM with Ubuntu 9.10 server to elaborate on this test case following the lack of progress on a real server. Is probably important to note that I can run jetty using the maven jetty plugin in the same distro, but I was looking at deploying my app to a more standard jetty installation using just a war file.

I have sun java 6 installed with "apt-get install sun-java6-jdk"
```
$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)

```

I initially started by just doing a :
```
$ sudo apt-get install jetty
```

But also tried (with similar outcome) to follow the instructions in Jetty Debian Packages Official debs page [http://docs.codehaus.org/display/JETTY/Debian+Packages]("http://docs.codehaus.org/display/JETTY/Debian+Packages"). Interesting to note that the instructions listed jetty6 as a package to be installed, but apt-get could not find it, so I had to install the "jetty" package instead. 

```
$ sudo apt-get install libjetty6-java
$ sudo apt-get install libjetty6-extra-java
$ sudo apt-get install jetty
```

I then started jetty using the standard service start syntax
```
$ sudo service jetty start
 * Starting Jetty servlet engine. jetty
 * Jetty servlet engine started, reachable on http://ubuntu:8080/. jetty
   ...done.

```

I then tried to access the default jetty site from a web browser external to the VM and using lynx in the vm on [http://localhost:8080/](http://localhost:8080/) and [http://10.211.55.9:8080/](http://10.211.55.9:8080/), and get no response:

```
$ ls -lha /usr/share/jetty/logs
total 16K
drwxr-x---  2 jetty adm   4.0K 2010-01-14 00:07 .
drwxr-xr-x 12 root  root  4.0K 2010-01-14 00:05 ..
-rw-r--r--  1 jetty jetty    0 2010-01-14 00:07 2010_01_14.request.log
-rw-r--r--  1 jetty jetty 2.2K 2010-01-14 00:07 2010_01_14.stderrout.log
-rw-r--r--  1 jetty adm    329 2010-01-14 00:07 out.log

```

/usr/share/jetty/logs/2010_01_14.request.log  **is empty**

/usr/share/jetty/logs/2010_01_14.stderrout.log 
```
2010-01-14 00:07:40.993::INFO:  jetty-6.1.x
2010-01-14 00:07:41.040::INFO:  Deploy /etc/jetty/contexts/javadoc.xml -> org.mortbay.jetty.handler.ContextHandler@16b13c7{/javadoc,file:/usr/share/jetty/javadoc}
2010-01-14 00:07:41.069::WARN:  failed org.mortbay.jetty.deployer.WebAppDeployer@1cdeff: java.lang.IllegalArgumentException: No such webapps resource file:/usr/share/java/webapps
2010-01-14 00:07:41.225::INFO:  NO JSP Support for , did not find org.apache.jasper.servlet.JspServlet
2010-01-14 00:07:41.358::INFO:  Opened /var/log/jetty/2010_01_14.request.log
2010-01-14 00:07:41.377::INFO:  Started SelectChannelConnector@:8080
2010-01-14 00:07:41.378::WARN:  failed Server@12d3205: java.lang.IllegalArgumentException: No such webapps resource file:/usr/share/java/webapps
2010-01-14 00:07:41.378::WARN:  EXCEPTION 
java.lang.IllegalArgumentException: No such webapps resource file:/usr/share/java/webapps
	at org.mortbay.jetty.deployer.WebAppDeployer.scan(WebAppDeployer.java:155)
	at org.mortbay.jetty.deployer.WebAppDeployer.doStart(WebAppDeployer.java:139)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:50)
	at org.mortbay.jetty.Server.doStart(Server.java:201)
	at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:50)
	at org.mortbay.xml.XmlConfiguration.main(XmlConfiguration.java:985)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.mortbay.start.Main.invokeMain(Main.java:194)
	at org.mortbay.start.Main.start(Main.java:534)
	at org.mortbay.jetty.start.daemon.Bootstrap.start(Bootstrap.java:30)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.commons.daemon.support.DaemonLoader.start(DaemonLoader.java:177)

```

/usr/share/jetty/logs/out.log
```
SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.
2010-01-14 00:07:40.502::INFO:  Logging to STDERR via org.mortbay.log.StdErrLog
2010-01-14 00:07:40.689::INFO:  Redirecting stderr/stdout to /var/log/jetty/2010_01_14.stderrout.log

```

```
$ nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-01-14 01:04 GMT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 998 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
8080/tcp open  http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.23 seconds

```

I do not get the port 8080 listed when I nmap the boxes ip address though, not sure if it's related
```
$ nmap 10.211.55.9

Starting Nmap 5.00 ( http://nmap.org ) at 2010-01-14 01:05 GMT
Interesting ports on 10.211.55.9:
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds

```

```
$ netstat -an | grep LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp6       0      0 127.0.0.1:8080          :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     20266    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     2622     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     20382    /var/run/avahi-daemon/socke
```

---

### Post by mighdoll on 2010-01-14
try this:
```
sudo mkdir -p /usr/share/java/webapps

```

and then restart jetty:
```
sudo /etc/init.d/jetty stop
sudo /etc/init.d/jetty start
```

That seems to do the trick for me.

---

### Post by Miguel de Melo on 2010-01-14
Thanks that got read of the java.lang.IllegalArgumentException, but it still complains about not having JSP support. 
```
NO JSP Support for , did not find org.apache.jasper.servlet.JspServlet
```

I tried to activate jasper but for some reason jasper has been removed from the archives and I found a request to raise a bug for that effect here [https://answers.launchpad.net/ubuntu/+source/jikes/+question/94834]("https://answers.launchpad.net/ubuntu/+source/jikes/+question/94834")

I also get 
```
SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
```

in the mean time I guess I'll have to try the stand alone distribution instead, as I have run out of ideas.

---

### Post by efleming969 on 2010-02-21
Miguel,

Did you have any luck with this. I'm running into the same problems.

The state of the this jetty package is broken in IMO.  I've spent more that 6 hours trying to get anything to work properly.

I install the tomcat6 package and it took two minutes to get the default application to respond.

---

### Post by noSelf on 2010-02-22
i was running into the same problems and am glad i found this thread before spending more than 40 min trying.

Download, install, and run of the .zip distribution took under 5 min. i don't mind some duplication of jars on my system to have a clean install distributed by the project itself.

---

### Post by elmdm on 2010-05-13
I've managed to get past this using:

sudo apt-get install libjetty-extra

---

