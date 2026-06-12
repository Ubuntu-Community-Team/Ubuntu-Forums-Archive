---
title: "Unable to run Eclipse"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by debtaru on 2008-02-24
I get the following message when I launch eclipse:



JVM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx512m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_ 1.0.1.R33x_v20070828.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /opt/eclipse/eclipse
-name Eclipse
--launcher.library /opt/eclipse/plugins/org.eclipse.equinox.launcher. gtk.linux.x86_1.0.2.R331_v20071019/eclipse_1021.so
-startup /opt/eclipse/plugins/org.eclipse.equinox.launcher_ 1.0.1.R33x_v20070828.jar
-exitdata 200014
-clean
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx512m
-jar /opt/eclipse/plugins/org.eclipse.equinox.launcher_ 1.0.1.R33x_v20070828.jar



I have installed eclipse-jee-europa-fall2-linux

I have eclipse installed at /opt/eclipse directory

Please help me resolve.

---

### Post by ckrul on 2008-02-24
Check [this post]("http://www.eclipsezone.com/eclipse/forums/m92225818.html") in the EclipseZone forum. Seems mixing 32 and 64 bit version could be causing this.

---

