---
title: "Dual boot xp64 and ubuntu 7.10 with multiples drives and partitions"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by CHER on 2008-02-22
Hi all,

This is my first post ever in a forum, and I hope that it can help someone.

What encouraged me to post this blog was my inability to find advice on what ended up being a very simple issue. What I had read during my research for the dual boot issue was a lot of gibberish without a simple answer so here we are&#8230;  

My task was to install ubuntu alongside with my xp64 with the option of dual booting. I had to do this without damaging my master boot sector MBR, or my existing OS, while achieving the dual boot option.

During the install when I reach the stage of selecting drives/partitions I realized that all of the options were too risky for a computer loaded with information and hardrives; I had three drives with multiple partitions on each, and none of the options could work for me probably because I am new to Linux.

The best way to dual boot and installing ubuntu in the safest manner was the simplest way and is as follows:

Step 1 - Partitioning
I partitioned my 150Gb Raptor in four areas. I left 15Gigs for my xp64 os (NTFS), 6gb for my page file (FAT32 &#8211; faster, and can also be used by ubuntu, 1.5 x ram recommended), 100Gigs for my files, and the rest 21 or so, I left unformatted.

Step 2 &#8211; Backup
Backed up all the important files on another hard drive and ghosted the xp64 partition

Step 3 &#8211; Simplifying
I removed the rest of the drives and left only the one where the xp64 and ubuntu would be installed

Step 4 &#8211; Installing
Then when I reached the stage of selecting installation method, I selected Guided - use the largest continuous free space, and since this was the only drive available the installation went beautifully and without any complications.

The ubuntu Grub at the booting stage is fantastic!

Simplicity worked for me. I hope it does for you as well. Good Luck!

---

