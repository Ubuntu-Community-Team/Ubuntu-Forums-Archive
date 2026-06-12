---
title: "Can't access all partitions of usb stick under windows"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by dylanv on 2007-08-18
Hi all,

This is my first Ubuntu Forums post, so I'm curious to see if Ubuntu's touted 'community support' can help me with my problem. The wiki has already proved to be a great source of information. Hopefully I can explain my problem clearly.

Today I made a Feisty live boot USB stick using (modified) instructions from [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"). I am able to boot a live Feisty environment from the flash drive (yay!), but as the wiki warned, I am not able to use the persistence feature. I don't need this feature, so I used the GParted LiveCD to delete the persistence partition on the flash drive. Then, I created a FAT32 partition to fill up the rest of the flash drive. I did this because the Ubuntu files are only taking up about 700MB on the drive, and I would like to be able to use the rest to store files on. I can access the new partition for my files under my Ubuntu installation (on my hard drive) but only the first partition (the one with the Ubuntu live files) is visible under Windows. In Windows Disk Management (in Administrative Tools), when I try to assign a drive letter to the second partition on the drive, it says, "The operation cannot be completed because the partition is not enabled. To enable the volume, restart the computer." When I restart, I get the same error.

Any thoughts? Thanks in advance for your help.

Dylan

---

### Post by kidders on 2007-08-19
Hi there,

I'm not much of a Windows user, but from my limited use of USB storage devices on the platform, Bill Gates seems to have decreed that there shall be no valid reason to store more than one filesystem on certain USB devices ... seemingly (and again, I may well be wrong about this) including things that don't have moving parts in them. Basically, my limited use of Windows has sort of taught me to instinctively expect attempts to mount second and subsequent filesystems on USB flash drives to fail ... even though "proper" hard disks seem to work as one would normally expect, for some reason.

I'm not sure if there's a clever way around this limitation, or why it's there. My approach has always been to put a filesystem that Windows needs access to first (in terms of the partition table). Filesystems for use by other OSs, such as MacOS or Linux can occupy the second & subsequent slots.

I hope that helps ... at least a little.

---

### Post by Chaotic Thought on 2007-08-19
I have several USB devices with several partitions and have not had a problem under Windows or Linux. However, I did a check for the problem the OP and it is not specific to Linux-partitioned drives. Several Windows users report similar problems:

[http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=ajw&q=%22partition+not+enabled%22+disk+management&btnG=Search](http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=ajw&q=%22partition+not+enabled%22+disk+management&btnG=Search)

I suggest reading through there and see if any of the proposed solutions help you out.

---

