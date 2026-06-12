---
title: "Epic install woes"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by meloncreative on 2012-06-13
Hi everyone!

I'm trying to get Ubuntu 12.04 64bit installed on a Tranquil PC BBS2 Advanced.

I've got to install from USB stick as there is no optical drive installed and I don't have a USB optical drive.

I've tried way too many combinations to count but I'll try to list what I've done.

Check MD5 sum of .iso - all good.

[LIST]
[*]Create bootable USB with unetbootin try to boot - doesn't seem to try to load anything just says boot error.
[*]Create bootable USB with unetbootin try to boot - boots but won't load installer or live Ubuntu.
[*]Create bootable USB with USB creator try to boot - doesn't seem to try to load anything just says boot error.
[*]Create bootable USB with USB creator try to boot - boots but won't load installer or live Ubuntu.
[/LIST]

I've also tried to boot up ubuntu 11.10 64bit and 11.10 32bit usb sticks to no avail.

I've even had it start loading the installer - then give me a login screen as if I've tried to boot into live Ubuntu but I can't login with ubuntu and no password or Ubuntu and no password.

I've created 12.04 and 11.10 cds and tried to boot them on another pc (which we've been unable to boot ubuntu cds with in the past) with pretty much the same outcomes.

The only thing I seem to be able to get the Tranquil box to boot is if I create a YUMI bootable usb stick. The only thing I've managed to run from there is a W7 installer which isn't much use.

Any ideas at all? I've totally run out of things to try.

---

### Post by darkod on 2012-06-13
First of all, you have to split your problem.

If the stick doesn't even start booting, double check the usb boot process and how the stick was created.

If it starts booting (the stick), but ubuntu doesn't load live mode correctly, it might be an issue with your hardware. Most often a video driver issue, especially with nvidia.

If you think this is the case, the first thing to try is the nomodeset parameter, as explained here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

See if that helps.

---

