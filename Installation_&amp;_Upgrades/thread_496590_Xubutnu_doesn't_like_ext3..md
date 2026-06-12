---
title: "Xubutnu doesn't like ext3."
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by Odrodzona-Sarmacja on 2007-07-09
Description of problem:

1. Xubuntu 7.04 install does not use low format for ext3 partitions and uses eagerly corrupted ext3/ext2 filesystems and corrupted files from earlier installations. It requires preformating its ext3 partitions (like /,/home/,swap and that is a known bug with manual install in all ubuntu installs) with other harddrive manager programs and it works only after changing them first to fat32 and lowformating these partitions. Also Xubutnu installer does not marks any ext3 partitions besides "/" and "swap" as Xpartition, which gives serious errors in windows system, when using dual boot. It can be only resolved by running partition manager in windows os.

2. After the tricky manual (using alternative windows partition manager for most its work) Xubuntu installation everything works fine for long weeks untill torrent client (bttornado in my case) reaches "corrupted download" error, which often happens after removal of pieces with failed hash check and when using ext3 extension for the place of downloading torrent. Then programs like Firefox, Thunderbird and others suddenly are starting to close. Diverse multimedia plugins and multimedia programs like xmms, gxine etc are starting to malfunction. Also when you weren't smart enough to format besides "/" and "swap" partitions also "/home/" partitions, then different programs stop working like firefox, vlc player or bittornado giving segmentation error and you get also from time to time "reinstall gdm" request. They demand total removal in synaptic and then removal of their directories left over in /home/ and then reinstall (in most cases first reinstall is enough) to work again without segmentation error and for some time also without suddenly closing themselves. Also on the corupted partition all files have some (about 10%) chance to get corrupted or segmented when being copied, edited, torrented or even downloaded by get-apt install.

3. Removing corrupted files in ext3 filesystem from /home/ directory on "/" partition gives critical errors, marks all files as system read only and demands reboot with manual use of fsck (i recomend using fsck -y unless someone feels like pushing "y" button for 30min) afterword. When removing the same corrupted files from /home/ directory on ext3 "/home"  partition doesn't mysteriously result in alike catastrofic situation.

My request for help:

I'm new to linux, but all that stinks long way that ext3 is highly instabile filesystem and for torrenting (which goes over 24 hours) large files better is to avoid ext3 on xubutnu 7.04 and use rather fat32 filesystem (mounted through /media/ directory) for that purpose. I don't know if this is some critical bug in ext3 system or simply Xfce destroys ext3 partition unintentionally due running all these continous logging background system processes (like that idiotic gam_server, which also causes some documented bug in ubuntu), or also intentionally (to disable use of torrenting on ubuntu) when it is also torrenting large files for longer times.

If this really happening because of some intentional setup of ubuntu os against torrenting on Ubuntu or just against torrenting of large torrents on Ubuntu, then I would like to have that officially confirmed.

I would like to know if there is any tool in Ubuntu alike ext3-scandisk and ext3-defragmenter on linux, so i could run "surface check + corrupted file system check" and then defragment my 60GB ext3 "/home/" partition so I can copy over there larger files from my fat32 partitions without causing "corrupted" errors. So long i only noticed that fsck is totally useless for that purpose and when run in maintenance shell without any "critical system error" on partition it totaly destroys entire file structures on the partition and put it into found&lost directory often in so small pieces that there is no hint which file belongs to which directory.

---

### Post by kerry_s on 2007-07-09
My first thoughts you have a bad disk. so the next time you install try reiserfs if you still have a corruption problem, than something is wrong with your hardware. ext3 is a widely used file system and very stable. i use ext2 myself cause i'd rather have the speed than the journaling.

---

### Post by Odrodzona-Sarmacja on 2007-07-09
> **kerry_s said:**
> My first thoughts you have a bad disk. so the next time you install try reiserfs if you still have a corruption problem, than something is wrong with your hardware. ext3 is a widely used file system and very stable. i use ext2 myself cause i'd rather have the speed than the journaling.

Next time? :) Let's hope not. :) Installing Xubuntu one more time is something I want to avoid if possible. If Xubuntu wasn't comming with that malfunctioning and buggy as it seems (I hope only not by design) partitioning/formating tool in its installer, then it wouldn't be such a horror at least.

I don't think there is any problem with my disk, but i could have some problems on it, which fat32 deals with pretty well and ext3 is just stumbling and dying over them (maybe because it is not so very stable file system as people would like to see it after all). Funny thing is that fsck downgrades ext3 into ext2, when it finds journal log corrupted too. I'm most curious about diagnostic&repair tools for ext3, which perform better then that crude fsck tool at finding corrupted files (faulty or crossed inodes is not something I am interrested in) and fixes them without damaging the structure of the ext3 file system like scandisk do on fat32. So firefox and other programs won't close at random when i am using them now when I was so smart to format additional partition for my "/home/" directory. ;)

Once upon the time there were two good video formats called asf and xvid. asf was widely used, very popular and very stable. It had only problem that there was no diagnostic and repair tool for asf files, Yeah... asf was hugely stable and popular, so why people don't use it anymore? Are there really no diagnostic&repair tools for ext3 too?

---

### Post by Odrodzona-Sarmacja on 2007-07-10
I just checked my "/home/" partition with "gparted" and of some reason it seems the partition seen by "gparted" is smaller by 1gb from the one i formated in "partition magic". It is maybe also the reason why one of my ext3 partitions gets corrupted all the time.

This reminds me about curious problem I had, when i was trying earlier to reformat already extisting "/" "/home/" and "swap" xubuntu partitions by first erasing them in manual setup in ubuntu installer and then formating them anew again with that ubuntu installer... The free space available was getting smaller and smaller every time I did any more particular resizing of a partition or erasing of a partition or creating of a partition.

Therefore I think that the "gparted" used by Xubuntu 7.04 installer comes with some critical bug, which eats available space, when manual setup of partitions is used which leads to ext3 file system corruption. Therefore Xubuntu 7.04 doesn't like ext3 file system.

---

### Post by Odrodzona-Sarmacja on 2007-07-31
I've resized with gparted livecd my "/home" partition, as it seemed ubuntu erased 7mb from my original preformated partition size. I hope it shall stop the file coruption in ubuntu.

I also noticed that launching windows program with wine crashed my ubuntu and introduced file system errors on my both "/" and "/home/" partitions... during the crash i saw also lots of ext3-journal errors on my "/" partition. However in lost&found after fixing it i found like twenty text files all begining with word "MCOP-Object:".

---

