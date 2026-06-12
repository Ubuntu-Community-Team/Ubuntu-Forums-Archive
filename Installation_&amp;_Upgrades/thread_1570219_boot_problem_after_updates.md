---
title: "boot problem after updates"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by bayouoldguy on 2010-09-07
Time for some ubuntu help.
 I just performed an update thru the Update Manager, & on re-boot got this message:    ( Ubuntu 10.04.1 LTS, kernel 2.6.32-24-386 )

[B][B]udevadm trigger is not permitted while udev is unconfigured.

Gave up waiting for root device.  Common problems :

- Boot args ( cat /proc/cmdline )
 - Check root delay= ( did the system wait long enough? )
 - Check root= ( did the system wait for the right device? )
- missing modules ( cat /proc/modules; ls /dev )

ALERT! /dev/disk/by-uuid/df0200e3-e6e9-439a-922f-100d92af0c58 does not exist. Dropping to a shell!.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built in shell (ash)
[/B]
(initramfs)_[/B]

Info: I can boot into older version: Ubuntu 10.04.1 LTS, kernel 2.6.32-23-386. The Update Manager does not seem to want to show any updates that are available.
Anyone have any ideas ?...................."G"

---

### Post by ronparent on 2010-09-07
Try booting into recovery mode and running dpkg off the recovery menu?

---

### Post by Francis 24/24 on 2010-09-08
There are several other posts in forums refering to this error message following this last upgrade. The following ones for instance and likely some
more :
[http://ubuntuforums.org/showthread.php?t=1568108](http://ubuntuforums.org/showthread.php?t=1568108)
[http://ubuntuforums.org/showthread.php?t=1567060](http://ubuntuforums.org/showthread.php?t=1567060)
[http://ubuntuforums.org/showthread.php?t=1567147&page=2](http://ubuntuforums.org/showthread.php?t=1567147&page=2)

I would say there is a bug within this last - september 2 ? - batch of
updated packages. And if it's not fixed quickly many people will run into it.

---

### Post by bayouoldguy on 2010-09-08
> **Francis 24/24 said:**
> There are several other posts in forums refering to this error message following this last upgrade. The following ones for instance and likely some
more :
[http://ubuntuforums.org/showthread.php?t=1568108](http://ubuntuforums.org/showthread.php?t=1568108)
[http://ubuntuforums.org/showthread.php?t=1567060](http://ubuntuforums.org/showthread.php?t=1567060)
[http://ubuntuforums.org/showthread.php?t=1567147&page=2](http://ubuntuforums.org/showthread.php?t=1567147&page=2)

I would say there is a bug within this last - september 2 ? - batch of
updated packages. And if it's not fixed quickly many people will run into it.

It Works !, thanks Francis.
 ran in terminal :
  sudo update-initramfs -u -k2.6.32-24-386
I guess I need to run for the "generic" version too, just to keep things smooth
Always can count on Ubuntu Help !......."G"):P

---

