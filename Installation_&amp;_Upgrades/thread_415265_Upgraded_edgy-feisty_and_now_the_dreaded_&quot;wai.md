---
title: "Upgraded edgy-feisty and now the dreaded &quot;waiting on root file system&quot; error"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by mlcampbe on 2007-04-20
Can someone help me out here??

I had a working edgy installation yesterday and did the online update overnight. I checked it before bed and it was installing packages and I thought excellent. I come in this morning and just have a black screen. I can do nothing so I try to reboot and it gets the splash screen and 1 bar of progress and hangs. Eventually I see the message about unable to load the root file system and then dropped to a shell.

I do the verbose boot and the last thing I see is "waiting for root file system"

I have booted qparted and verified that the root file system is still /dev/hda2 which is what grub says. I can mount /dev/hda2 from a resuce cd just fine. Seems that the problem is grub finding the disk. 

How do I get around this problem? Please help

---

### Post by mlcampbe on 2007-04-20
Following the instructions from another post I did the following:

modprobe ide-disk
modprobe ide-generic
mount -t ext3 /dev/hda1 /root
mkdir -p /dev/disk/by-uuid
ln -s /dev/hda1 /dev/disk/by-uuid/xxxxx-xxxxx-xxxx-xxxx (replace with your uuid in /root/etc/fstab)
Control-D

Now I can get to the login page and it takes my credentials. However at that point I just get the yellow/orange ubuntu background and nothing else. Any ideas from here?

---

### Post by revoltism on 2007-04-21
sounds like my problem. I changed the IDE-Configuration option in Bios from AHCI to Standard IDE and got it working.

---

