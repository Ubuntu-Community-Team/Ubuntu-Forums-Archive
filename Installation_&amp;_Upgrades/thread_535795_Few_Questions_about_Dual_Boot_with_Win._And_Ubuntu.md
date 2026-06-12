---
title: "Few Questions about Dual Boot with Win. And Ubuntu 7.04"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by Destroyer14094 on 2007-08-26
1. I have yet to get a dual boot working between windows(ME) and ubuntu without windows simply not operating(ubuntu will work perfectly though)... I did some research, but I want to make sure I know what I am doing before I try this since I don't feel like reloading everything again, even though I have everything backed up so it won't be a problem(just a pain).

2> .If you want a partition which can be readable by both Windows and Ubuntu without installing anything extra you will need to use Fat32.
What does this mean? Does it mean that I can make the bare minumum of a partition of what ubuntu needs to operate, then save data(and install programs) on the remaining 70gb-ish of HHD space with ubuntu(remaining space is FAT32 Windows ME), or can ubuntu only install it's own programs on it's own partition?

---

### Post by Pumalite on 2007-08-26
.If you want a partition which can be readable by both Windows and Ubuntu without installing anything extra you will need to use Fat32.
 This refers to a partition to store data if you want. You can just defrag ME and then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to 'shrink' the ME partition. Then install. Grub installed in the MBR will give you an option to boot either system.

---

### Post by Destroyer14094 on 2007-08-26
oh, wait, is not defragging directly before installing why it didn't work right in the first place? And I didn't realize I needed grub to get dual boot to work, since I have accidently gotten 2 windows ME systems installed at the same time, and it let me go into both(tried repairing existing installation,it  just wrote a 2nd one instead, don't know why, and it gave me the option at startup w/o grub)

What I meant was can I install programs using Ubuntu onto the windows FAT32 partition with Win. ME already installed on it without making a second FAT32 partition?

---

### Post by merlinus on 2007-08-27
ubuntu is linux, and uses ext2, ext3, reiserfs, etc.  windows uses fat32 and/or ntfs.

you can copy data to/from fat systems with ubuntu, but cannot use that format for linux programs.

-merlin

---

