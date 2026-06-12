---
title: "Installation Trouble"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by noobed on 2011-12-07
I installed Ubuntu 11.04 on my PC a few days ago and really liked it. Since yesterday i have been trying to install Vuze but the following message is being posted. Any help is appreciated.


file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/lib/java/swt-gtk-3.5.1.jar ; file:/home/user/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.gudy.azureus2.ui.common.Main.directLaunch(Main.java:229)
    at org.gudy.azureus2.ui.common.Main.main(Main.java:132)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:662)
Caused by: java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3555 or swt-pi-gtk in swt.library.path, java.library.path or the jar file
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:254)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:159)
    at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:131)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:79)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:59)
    at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:111)
    at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
    at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
    ... 12 more
Start fails:
com.aelitis.azureus.core.AzureusCoreException: Azureus core already instantiated
    at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:120)
    at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
    at org.gudy.azureus2.ui.common.Main.main(Main.java:160)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:662)

Thanks in Advance.

---

### Post by 2F4U on 2011-12-07
This component seems to be missing/not installed or it is not included in the path

> Caused by: java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3555 or  swt-pi-gtk in swt.library.path, java.library.path or the jar file

---

### Post by BC59 on 2011-12-07
It's a bug:

[https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/700602](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/700602)
[https://bugs.launchpad.net/ubuntu/+source/tuxguitar/+bug/703618](https://bugs.launchpad.net/ubuntu/+source/tuxguitar/+bug/703618)

The proposed workaround:

```
sudo apt-get remove libswt-gtk-3.5-jni libswt-gtk-3.5-java
```


```
sudo apt-get install libswt-gtk-3.6-jni libswt-gtk-3.6-java
```

---

### Post by noobed on 2011-12-08
Got this reply... :(

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libswt-gtk-3.6-jni
E: Couldn't find any package by regex 'libswt-gtk-3.6-jni'
E: Unable to locate package libswt-gtk-3.6-java
E: Couldn't find any package by regex 'libswt-gtk-3.6-java'

What should i do???

---

### Post by BC59 on 2011-12-08
The problem is Java. I don't know if you can follow the instructions and install Java 7:

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

### Post by noobed on 2011-12-10
> **BC59 said:**
> The problem is Java. I don't know if you can follow the instructions and install Java 7:

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

Thanks a lot works fine now... :D:KS:KS:)

---

### Post by BC59 on 2011-12-10
Please mark the thread as solved, from the thread tools close to the top of the page.

---

