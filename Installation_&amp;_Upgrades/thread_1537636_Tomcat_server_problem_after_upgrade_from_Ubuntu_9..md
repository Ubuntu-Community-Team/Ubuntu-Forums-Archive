---
title: "Tomcat server problem after upgrade from Ubuntu 9.4 to 9.10"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by wlbragg on 2010-07-23
I should have caught this during the upgrade, I saw the potential problem but failed to write it down. All my applications served by Tomcat fail to load. Catalina logs show the following error for each app

Error deploying configuration descriptor msgboard.xml

The complete error for an individual application is

> Jul 23, 2010 5:13:38 PM org.apache.catalina.startup.HostConfig deployDescriptor
SEVERE: Error deploying configuration descriptor msgboard.xml
java.lang.NoSuchMethodError: org.apache.naming.resources.BaseDirContext.setCacheObjectMaxSize(I)V
	at org.apache.catalina.core.StandardContext.setResources(StandardContext.java:1901)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4210)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.access$000(ContainerBase.java:123)
	at org.apache.catalina.core.ContainerBase$PrivilegedAddChild.run(ContainerBase.java:145)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:769)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:526)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1258)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:722)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:443)
	at org.apache.catalina.core.StandardService.start(StandardService.java:516)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:583)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:288)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.commons.daemon.support.DaemonLoader.start(DaemonLoader.java:177)


Again, during the upgrade a warning popped up that each app would need to be spelled out in some configuration file SOMEWHERE because of a change in security! Would someone be so kind as to direct me as to where and how this would be accomplished. I apologizes for not being able to find this out on my own but have looked and can't find it. I'm pretty sure anyone proficient with Tomcat on Linux will know what and where these changes need to be made. Or if anyone knows if and where there is a log of all communication during the upgrade I might be able to figure this out on my own. Is there such a log kept during an upgrade? Also if this question would be more appropriate in the Server Platforms forum I will do that. Thank You!

---

### Post by wlbragg on 2010-07-24
Anyone know if there are logs of all communication, warnings and/or messages during an upgrade of Ubuntu? If so what are their file names and where are they located? This was an upgrade from Ubuntu 9.04 to 9.10.

Never mind about the location of the upgrade logs, I found logs at var/log/dist-upgrade. Unfortunately there wasn't anything in them that helped. The upgrade did replace web.xml, context.xml and server.xml but there were no changes made to them.

---

### Post by wlbragg on 2011-01-21
Just a bump as I still haven't found out what happened with this. I have been all over the web and have found this to be a major problem with Ubuntu upgrades but no one seems to have the answer. Hoping this reaches the right person.

---

### Post by wlbragg on 2011-01-22
A bit more info if this helps, I went back to square one with the default install of Apache2, Tomcat6 and jk_connector through SPM no examples, docs etc. I still get the configuration descriptor error on the ROOT.

> 
Jan 22, 2011 11:56:01 AM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory ROOT
Jan 22, 2011 11:56:01 AM org.apache.catalina.startup.HostConfig deployDirectory
SEVERE: Error deploying web application directory ROOT
java.lang.NoSuchMethodError: org.apache.naming.resources.BaseDirContext.setCacheObjectMaxSize(I)V
	at org.apache.catalina.core.StandardContext.setResources(StandardContext.java:1912)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4248)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:526)
	at org.apache.catalina.startup.HostConfig.deployDirectory(HostConfig.java:1041)
	at org.apache.catalina.startup.HostConfig.deployDirectories(HostConfig.java:964)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:502)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:722)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:443)
	at org.apache.catalina.core.StandardService.start(StandardService.java:516)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:593)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)

Specifically 

> 
java.lang.NoSuchMethodError: org.apache.naming.resources.BaseDirContext.setCacheObjectMaxSize(I)V


Since the original post I have upgraded to Ubuntu 10.04 LTS - the Lucid Lynx. I have tried default.jre, openjdk-6.jre and sun-java6.jre all with no change. 

FYI: the configdeployDirectories are

/etc/tomcat6/Catalina/localhost
/var/lib/tomcat6/conf/Catalina/localhost

and have appropriate .xml configurations for the apps

Any ideas or help would be greatly appreciated.

---

### Post by wlbragg on 2011-01-23
I figured it out, problem solved. 

FYI: Short version of solution

There were at least three separate naming.resources.jar files on the system in different places. Unfortunately because I was in a hurry I did two different things that may have corrected it. I also didn't examine each version to see if they were different or corrupt. 

Solution was,

Changed CLASSPATH to point at a newer version of java 
Deleted naming.resources.jar I knew wasn't necessary out of /usr/share/java. 

Again, I was in a hurry to solve (after 3 years) and did both steps at the same time. So I'm not sure which one fixed it. Bottom line is, for those of you at my (limited) experience level, make sure you read those error messages closely. They will usually contain enough info to get you to the root of the problem IE: 
> java.lang.NoSuchMethodError: org.apache.naming.resources.BaseDirContext.setCach eObjectMaxSize(I)V 
was the error message in Catalina logs that clued me in to the specific problem and eventual solution.

---

