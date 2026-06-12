---
title: "Problems with Grub menu after installing Karmic from Karmic with debootstrap/chroot"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by GeoMX on 2010-03-31
I'm currently running Ubuntu Karmic in a dual boot environment (Windows 7) and I'm trying to make a clean Ubuntu installation to a new hard drive to be used with another system.

I've followed the Ubuntu documentation guide at: [https://help.ubuntu.com/9.10/installation-guide/i386/linux-upgrade.html#id2628424](https://help.ubuntu.com/9.10/installation-guide/i386/linux-upgrade.html#id2628424)

and was able to follow all steps without problems. However, I have one problem with GRUB:

The new disk will hold only one OS (Ubuntu), so I'd like the GRUB menu not to appear, this is the case when booting from the new installation for the first time, but for the next one, GRUB menu appears and stays there no mater what I try. I've tried editing /etc/default/grub but when running update-grub I get this erros message:

grub-probe error cannot find a device for /

I think I got confused with the partition configuration, so could someone please give me some advice for configuring the new system correctly to work with GRUB?

Woudl it be possible to use a Live CD to reinstall and configure grub?

I've just switched to Karmic a week ago (I've been working with Hardy) and I'm a bit confused with the new version of grub, I find it a bit hard not to be able to edit the files but run update-grub instead.

---

### Post by oldfred on 2010-04-01
Is the drive still on your system or have you moved it to the new system? Drive numbers probably changed.

Yes you can reinstall grub2
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you want to see where everything is installed:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

More info on grub2
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

---

### Post by GeoMX on 2010-04-07
Thanks a lot for all your help, those links provided me with enough information for understanding the new GRUB :).

However, I now have a more specific problem, we are trying to run a read only linux system, but don't know how should I proceed in order to edit GRUB since it relies on "normal" partitions (correct partitions declared in /etc/fstab and device.map), but when I try to configure GRUB inside the read only system, I get this GRUB error message: "can not find a device for /".

I'm basically following these instructions:
[http://www.logicsupply.com/blog/2009/01/27/how-to-build-a-read-only-linux-system/](http://www.logicsupply.com/blog/2009/01/27/how-to-build-a-read-only-linux-system/)

for setting our read-only system, do you have any advice on how to proceed in order to be able to configure GRUB in such a setup?

---

### Post by oldfred on 2010-04-07
Not quite sure if it is the same thing or not. But I used this to directly boot ISO which are read only.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the ccaveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you boot from a CD with no hard drive that is a read only system. I saw several years ago a minimal floppy only system where the floppy was set to read only - I think it may have been to convert an old computer to a router.

You may do better with a new thread with your new subject in the title as those with more interest in special configurations will read the thread as opposed to boot issues.

---

### Post by GeoMX on 2010-04-07
Thanks again for your help, I'll make a new post and mark this one as solved since now I'm able to configure the GRUB menu for a "standard" installation.

---

