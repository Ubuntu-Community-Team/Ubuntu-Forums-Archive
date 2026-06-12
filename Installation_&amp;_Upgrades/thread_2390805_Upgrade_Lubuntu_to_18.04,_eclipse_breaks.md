---
title: "Upgrade Lubuntu to 18.04, eclipse breaks"
date: 2018-05-02
forum: Installation &amp; Upgrades
---

### Post by mrwhoohoo on 2018-05-02
Was previously at 16.04. Upgraded to 18.0.4.

When I start Eclipse, it responds :
An error has occurred.  See the log file /home/username/.eclipse/org.eclipse.platform_3.8_155965261/configuration/1525293593597.log

Log file reports:

!SESSION Wed May 02 21:10:36 BST 2018 ------------------------------------------
!ENTRY org.eclipse.equinox.launcher 4 0 2018-05-02 21:10:36.845
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.ClassNotFoundException: org.eclipse.core.runtime.adaptor.EclipseStarter
	at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:466)
	at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:566)
	at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:499)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:626)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
	at org.eclipse.equinox.launcher.Main.main(Main.java:1414)

Any ideas how to fix this.

I'm a newbie with Ubuntu.

Thanks

Steve

---

### Post by thiago.n.costa.86 on 2018-06-02
I'm having the same problem. Did anyone fix this?

---

