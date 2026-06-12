---
title: "How to partition for dual boot"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by king0 on 2010-01-21
I'm trying to understand how I can partition my hard disk to allow for a dual boot (Windows & Ubuntu) as well as allow access to a certain set of files from both Windows & Ubuntu. So far I understand that I'll need:


[LIST]
[*]1 Windows boot partition ~2-4GB
[*]1 Linux boot partition ~2-4GB
[*]1 Linux swap partition ~1-2 GB
[/LIST]
But I don't know:


[LIST]
[*]How can I keep my non-boot linux files & folders -- /home, /usr, etc. -- separate from the boot files? Do I need another partition? If yes, what _size & format_ -- FAT32, ext3, etc. -- should it be?
[*]If I separate, for instance, the "/home" folder only where do the remaining folders and files reside?
[*]How can I access certain files with both Windows & Ubuntu? Do I need yet another partition, formatted in FAT32?
[/LIST]
Thanks.

---

### Post by Yogotiss on 2010-01-21
If Windows is install first just do this for starters. Boot the live Linux disk and choose install side-by-side. There should be a diagram bar of some sort the shows your hard drive space. On that bar should be a grey knob you can move to determine how much space you want Linux to use. Then just continue on with the installation. Don't worry about boot partitions from Windows nor Linux, the Live disk will handle it accordingly. As far as you sharing files from boot operating system it is possible. Linux will naturally see the Wwindows as a separate partition but within Windows you may need some type of third party software to see the Linux partition.

---

### Post by raymondh on 2010-01-21
Dated but still very relevant.

[http://ubuntuforums.org/showpost.php?p=1646977&postcount=1](http://ubuntuforums.org/showpost.php?p=1646977&postcount=1)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Some reference read on gparted (if you decide to use that)

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

This is about dual-boot installations (but using GRUB-legacy) so reference this for 'ideas'.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Recovering/re-installing GRUB2 (if needed)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

My thoughts:

1.  You don't need a separate /boot partition unless you are trying to avoid an error 18 (where your BIOS is limited in how much HD it can access).  Nevertheless, workarounds for the error 18 is to ensure that the kernel is within the limit (for vintage 2000 around 137gb).

2.  Grub (or GRUB2) can be installed in the MBR of the HD that is set to boot first in BIOS.

3.  For sizing (and noting that this is minimal ... which you should remember when adding media files to ubuntu), I'd reco about 15gb for Ubuntu.

4.  Ext3 or Ext4 is OK.  I use ext3 because it has been proven/tested.  Ext4 has advantages which I do not discount but, I don't need them.  Your call ;)

5.  Some folks (like me) advocate having a DATA partition.  I put mine in NTFS format which can be accessed by both windows and Ubuntu.  Though I also use a separate /home, I do it because I have the space and I seem to 'tinker' a lot with my root (/) partitions.  See Bodhi-Zazens link (above) about /data and /home.

6.  For SWAP, I use 1x maximum installable RAM.  So if my system is capable of having a total of 32gb RAM, I will put my swap at 32GB.  Just in case I do put 32gb RAM in the future :)

Post back if you need clarifications or assistance.  

happy ubuntu-ing.

Raymond

---

