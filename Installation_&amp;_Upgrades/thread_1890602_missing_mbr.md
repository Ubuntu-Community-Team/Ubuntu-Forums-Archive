---
title: "missing mbr"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by mercenarygod on 2011-12-03
Well here's my problem. I've installed Ubuntu using wubi onto my second hard drive. My sata HDD is running W7 ultimate. The second HDD with Ubuntu is connected via IDE. When I try and boot into Ubuntu I get a software or hardware could be causing a problem error. Missing or corrupt ubuntu\winboot\wubildr.mbr and the error code below is 0xc000000e.

I have tried researching this problem and tried different things. Nothing seems to be working. So I come to you guys because I'm probably over looking something simple.:confused:

Edit:
More info so you guys can help me. I'm stumped.
wubildr and wubildr.mbr are on my C: drive
checked in advanced system settings>startup and recovery and ubuntu shows up in default operating system

---

### Post by bcbc on 2011-12-04
> **mercenarygod said:**
> Well here's my problem. I've installed Ubuntu using wubi onto my second hard drive. My sata HDD is running W7 ultimate. The second HDD with Ubuntu is connected via IDE. When I try and boot into Ubuntu I get a software or hardware could be causing a problem error. Missing or corrupt ubuntu\winboot\wubildr.mbr and the error code below is 0xc000000e.

I have tried researching this problem and tried different things. Nothing seems to be working. So I come to you guys because I'm probably over looking something simple.:confused:

Edit:
More info so you guys can help me. I'm stumped.
wubildr and wubildr.mbr are on my C: drive
checked in advanced system settings>startup and recovery and ubuntu shows up in default operating system
Wubildr.mbr may be on your C: drive, but the one that's being called from windows boot manager is "\ubuntu\winboot\wubildr.mbr" which is on that hard drive.

So I'd guess that the drive (possibly just the file) is not visible to BIOS. What could happen is that some older BIOSes can only address files within 137GB of the start of the drive and if Ubuntu is installed outside of that you'd see something similar. What the actual cause is - I can't say - but for some reason wubildr.mbr cannot be found.

---

### Post by mercenarygod on 2011-12-04
Well my mother board isn't old. What if I try this.
Uninstall wubi.
Unplug my sata.
Install ubuntu from cd.

Would there then be any way to edit something in ubuntu to make it work when I have my sata plugged back in?

---

### Post by darkod on 2011-12-04
Yes, when you plug the sata back in you will boot ubuntu and in terminal execute:
sudo update-grub

That will discover win7.
But you don't even need to disconnect. During the install you just make sure to tell it to install onto the disk you want and that's it. I always prefer installing a OS with all the hardware present.

And installing properly, fully, is always much better than wubi.

---

### Post by bcbc on 2011-12-04
Yes a full install is better. Wubi is good to try out Ubuntu in which case installing on the internal hard drive can rule out problems like the one you're having.

Since you have a separate hard drive, Wubi is not a good idea. Also you'll find out pretty quickly if there is a problem booting from the drive. Just make sure you put the grub bootloader on the separate drive (if you put it on your internal drive and it cannot locate the grub.cfg and additional modules on the separate drive - you'll end up with a grub rescue prompt).

Best idea is to create a Windows repair CD before installing Ubuntu (of course you should back everything up etc.) - the repair CD will let you reinstall a windows bootloader if you run into problems.

Here's a good guide: [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html) (written for release 10.10 but most still applies).

---

### Post by mercenarygod on 2011-12-04
Thank, I think I got it working. I just use tab to switch to post then f11 and boot into ubuntu. The three times I tried installing it with the CD I got the same errors. I'll look over the tutorial and see if I did anything wrong. Cheers.:)

---

