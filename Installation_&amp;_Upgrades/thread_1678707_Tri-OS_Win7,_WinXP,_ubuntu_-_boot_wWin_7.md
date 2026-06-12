---
title: "Tri-OS Win7, WinXP, ubuntu - boot w/Win 7"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by Mesmurized on 2011-01-30
After years of absence, I'm back ):P. Two questions:

Question 1. See attached image: ubuntu 10.10 installed on two small logical partitions (root@5GB + swap@1GB) however Win7 Disk management shows them as unnamed primary (not logical) partitions. Of course this is impossible because only 1 extended partition is allowed.  Is this a windows issue and should I be concerned?  I suspect it's because Win7 doesn't understand an ext4 file system, but I thought the partition layout was independent of the OS :confused:

[http://ubuntuforums.org/attachment.php?attachmentid=182365&stc=1&d=1296438245](http://ubuntuforums.org/attachment.php?attachmentid=182365&stc=1&d=1296438245)

Question 2:  Using the same disk layout, three OS's (Win7, WinXP and ubuntu 10.10) are installed. Everything is working, but since ubuntu was installed last, it took over the MBR. Makes it easy to get to ubuntu, but 2-steps to Win 7 or WinXP (my primary system). I swapped the grub boot order to make Win 7 first, but I still want to use Win7's boot BCD menu. Tried installing ubuntu's boot on the ubuntu partition (/dev/sda9) and using EasyBCD to add it to Win7 ... but ubuntu it won't boot (always menu.lst errors). Tried several EasyBCD options without success.

I'm fairly sure it will work, but I must have overlooked something, probably very simple.

Can someone simplify this boot stuff for me?  Thanks all. ;)

---

### Post by slooksterpsv on 2011-01-30
1 - It's Windows cause it doesn't know what Linux Partitions are - we see Ext4, it sees nothing. Windows needs 3rd party programs/drivers to even read Ext2/3 partitions, and I have yet to find a program that can read 4.

2 - I have a feeling this is related to #1, because BCD doesn't know how to read or start the boot process for an EXT<x> drive it won't boot. With Ubuntu and WUBI, WUBI installs Ubuntu to a file on a drive, (your choice of size up to 30GB) and uses the NTFS partition to find the files on it to load that file (which contains the Ubuntu OS). 

I'd stick with Grub, you can even make it look awesome with BURG (Grub spelled backwards =P) - here's a look at Burg boot up themes:

[http://code.google.com/p/burg/wiki/Screenshots](http://code.google.com/p/burg/wiki/Screenshots)

I'm going to put BURG back on my system now.

EDIT:
[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

Instructions on how to install it.

---

### Post by Mesmurized on 2011-01-31
Thanks for your quick reply. Maybe there is no solution to my preferred boot method :) Since this is a test environment, I will continue to experiment. Time to try Wubi ubuntu as a file on Win 7 too. Also thanks for the info on Burb, will give it a try ;)

---

