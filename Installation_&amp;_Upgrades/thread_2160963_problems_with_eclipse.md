---
title: "problems with eclipse"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by nngrey on 2013-07-08
[SIZE=3][SIZE=2]I have installed eclipse kepler from the software center. I am now trying to open and run source files from dropbox. These are simple programs (homework for an intro java class) which I created using eclipse in windows or mac os. When I try to open and run the files I get errors like "The import java.util cannot be resolved." Usually the files will not compile or run and I get output like...
[/SIZE]
[/SIZE][SIZE=2][FONT=arial]Exception in thread "main" java.lang.[/FONT][FONT=arial]UnsupportedClassVersionError: FractionScale : Unsupported major.minor version 51.0[/FONT]
[FONT=arial]    at java.lang.ClassLoader.[/FONT][FONT=arial]defineClass1(Native Method)[/FONT]
[FONT=arial]    at java.lang.ClassLoader.[/FONT][FONT=arial]defineClass(ClassLoader.java:[/FONT][FONT=arial]634)[/FONT]
[FONT=arial]    at java.security.[/FONT][FONT=arial]SecureClassLoader.defineClass([/FONT][FONT=arial]SecureClassLoader.java:142)[/FONT]
[FONT=arial]    at java.net.URLClassLoader.[/FONT][FONT=arial]defineClass(URLClassLoader.[/FONT][FONT=arial]java:277)[/FONT]
[FONT=arial]    at java.net.URLClassLoader.[/FONT][FONT=arial]access$000(URLClassLoader.[/FONT][FONT=arial]java:73)[/FONT]
[FONT=arial]    at java.net.URLClassLoader$1.run([/FONT][FONT=arial]URLClassLoader.java:212)[/FONT]
[FONT=arial]    at java.security.[/FONT][FONT=arial]AccessController.doPrivileged([/FONT][FONT=arial]Native Method)[/FONT]
[FONT=arial]    at java.net.URLClassLoader.[/FONT][FONT=arial]findClass(URLClassLoader.java:[/FONT][FONT=arial]205)[/FONT]
[FONT=arial]    at java.lang.ClassLoader.[/FONT][FONT=arial]loadClass(ClassLoader.java:[/FONT][FONT=arial]321)[/FONT]
[FONT=arial]    at sun.misc.Launcher$[/FONT][FONT=arial]AppClassLoader.loadClass([/FONT][FONT=arial]Launcher.java:294)[/FONT]
[FONT=arial]    at java.lang.ClassLoader.[/FONT][FONT=arial]loadClass(ClassLoader.java:[/FONT][FONT=arial]266)[/FONT]
[FONT=arial]Could not find the main class: FractionScale. Program will exit.

These are all files that I can run from eclipse on my mac. I just can't run them from eclipse on ubuntu. I am wondering if there is a path issue but can't seem to determine if it is an how to fix it. Any suggestions would be appreciated. [/FONT][/SIZE][SIZE=3][/SIZE]

---

### Post by DJRoTec on 2013-07-09
you're probably using two different versions of java jdk. try using the same one on both machines. that should solve the problem

---

