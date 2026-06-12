---
title: "On upgrading to Ubuntu 10.04 I can no longer open manually installed bittorent client"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by laeg_ on 2010-06-26
When trying from the link which was in the applications menu, and manually from terminal I receive the following errors:

```
laeg@skyrocket:~$ vuze
[warning] /usr/bin/vuze: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/home/laeg/
changeLocale: *Default Language* != English (Ireland). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Ireland)' (en_IE), using 'English (default)'
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
laeg@skyrocket:~$ azureus
[warning] /usr/bin/azureus: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/home/laeg/
changeLocale: *Default Language* != English (Ireland). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Ireland)' (en_IE), using 'English (default)'
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

I have since tried the [HOWTO: Install Azureus (newest, non-repo way)]("http://ubuntuforums.org/showthread.php?t=144546")  method of installing Vuze/Azureus, which I think is what I set up for 9.04, and also a synaptic complete removal and reinstall which didn't work.

I have an .azureus folder in my home dir which I would like to keep because it contains my settings and half downloaded torrents etc.

I would be happy to use the the synaptic packaged version of Vuze because it is much more up to date than it has been in the past. 

How would I go about this?

---

### Post by teejaybee on 2010-06-26
Looks to me like after the upgrade, the custom version of vuze you  installed no longer has access to the right versions of the libraries it  needs to run.

But, just in case, have you tried moving your config directory just to make sure it isn't causing problems?

mv .azureus .azureus-old

Otherwise, after you have completely uninstalled all versions of vuze, if you type 'which vuze" does it list anything? If it does, there is still a binary in your PATH somewhere. Find it and remove it, then apt-get install vuze. If it runs fine now, exit out of the program, delete the .azureus directory it made and move the -old directory back to its proper name and away you go.

---

### Post by laeg_ on 2010-06-26
> **teejaybee said:**
> Looks to me like after the upgrade, the custom version of vuze you  installed no longer has access to the right versions of the libraries it  needs to run.

But, just in case, have you tried moving your config directory just to make sure it isn't causing problems?

mv .azureus .azureus-old

Otherwise, after you have completely uninstalled all versions of vuze, if you type 'which vuze" does it list anything? If it does, there is still a binary in your PATH somewhere. Find it and remove it, then apt-get install vuze. If it runs fine now, exit out of the program, delete the .azureus directory it made and move the -old directory back to its proper name and away you go.

Thanks for the input but your solution thus far hasn't worked so I'm doing it again and noting each step as I do.

Moved .azureus to .azureus-old but it still wouldn't start.

Completely removing Vuze 4.3.0.6-1 with Synaptic Package Manager's GUI.

Removing entry from usr/bin/ and the symlink in the applications menu.

```
laeg@skyrocket:~$ which vuze
laeg@skyrocket:~$ which azureus
laeg@skyrocket:~$ 

```

Deleting an .azureus dir from home.

Installing Vuze 4.3.0.6-1 via Synaptic Package Manager's GUI.

No link now created in Applications > Internet menu. Possibly resulting because of everything I've been doing?

```
laeg@skyrocket:~$ vuze
The program 'vuze' is currently not installed.  You can install it by typing:
sudo apt-get install vuze
laeg@skyrocket:~$ azureus
The program 'azureus' is currently not installed.  You can install it by typing:
sudo apt-get install azureus
laeg@skyrocket:~$ sudo apt-get install vuze
[sudo] password for laeg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vuze is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-x nvidia-185-kernel-source libxine1-misc-plugins libxcb-xv0
  libxine1-bin libxine1-ffmpeg libxcb-shape0 libxine1-plugins libxcb-shm0
  libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

What next friend?

---

### Post by teejaybee on 2010-06-26
You may have to log in and out again for your PATH to work correctly again, either that, or there's something up with your package db. Maybe try:

sudo apt-get purge vuze ; sudo apt-get install vuze?

If vuze is listed as being installed after that and still wont run from the command line as vuze, maybe another command is used to start it? Or something else is broken?

Maybe you could grab the latest source tarball and install it manually again?

---

### Post by laeg_ on 2010-06-26
> **teejaybee said:**
> You may have to log in and out again for your PATH to work correctly again, either that, or there's something up with your package db. Maybe try:

sudo apt-get purge vuze ; sudo apt-get install vuze?

If vuze is listed as being installed after that and still wont run from the command line as vuze, maybe another command is used to start it? Or something else is broken?

Maybe you could grab the latest source tarball and install it manually again?

Purged both vuze and azureus and then tried reinstalling:

