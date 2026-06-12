---
title: "Exception in thread &quot;main&quot; java.lang.NoClassDefFoundError: com/zerog/lax/LAX"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by saz on 2006-12-27
I'm trying to install the program that came with my UPS, but when i run the installer (./setup.bin) i get this error:

> sa@Sazito:~/Linux$ sudo ./setup.bin
Exception in thread "main" java.lang.NoClassDefFoundError: com/zerog/lax/LAX


and a file (setup.bin.lax), that is in the same folder as the installer, is changed.
here is the content of the original file:

> #THIS FILE IS MACHINE GENERATED; DO NOT MODIFY. (UNIX)  [http://www.ZeroG.com/](http://www.ZeroG.com/)

lax.stdout.redirect=

lax.user.dir=.

lax.application.name=setup

lax.command.line.args=$CMD_LINE_ARGUMENTS$

lax.nl.java.launcher.main.method=main

lax.main.class=com.zerog.ia.installer.Main

lax.nl.valid.vm.list=J2 J1 MSJ MRJ

lax.nl.java.option.verify.mode=none

lax.stderr.redirect=

lax.resource.dir=Linux

lax.stdin.redirect=

lax.nl.java.option.java.heap.size.initial=16777216

lax.nl.java.option.check.source=off

lax.main.method=main

lax.nl.java.launcher.main.class=com.zerog.lax.LAX

lax.version=5.0.6 Enterprise

lax.installer.unix.internal.property.0=bin/java

lax.installer.unix.ui.default=GUI

lax.nl.current.vm=resource/jre/bin/java

lax.nl.java.option.java.heap.size.max=50331648

lax.class.path=../InstallerData/IAClasses.zip:../InstallerData/Installer.zip:InstallerData/Installer.zip:../InstallerData:InstallerData


the changed file, has a different line 39.
**the original is:**
> lax.nl.current.vm=resource/jre/bin/java

**the new one is:**
> lax.nl.current.vm=/usr/lib/jvm/java-1.5.0-sun/jre/bin/java

can someone help me out? please let me know if i was unclear...

---

### Post by saz on 2006-12-29
anyone help?

---

