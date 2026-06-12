---
title: "Installing Lubuntu 11.04 on a Dell Mini 9 netbook"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by jarofgreen on 2011-09-15
Has anyone managed this?
I tried this afternoon and had all kinds of fatal errors.
I will try again soon and file bug reports but some of the errors were so vague as to be worthless.
But here's one I confirmed: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/630990](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/630990)

---

### Post by jarofgreen on 2011-09-15
Running graphical installer from live-USB, crashes:
ubi-partman failed with exit code 10.

The only things that look like errors in the syslog are
ubiquity: sh: getcwd() failed:No such file or directory
ubiquity: shell-init: error retrieving current directory: getcwd: cannot access parent 
directories: No such file or directory.
These are repeated several times.
Also 
kernel : lxinput[5293]: segfaultat 21 ip ... error in libX11.so.6.3.0
ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat

My HD had a just-formatted ext4 partition on it at the time. Any ideas?

---

### Post by kerry_s on 2011-09-15
Bad installer? Try making it again.

---

### Post by jarofgreen on 2011-09-15
Fixed it by installing Ubuntu 10.04LTS :-(

But not after one final quirk: creating a boot USB in a later Ubuntu makes a broken boot disk, but I found the answer here [http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/) - you have to type help then press enter at the boot prompt. Sigh.

Will try again in several months time ... in the mean time, any advice welcome.

---

### Post by jarofgreen on 2011-09-15
> **kerry_s said:**
> Bad installer? Try making it again.

This was one of the really odd errors I ran into this afternoon
* boot from USB, start install process or live disk works once.
* boot from same USB, you get a blank screen and a freeze.
* reimage USB from same ISO.
* boot from USB, start install process or live disk will now work.
WTF? It was almost like the mere act of starting the installer or live session corrupted the USB.

I did find this page [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall) which has a separate installer for Lubuntu but after downloading mini.iso I couldn't write it it the USB.

That page says "The team are working on a minimal installation cd." so hopefully in 3 months time the 11.10 set of installs will work for me.

Agh. One of the reasons I wanted to move to Lubuntu was all the Ubuntu bloat, and the damn Ubiquity installer stopped me. Ironic. I note that page says "The graphical installation system ([Ubiquity]("https://wiki.ubuntu.com/Ubiquity")) requires more RAM than lubuntu needs to run." :-)

---

