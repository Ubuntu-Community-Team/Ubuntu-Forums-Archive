---
title: "Installed XP, now Ubuntu won't boot...HELP!"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by tekpunk on 2007-10-26
Hey guys, I was running Ubuntu feisty and I decided to reinstall xp on a separate partition for my games (wine isn't cutting it).  Now XP is running fine, but I can't boot into Ubuntu.  I think the xp installation disabled the partition because I've already messed around with boot.ini by adding this line :multi(0)disk(0)rdisk(0)partition(1)\LINUX="UBUNTU" 
But it won't boot.  Any suggestions???

---

### Post by thelocust on 2007-10-26
Your budy and mine the Super GRUB Disk download yourself one. Stick it in your cd-rom reboot and then resote GRUB to your MBR and you'll be good. (P.S. all your info is good nothing got deleted just that windows thinks it's the only OS in the world so it overwrites your MBR just for it's self. easy fix)

---

### Post by tekpunk on 2007-10-26
Thanks, I hope this works!

---

### Post by Doomguy0505 on 2007-10-26
If that doesn't work, the alternate cd can do a rescue, such as restoring GRUB

---

### Post by thelocust on 2007-10-26
> **Doomguy0505 said:**
> If that doesn't work, the alternate cd can do a rescue, such as restoring GRUB
[COLOR=#666666]That’s usually my suggestion but gusty’s grub installer seems too jacked up.[/COLOR]

---

### Post by peetbull on 2007-10-26
Hi all,

I would like to add a relevant note for the future readers that may come across this topic, searching about their first dual-boot system.

If you would like to have Windows and Linux (any distro or flavour) on your system, prefer to install Windows first and then Linux.

Specifically, it's more secure to allocate the first partition for Windows, because initiates its setup at the very first cylinder of the hard disk, on the Master Boot Record (simplified, this is the primary record on the hard disk where data about partitions and booting is written); that's why it messed Tekpunk's installation (see the 1st post).

So the idea is to create your partitions, in my opinion using a Linux OS partitioner or any other you may like better.  (Linux-setup partitioners are very effective and quick, even for many different partitions at the same install process, without the geeky console and parameters!)

The partitions that you need at least are:
 
1 partition for windows (NTFS, FAT32)
1 partition for linux root (JournalisedFS, ReiserFS, or any other suggestion)
1 partition for linux swap (swap fs)

(I, sometimes, add one more partition FAT32 as a common storage for Linux and Windows - that's only to have a common place for storing files, independently on the OS I work on)

Then you can install Windows. The windows will be install on the first partition (give it > 5 GB, you never know!).

After Windows setup, you can initiate the Linux setup. Almost all of the famous distributions (Ubuntu, thumbs up!) will know where to be installed given the fact that you have partitioned your disk properly. Linux will also recognize Windows partition and it will probably be mounted on your current Linux logical file system. 

So everything's cool, and you probably have just followed yet another next-next-finish process! :)

Enjoy!

(Btw, enjoy your games Tekpunk!)


:guitar:

---

### Post by thelocust on 2007-10-26
good call peetbull I missed that. tekpunk, you can download the gparted live cd this can shrink expand and move around partions with out loosing any data

---

