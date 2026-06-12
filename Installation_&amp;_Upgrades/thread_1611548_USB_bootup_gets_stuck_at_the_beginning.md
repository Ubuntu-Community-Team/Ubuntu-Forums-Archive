---
title: "USB bootup gets stuck at the beginning"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by Eoghanalbar on 2010-11-02
It just displays the line "SYSLINUX 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 H. Peter Anvin et al" and a flashing underscore, and goes nowhere.

I made the boot usb from kubuntu-10.10-desktop-i386.iso on an acer aspire one netbook in windows 7 starter, and am trying to install to the same computer (which of course has no optical drive).

Any ideas?

Thanks!

~Owen

---

### Post by wilee-nilee on 2010-11-02
Make sure your using the latest version of the loader, sounds like unetbootin. Make sure the ISO is a good download.
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

Make sure if you get to installing that you use the W7 disk manager to resize the W7 C partition or any other windows partition. Resize and reboot W7 before installing Kubuntu to the free space. Also be aware of the maximum amount of primary partitions on a single HD.

---

### Post by oldfred on 2010-11-02
There seems to be a bug, yours may be the syslinux version issue:

[http://ubuntuforums.org/showthread.php?t=1589852](http://ubuntuforums.org/showthread.php?t=1589852)
[http://my.opera.com/toman/blog/setting-up-squeezebox-server-on-new-hardware](http://my.opera.com/toman/blog/setting-up-squeezebox-server-on-new-hardware)
After some fiddling around with the syslinux config files and still not getting it to boot properly, I found a deceptively simple workaround for this: Just type "help" on the BOOT prompt, and when you get the help menu, just hit enter. The system will now boot!

Maverick images burned to usb key on lucid fail to boot - different syslinux version 
ui in /isolinux/isolinux.cfg
[http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/](http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/)
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
[http://ubuntuforums.org/showthread.php?t=1582446](http://ubuntuforums.org/showthread.php?t=1582446)
[http://ubuntuforums.org/showthread.php?p=9948797](http://ubuntuforums.org/showthread.php?p=9948797)

---

