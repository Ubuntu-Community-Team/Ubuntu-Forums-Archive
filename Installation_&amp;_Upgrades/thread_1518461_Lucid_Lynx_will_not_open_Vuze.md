---
title: "Lucid Lynx will not open Vuze"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by JThompson118 on 2010-06-26
I was running 9.04, but finally upgraded to Lucid Lynx a few days ago. However, now it won't run Vuze. ```
[warning] /usr/bin/vuze: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/home/jeffrey/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.gudy.azureus2.ui.common.Main.directLaunch(Main.java:229)
    at org.gudy.azureus2.ui.common.Main.main(Main.java:132)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Listener
    at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:111)
    at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
    at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
    ... 12 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Listener
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at com.aelitis.azureus.launcher.classloading.PrimaryClassloader.loadClass(PrimaryClassloader.java:103)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
    ... 15 more
Start fails:
com.aelitis.azureus.core.AzureusCoreException: Azureus core already instantiated
    at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:120)
    at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
    at org.gudy.azureus2.ui.common.Main.main(Main.java:160)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:636)
 
```
Is what comes up when I try opening it in the terminal. I've tried patching it up with a few things I found on the forums, such as ```
sudo ln -s swt-gtk-3.5.1.jar swt.jar
 
```, but it says the file already exists, and Vuze still will not budge. How do I get my program running again?

---

### Post by JThompson118 on 2010-06-26
I should also note that I DID upgrade Java.

---

### Post by eltonw on 2010-06-26
> **JThompson118 said:**
> I should also note that I DID upgrade Java.

" /usr/bin/vuze: Unable to locate swt in /usr/share/java"  indicates that something is missinge in your java installation. You could remove java then re-install. Either OpenJava, or Sun Java should do. (I tend to use Synaptic, rather than the console).

HTH...):P

---

### Post by JThompson118 on 2010-06-26
Ugh. Removed all my Java, and my Vuze. Then Reinstalled Java, then Vuze. Still not responsive, still identical code as before. Does my computer just not like me? :P

---

### Post by wilee-nilee on 2010-06-27
In case you can't resolve this, deluge is another nice setup.

If you run a sudo apt-get (program) purge it might get vuze up and running again. Some programs have to be purged.

---

### Post by lewile1 on 2010-07-18
Symbolic link must be made in the /usr/share/java directory, not the /usr/lib/java directory.

I ran into the same problem, and did the purge but that did not work. I tried to locate the swt file, but only found the /usr/lib/java/swt-gtk-3.5.1.jar file. I symlinked it to /usr/share/java/swt.jar and voila, up and running.

"lewile1@lewile1-desktop:~$ sudo ln -s /usr/lib/java/swt-gtk-3.5.1.jar /usr/share/java/swt.jar"

---

### Post by pierrem-m on 2010-08-24
I ran the command given by lewile1 above and it fixed this annoying problem for me. Many thanks indeed for the help!!!!!! 

Has anyone any thoughts on why this happened with the 10.04 upgrade?

---

### Post by bejinx on 2011-06-17
> **lewile1 said:**
> Symbolic link must be made in the /usr/share/java directory, not the /usr/lib/java directory.

I ran into the same problem, and did the purge but that did not work. I tried to locate the swt file, but only found the /usr/lib/java/swt-gtk-3.5.1.jar file. I symlinked it to /usr/share/java/swt.jar and voila, up and running.

"lewile1@lewile1-desktop:~$ sudo ln -s /usr/lib/java/swt-gtk-3.5.1.jar /usr/share/java/swt.jar"


6/17/2011  I also just upgrade my asrock 330 ion htpc xbmc live install to 10.04 lucid.  I share files privately with friends now and then, using vuze.  I tried purging/re-instaling vuze, didnt work. the symlink above did, thanks!! --bej

---

