---
title: "First boot after upgrade to dapper fails"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by twowheeler on 2006-06-02
I used update-manager -d to move from breezy to dapper.  The process hung up at the point of configuring one of the packages (console-data) and I had to use the reset button.  When it came back up, I used dpkg --configure -a to restart the configuration.  It eventually finished correctly so I did a apt-get update and apt-get upgrade to make sure I had everything.  It fixed several broken packages and then reported everything was fixed and up to date.  So I booted again.

It got as far as the usplash screen and reported that it was mounting the root file system, and sat there a long time.  Eventually it dropped out to a console and I have this on the screen (retyped, so it is not exact) --

> Uncompressing Linux... Ok, booting the kernel.
/sbin/udevd: error while loading shared libraries: libsepol.so.1: cannot open shared object file: No such file or directory.
/scripts/local-top/udev: 30: /sbin/udevplug: not found

ALERT! /dev/hda1 does not exist.  Dropping to a shell!


BusyBox v1.01 Built-in shell (ash)

/bin/sh: Can't access tty; job control turned off.
#


So my *&^%$# udev is gone???  No disk drives, no network ... now what?  Do I have to start over?

---

### Post by ubuntu_demon on 2006-06-02
try this :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

