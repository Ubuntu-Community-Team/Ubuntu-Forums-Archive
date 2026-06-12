---
title: "Bruker Topspin installation problems"
date: 2016-12-18
forum: Installation &amp; Upgrades
---

### Post by druillich on 2016-12-18
Hi

I am trying to install Bruker Topspin 3.5 to my laptop with Lubuntu DE. I've been able to solve few issues but this error message pops up when I try to run the program. The lisence error isn't a problem, it ships with lisence till 2017. When I check /opt/topspin3.5pl6/jre/lib/i386/ liba_xwat.so file is there but libxrender.so.1 isn't. I have the newest version of libxrender installed (Ran sudo apt-get install libxrender1), but I cannot find the libxrender.so.1 file anywhere on the computer. I have tried reinstalling the library and that didn't work. Does anyone have any idea how to fix this?

Cannot checkout TopSpin FLEXlm license
Invalid license file syntax
Feature:       TOPSPIN3
License path:  /usr/local/flexlm/Bruker/licenses/license.dat
FLEXlm error:  -2,413
For further information, refer to the FLEXlm End User Manual,
available at "www.macrovision.com".

The FLEXlm host ID of this machine is unascertainable, eth0 is not available

license for noncommercial use, valid until 2017-07-31
error message cprserver: GetSystemPrinterList: dlopen(libcups.so) failed
Exception in thread "main" java.lang.UnsatisfiedLinkError: /opt/topspin3.5pl6/jre/lib/i386/libawt_xawt.so: libXrender.so.1: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1941)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1824)
    at java.lang.Runtime.load0(Runtime.java:809)
    at java.lang.System.load(System.java:1086)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1941)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1845)
    at java.lang.Runtime.loadLibrary0(Runtime.java:870)
    at java.lang.System.loadLibrary(System.java:1122)
    at java.awt.Toolkit$3.run(Toolkit.java:1636)
    at java.awt.Toolkit$3.run(Toolkit.java:1634)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1633)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1668)
    at java.awt.Color.<clinit>(Color.java:275)
    at de.bruker.nmr.mfw.base.BSplashScreen.<clinit>(BSplashScreen.java:44)
    at de.bruker.nmr.mfw.base.MfwBuilder.programMain(MfwBuilder.java:420)
    at bruker.bio.start.topspin.Start.main(Start.java:47)

premature Java Virtual Machine termination
Program is exiting ...

---

### Post by kongooi on 2017-07-22
> **druillich said:**
> Hi

I am trying to install Bruker Topspin 3.5 to my laptop with Lubuntu DE. I've been able to solve few issues but this error message pops up when I try to run the program. The lisence error isn't a problem, it ships with lisence till 2017. When I check /opt/topspin3.5pl6/jre/lib/i386/ liba_xwat.so file is there but libxrender.so.1 isn't. I have the newest version of libxrender installed (Ran sudo apt-get install libxrender1), but I cannot find the libxrender.so.1 file anywhere on the computer. I have tried reinstalling the library and that didn't work. Does anyone have any idea how to fix this?

Cannot checkout TopSpin FLEXlm license
Invalid license file syntax
Feature:       TOPSPIN3
License path:  /usr/local/flexlm/Bruker/licenses/license.dat
FLEXlm error:  -2,413
For further information, refer to the FLEXlm End User Manual,
available at "www.macrovision.com".

The FLEXlm host ID of this machine is unascertainable, eth0 is not available

license for noncommercial use, valid until 2017-07-31
error message cprserver: GetSystemPrinterList: dlopen(libcups.so) failed
Exception in thread "main" java.lang.UnsatisfiedLinkError: /opt/topspin3.5pl6/jre/lib/i386/libawt_xawt.so: libXrender.so.1: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1941)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1824)
    at java.lang.Runtime.load0(Runtime.java:809)
    at java.lang.System.load(System.java:1086)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1941)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1845)
    at java.lang.Runtime.loadLibrary0(Runtime.java:870)
    at java.lang.System.loadLibrary(System.java:1122)
    at java.awt.Toolkit$3.run(Toolkit.java:1636)
    at java.awt.Toolkit$3.run(Toolkit.java:1634)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1633)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1668)
    at java.awt.Color.<clinit>(Color.java:275)
    at de.bruker.nmr.mfw.base.BSplashScreen.<clinit>(BSplashScreen.java:44)
    at de.bruker.nmr.mfw.base.MfwBuilder.programMain(MfwBuilder.java:420)
    at bruker.bio.start.topspin.Start.main(Start.java:47)

premature Java Virtual Machine termination
Program is exiting ...

if you are using ubuntu, log in as root and do this, it shall work

[COLOR=#303336][FONT=inherit]apt[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]get install libxrender1[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit]i386 libxtst6[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit]i386 libxi6[/FONT][/COLOR][COLOR=#303336][FONT=inherit]:[/FONT][/COLOR][COLOR=#303336][FONT=inherit]i386[/FONT][/COLOR]

---

### Post by oldos2er on 2017-07-22
There is no root login by default on Ubuntu, we recommend using [sudo]("https://help.ubuntu.com/community/RootSudo") instead. But since druillich hasn't been back on the forums since they last posted this, I don't think s/he's likely to return now.

Please don't bump old threads; thanks.

Closed.

---

### Post by sofia.mariasina on 2018-01-04
I had the same problem when installing TopSpin on Ubuntu 16.04.1 64 bit.
In my case the solution was: 

1) install packages libxft2, libxft2:i386, lib32ncurses5, libxrender1:i386, libxtst6:i386, libxi6:i386

sudo apt-get install libxft2 libxft2:i386 lib32ncurses5 libxrender1:i386 libxtst6:i386 libxi6:i386
(after that I had exactly the same message from TopSpin, as you)

2) add line 'xxx.xxx.xxx.xx my_host' to the file /etc/hosts
In  my case it was '192.168.100.96 nmr-OptiPlex-7050' where '192.168.100.96'  is IP address of my computer, and 'nmr-OptiPlex-7050' is the name of my  computer.

---

