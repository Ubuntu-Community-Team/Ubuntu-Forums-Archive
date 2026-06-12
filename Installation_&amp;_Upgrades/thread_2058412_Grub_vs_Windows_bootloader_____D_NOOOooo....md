---
title: "Grub vs Windows bootloader     D: NOOOooo..."
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by *^kyfds( on 2012-09-15
I've got a windows 7 OEM installation on my Dell 1018 mini-netbook that i'm trying to install ubuntu 12.04 alongside.

Whenever i finish the installation, it'll use the grub bootloader for the first one or two boots, but for some reason it just reverts back to the windows boot loader after that.

I'm getting very frustrated with this as the only guides i've read to try to fix this issue involve reformatting my entire drive, which i can't do, because it has a recovery partition, which i can't move.

help?

---

### Post by darkod on 2012-09-15
Dell probably installed some sort of software that detects changes in the MBR and restores the previous one, thinking that maybe a virus was doing the changes. Or simply to help MS keep dominance. :)

You will need to investigate about your exact model, and whether any kind of software of this type is running.

---

### Post by *^kyfds( on 2012-09-15
the only software i can think of that's visibly running all of the time is the dell maintenance centre.

Is there any way to get ubuntu to work with the windows bootloader without using wubi?

---

### Post by darkod on 2012-09-15
For that you would need to force grub2 to install on the root partition, not the MBR.
Then use EasyBCD or similar to add it to windows bootloader.

In this kind of setup grub2 can break sometimes on updates because they can move the location of some grub2 files. That's why installing on partition is not recommended, but you can go for it if you want to.

I would rether sort out the MBR thing because you need to know what you have controlling your computer. Dell support can probably help you with that, after all you paid for their product.

---

### Post by oldfred on 2012-09-15
Places to start looking for issues.

In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)

I also prefer grub2.

---

### Post by *^kyfds( on 2012-09-16
if it's relevant, whenever i boot from windows after i install ubuntu, chkdsk always runs automatically.

---

### Post by cwsnyder on 2012-09-16
I don't know of a fix to the problem other than using the Windows bootloader, but I think I can identify the problem: Windows 7 security **always** checks the MBR and restores the Windows MBR from a copy kept in the C:\ folder if Windows 7 is installed as the first operating system on the drive.:confused:  This clobbers the GRUB boot loader if GRUB writes to the MBR.

This is part of the security system of Windows 7 to block some viruses.

---

### Post by *^kyfds( on 2012-09-16
[http://www.ubuntu.com/certification/hardware/201010-6646/](http://www.ubuntu.com/certification/hardware/201010-6646/)


"certified for ubuntu"

:(

---

### Post by *^kyfds( on 2012-09-16
> **cwsnyder said:**
> I don't know of a fix to the problem other than using the Windows bootloader, but I think I can identify the problem: Windows 7 security **always** checks the MBR and restores the Windows MBR from a copy kept in the C:\ folder if Windows 7 is installed as the first operating system on the drive.:confused:  This clobbers the GRUB boot loader if GRUB writes to the MBR.

This is part of the security system of Windows 7 to block some viruses.


i really don't want to use wubi again

-_-

---

### Post by darkod on 2012-09-16
> **cwsnyder said:**
> I don't know of a fix to the problem other than using the Windows bootloader, but I think I can identify the problem: Windows 7 security **always** checks the MBR and restores the Windows MBR from a copy kept in the C:\ folder if Windows 7 is installed as the first operating system on the drive.:confused:  This clobbers the GRUB boot loader if GRUB writes to the MBR.

This is part of the security system of Windows 7 to block some viruses.

This is not true, except if you are talking about some third party software or some win7 component that is not activated by default and you need to activate it yourself.

I have both my desktop and netbook installed with win7 first and ubuntu second, and they are happily running dual boot for years with different versions of ubuntu. Not once has win7 deleted grub2 from the MBR.

This is a software that Dell has installed. Few years back there was a period when both HP and Dell were doing this and I remember there were many threads from people complaining they are losing grub after they boot windows once. Since then, they seem to have stopped installing this rubbish, but maybe Dell has started again.

I say again, talk to their support. After all, you paid for their product and now it's yours. They are obligated to help you remove such rubbish from it. What's next, tomorrow they will enter your computer remotely to check if everything is running OK?

And for the future, you know to avoid their products, especially if they don't want to assist. I assume you were never told you can't use that machine in a dual boot so they don't have the right to do that.

PS. Did you read and checked the information oldfred posted? Usually there is a way to disable this software.

---

### Post by cwsnyder on 2012-09-16
It may be the Microsoft Security Essentials, but I have seen this problem before.

---

### Post by *^kyfds( on 2012-09-16
i'm going ahead with this from oldfred's post.

[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by *^kyfds( on 2012-09-18
i still can't boot from the grub bootloader.

would it be possible to completely get rid of the windows partition, but leave the recovery partition intact if i want to restore it?

---

### Post by oldfred on 2012-09-18
Often the system lets you write the recovery to a set of DVDs so you can recover to a new drive when the old drive fails. Then you do not have to save the recovery partition.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by *^kyfds( on 2012-10-16
Considering how slowly windows 7 was running of this netbook, i just decided to wipe out all of the partitions, apart from the recovery partition, and install ubuntu 12.04

marking as solved.

---

