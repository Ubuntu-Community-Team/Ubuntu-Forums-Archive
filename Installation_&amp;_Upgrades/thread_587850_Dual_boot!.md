---
title: "Dual boot!"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by FnTm on 2007-10-23
Hi!

I have this question.

I have 2x40gb HDD's set up in a FakeRaid0, and they have Windows on them.

I allso have a 250gb HDD, that was mainly thought to be for files only, but i decided to install Ubuntu on it.

so:
1) Will grub be able to do a dualboot? Will I be able to chose between linux and windows when starting my system?
2)Do I need to know anything in particular about linux partitions, or do I just select free space (or something) because I have never done anything like this before.

Thanks

---

### Post by 1/0 on 2007-10-23
You should follow an installation guide, but yes you will be able too choose which os to boot via GRUB. As for the partitioning: its something users who are interested in computers argue a lot about. 

You can let Ubuntu choose for itself but I wouldn't.

I recommend a separate /home partition. That way you can update or switch distro later (usually requires a format of root). That way you just fo, install/upgrade and then mount the old /home partition as /home WITHOUT FORMATING HOME. 

You need a swap partition of roughly twice your RAM (some say splitted in two for speed but I haven't noticed much of a change). You need a root partition of (depending on how much you are going to install) at least 3,5 Gb, I recommend 5 Gb. And lastly a separate /boot partition of about 64 Mb (yes Mb not Gb). 

As for file system I recommend the good old ext3 for root and home. It is dependable and pretty fast. You will not loose all data if the computer crashes or looses power (as is the case in many others s.a. Reiserfs 3,4, XFS, aso). Ext2 for boot (no journaling needed) and SWAP pretty much says it. 

I recommend these tweaks of the file system to improve speed and remove irritating fs checks that has never ever found anything for me. Note this has to be done with all partitions unmounted so boot from the install CD, KNOPPIX or any such but have the partitions unmounted.

The ext3 performance tweaks:

```

tune2fs -O dir_index /dev/sdXY
e2fsck -D /dev/sdXY 
tune2fs -O has_journal -o journal_data /dev/sdXY
tune2fs -c 0 -i 0 /dev/sdXY

```

Do this on all your ext3 partitions (root and home), where XY is the partition. For instance /dev/sda1 or /dev/sdb3.

Well I'll write down a recommended partition table for a computer with 1 Gb memory and 250 Gb HD.

/boot 64 Mb ext2
SWAP 2Gb
/ 5Gb ext3
/home the rest ext3

I hope that helps.

---

### Post by FnTm on 2007-10-23
Oh... damn, forgot to mention.

the 250gb drive allready has about 180gb filled, so what do i do now? Just proceed, as if i would have a 70gb drive? and do as you said?

---

### Post by 1/0 on 2007-10-23
Yes, pretty much the same. You'll need ntfs-3g installed to read and write info from the ntfs partitions. Oh, and the NTFS file system will still be fragmenting the bits so the defrag **** will continue and the FS will get horribly slow if you store much (+~90%).

Good luck! And remember, dont fsck up!

---

### Post by Lardarse on 2007-10-23
I don't know if I should tag onto this thread, but my problem is similar. I'm trying to work out how to to setup Ubuntu 7.10 to dual boot with Windows XP. My system has a single 300GB hard drive (reported as 279GB) which is used completely by an NTFS partition (apart from the customary 8MB that it likes to always leave behind), and is just under half full. It also has 2GB of memory.. I can see 2 methods of approach to this, and I am not sure which would be easiest in the long term:

1: Repartition the hard drive. Allocate roughly 40GB to Ubuntu, and keep the rest dow Windows. The problem that I can see with this is that I don't understand how to repartition it. The installer for 7.10 doesn't show an option to resize the main partition (like the installer for 6.10 did when I was installing it on another computer), and I am worried about losing data that I have no easy way to back up.

2: Install a separate 120GB hard drive that I have spare (it used to be in here until earlier this year) and install Ubuntu on that. Opening up the computer isn't a problem for me, as this computer is self-built, but I am unsure how to make dual booting work with that.

Any thoughts on this would be welcomed...

---

### Post by 1/0 on 2007-10-23
Well "Lardarse". You're right about the need for empty partitions. Since NTFS is proprietary and build the way it is, other OS:s are not gonna be of much help to repartition the Microsoft FS. There are companies that try to do this (check/buy for instance Partition Magic from Symantec) but there's no warranty that it'll succeed nor that it won't loose your data. 

My suggestion is that you plug in the extra drive and use parts or the whole one for GNU/Linux. As for setting up GRUB on it, it shouldn't really be a problem but I haven't used Windows since 2000 so I'm a bit rusty...

Grub will set up in any MBR and will be able to boot XP, GNU/Linux aso. (No clue about Vista.) The tricky part is whether the drive should be master or slave. You can set the drive as slave (although the opposite usually is better) but you might have to change the boot order in BIOS to CDROM, HD1, HD0 instead of CDROM, HD0, HD1. 

I'm not sure you will need a 4 Gb large swap partition. I doubt it'll use more than 1 Gb but that's my guess. 

I hope it helps

---

### Post by Lardarse on 2007-10-24
That was... decidedly painless...

I went with the second hard drive, with 4 partitions like you suggested to the previous person, and putting it in the slave position. GRUB set itself up fine, without having to change the boot order in BIOS.

Now the hard part: moving the computer back where it belongs...

Oh, and call me LA if it's any easier.

---

### Post by 1/0 on 2007-10-24
Congrats mate! Its one of the trickier steps of the install but really not that difficult after all. And yes LA is much easier to say.

---

