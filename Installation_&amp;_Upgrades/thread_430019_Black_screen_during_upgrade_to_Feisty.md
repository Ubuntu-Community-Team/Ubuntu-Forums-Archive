---
title: "Black screen during upgrade to Feisty"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by DarkDead on 2007-05-01
Hi.
I have a dual boot system with the following disk partitions:
/dev/hda1 - ntfs (Windows XP)
/dev/hda2 - ext3 (Ubuntu 6.10)
/dev/hda3 - swap

I was upgrading for 45 minutes to Feisty using the Update Manager when the screen went black. I checked and the monitor was working (I could enter it's configuration menu). I let the computer turned on during the night and in the morning it continued equal. I did a reset and now I can't enter in Ubuntu. Grub shows Windows and kernel 2.6.17-10-generic Ubuntu. On the recovery mode I get > Begin: Waiting for root file system for some minutes and then:
> ALERT! /dev/hda2 does not exist. Dropping to a shell.
Busy Box v1.1.3 [...]
/bin/sh: can't access tty; jog control turned off (initramfs)
Using the Live CD of Feisty I can access /dev/hda2 and it still got all files there. But the Install application doesn't detect previous installed versions.
I had many programs and configurations that cost me a lot of time to apply on Edgy and I didn't want to loose them. So I was wondering if anyone can find a away to get Feisty working without having to loose all my data.
Thanks in advance.

---

### Post by unlimitedorb on 2007-05-03
I'm having the exact same problem with the exact same setup, is anyone willing to take up this topic? In the meantime, I'll be searching for fixes. With the Feisty live cd, all my files are there upon examination, so I'm not exactly panicking just yet. But I really need to hit the ground running pretty soon.

---

### Post by mjgumbley on 2007-05-06
After leaving the system for a while at the "Waiting for root file system" message, it complained that it couldn't find the UUID=xxxx-xxxx filesystem. I note (from booting from a Damn Small Linux CD) that my /etc/fstab has been modified to declare the filesystems using some awful UUID-naming scheme. (With helpful comments suggesting that this was done during the upgrade to edgy...) There's nothing wrong with /dev/hda7 -- IT'S UNDERSTANDABLE BY HUMANS, YOU MORONS --  so I'm currently trying to edit /etc/fstab, and see if it'll boot again.

I'm able to "boot" into Ubuntu by choosing a previous kernel in the GRUB menu, pressing 'e' to edit its options, and appending 'init=/bin/sh' - and changing the root=UUID=xxxx-xxxx to root=/dev/hda7 then press 'b' to boot this, then you get a shell.

You may have to remount the root FS with mount -o remount /dev/hda7 / 
(Replace this with your actual filesystem - fdisk -l /dev/hda will report the filesystems.)

All the above is, however, futile. The mdadm timeout now says /dev/hda7 does not exist! Like hell it does!

I think I'll have to get it into a state where I can remove/reconfigure the mdadm package - I answered 'all' - the default - to the mindnumbingly stupid long question I couldn't understand during upgrade. Other posts here suggests that I should have answered 'none' to this - I don't know how to change this configuration item yet though...

My overall conclusion of upgrades from Dapper to Edgy to Feisty is that there needs to be a damn sight more testing going on - if Dell are going to install this on systems, then upgrades have got to be DAMN TIGHT - the pain I've had during these upgrades has been unacceptable. Come on Ubuntu, you're probably the best distro out there - let's make upgrades JUST WORK, please...

---

### Post by mjgumbley on 2007-05-07
This thread
[http://ubuntuforums.org/showthread.php?t=429609](http://ubuntuforums.org/showthread.php?t=429609)
may be of some use - or at least, offers some hope...

---

