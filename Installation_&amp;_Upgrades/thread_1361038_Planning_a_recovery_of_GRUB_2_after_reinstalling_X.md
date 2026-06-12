---
title: "Planning a recovery of GRUB 2 after reinstalling XP"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by pikmen on 2009-12-21
Hi guys!

After installing Ubuntu 9.10, and following several newbie mistakes, I ended up killing my Windows XP boot record - all I get now is a "NTLDR is missing" error, and it won't boot. This isn't really dramatic, all the files were still intact and I've already backed them up. Anyway, I'm planning on formating the partition XP was in, and reinstalling it.

From what I read, I can expect the default XP loader to override GRUB 2, and in anticipation I've been reading some guides in the forums. This one ([http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)) seems simple enough to understand, but I'm a little unsure about using terminal codes I know nothing about, and I was hopping you guys could explain some things to me.

Currently, using:

**sudo fdisk -l**

I get:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x173533d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           9       71268+   7  HPFS/NTFS
/dev/sda2           11151       19457    66725977+   7  HPFS/NTFS
/dev/sda3              10       11150    89490082+   5  Extended
/dev/sda5              10       10787    86574253+  83  Linux
/dev/sda6           10788       11150     2915766   82  Linux swap / Solaris

Partition table entries are not in disk order


So, after I've properly installed XP, and rebooted starting Ubuntu from it's installation CD, the terminal commands I should use for my specific disposition of partitions are:

[B]sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
[/B] 
followed by:

** sudo grub-install --root-directory=/media/sda5 /dev/sda**

When I next reboot I should find GRUB 2 and Ubuntu working as usual, also allowing me to run XP when I need it, is this correct?

Sorry for asking such a common question, but I really don't want to make more mistakes.

---

### Post by darkod on 2009-12-21
Yes. There is slight modification to those commands you can make which is even easier:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Instead of creating a folder sda5 in /media, you can use /mnt directly.

---

### Post by presence1960 on 2009-12-21
> **darkod said:**
> Yes. There is slight modification to those commands you can make which is even easier:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Instead of creating a folder sda5 in /media, you can use /mnt directly.

+1

[Here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") is a link for reference to what Darko told you. I would do it that way.

---

### Post by pikmen on 2009-12-22
The commands you guys gave me worked perfectly, and everything is working fine.

Thanks for the help :)

---

### Post by presence1960 on 2009-12-22
Glad you got it working. Enjoy Ubuntu.

---