```
laeg@skyrocket:~$ azureus
[warning] /usr/bin/azureus: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/home/laeg/
changeLocale: *Default Language* != English (Ireland). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Ireland)' (en_IE), using 'English (default)'
DEBUG::Sun Jun 27 02:14:37 IST 2010  Successfully migrated key management
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
laeg@skyrocket:~$ vuze
[warning] /usr/bin/vuze: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/home/laeg/
changeLocale: *Default Language* != English (Ireland). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Ireland)' (en_IE), using 'English (default)'
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

Back to square 1.

But if I do the manual install it won't neatly create application menu entries and update automatically. Also, I'll have the same problem on the next upgrade?

---

### Post by laeg_ on 2010-06-26
Shouldn't synaptic just work?

---

### Post by teejaybee on 2010-06-26
Yes, it should just work. It doesn't. Something's gone wrong. I had a closer look at the error messages and did a few google searches. It appears a symbolic link has been removed. Try reinstalling libswt-gtk-3.5-java.

Source: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568940](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568940)

If doing that fix enables you to run the program, you can manually add it into the menus. Maybe future versions will add a corresponding entry to the menu.

---

### Post by laeg_ on 2010-06-27
> **teejaybee said:**
> Yes, it should just work. It doesn't. Something's gone wrong. I had a closer look at the error messages and did a few google searches. It appears a symbolic link has been removed. Try reinstalling libswt-gtk-3.5-java.

Source: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568940](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568940)

If doing that fix enables you to run the program, you can manually add it into the menus. Maybe future versions will add a corresponding entry to the menu.

```
laeg@skyrocket:~$ sudo rm -r /opt/vuze
[sudo] password for laeg: 
laeg@skyrocket:~$ mv .azureus .azureus-old
laeg@skyrocket:~$ 
laeg@skyrocket:~$ sudo apt-get purge vuze
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vuze is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni liblog4j1.2-java libswt-mozilla-gtk-3.5-jni
  libcommons-cli-java libcommons-lang-java libswt-gnome-gtk-3.5-jni
  java-wrappers
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
laeg@skyrocket:~$ sudo apt-get purge azureus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package azureus is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni liblog4j1.2-java libswt-mozilla-gtk-3.5-jni
  libcommons-cli-java libcommons-lang-java libswt-gnome-gtk-3.5-jni
  java-wrappers
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
laeg@skyrocket:~$ sudo apt-get purge libswt-gtk-3.5-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni libswt-gtk-3.5-jni liblog4j1.2-java
  libswt-mozilla-gtk-3.5-jni libcommons-cli-java libcommons-lang-java
  libswt-gnome-gtk-3.5-jni java-wrappers
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libswt-gtk-3.5-java*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,651kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 187645 files and directories currently installed.)
Removing libswt-gtk-3.5-java ...
laeg@skyrocket:~$ sudo apt-get install libswt-gtk-3.5-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni liblog4j1.2-java libswt-mozilla-gtk-3.5-jni
  libcommons-cli-java libcommons-lang-java libswt-gnome-gtk-3.5-jni
  java-wrappers
Use 'apt-get autoremove' to remove them.
Suggested packages:
  libswt-gtk-3.5-java-gcj
The following NEW packages will be installed:
  libswt-gtk-3.5-java
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,467kB of archives.
After this operation, 1,651kB of additional disk space will be used.
Selecting previously deselected package libswt-gtk-3.5-java.
(Reading database ... 187636 files and directories currently installed.)
Unpacking libswt-gtk-3.5-java (from .../libswt-gtk-3.5-java_3.5.1+versionbump-2ubuntu2_i386.deb) ...
Setting up libswt-gtk-3.5-java (3.5.1+versionbump-2ubuntu2) ...
laeg@skyrocket:~$ sudo apt-get install vuze
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  azureus
The following NEW packages will be installed:
  azureus vuze
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.9MB of archives.
After this operation, 13.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package azureus.
(Reading database ... 187647 files and directories currently installed.)
Unpacking azureus (from .../azureus_4.3.0.6-1_all.deb) ...
Selecting previously deselected package vuze.
Unpacking vuze (from .../vuze_4.3.0.6-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IE.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up azureus (4.3.0.6-1) ...

Setting up vuze (4.3.0.6-1) ...
Processing triggers for menu ...
laeg@skyrocket:~$ sudo rm -r .azureus
laeg@skyrocket:~$ mv .azureus-old .azureus
```

Many thanks, synaptic packaged version works again :)

---

