---
title: "FAT32 Partition Shrinking Issue"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by actionmystique on 2014-05-09
Hello everyone,


 I'm trying to shrink a FAT32 boot partition which is 29.89 GB in size, 1008 MB used, 28.90 unused (on a USB drive).
It has been made bootable by Unetbootin with a 4 GB persistent file, which I have then deleted.
The goal is to create another partition after the first one to extend  the persistence above 4 GB. The trick is to give this new partition the  same name as the persistent file (casper-rw).

 
The issue is:
- if I downsize it to 1GB with "**fatresize -v -p -s 1G /dev/sdb1**", I get  the error: "***Unable to satisfy all constraints on the partition***."
- If I downsize it to 2GB with "**fatresize -v -p -s 2G /dev/sdb1**", I get the waning/error:
"[I][B]Warning: File system is reporting the free space as 1894262 clusters, not 1894260 clusters.
Segmentation fault (core dumped)[/B][/I]" and nothing is done.

 Do you have any suggestion?

P.S: The partition table is **GPT**; with ms-dos, there's no problem.

---

### Post by oldfred on 2014-05-09
If gpt try gdisk or gparted.

       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

But if flash drive is 32GB, why not a full install. While a full install takes more space, you then can update entire system and use rest of flash drive for data.

      
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

You do want to change some settings to reduce writes.
I have full installs in both a 16GB flash drive with 8GB for data, / is a bit small. And a full install in my 32GB flash drive. Both use gpt partitioning, but currently boot in BIOS mode.

---

### Post by actionmystique on 2014-05-09
I have to restore my whole system from the live USB and a 1000 GB USB drive of which 200 are backup files. I made a first attempt which stopped for lack of space. The target drive has plenty of free space (more than 500 GB). 
I do not know how much the restore needs on the live USB to succeed.

So I tried to resize the live USB with GParted first, but it crashed. Then I tried manually as explained on the first post.

**Thank you for your link about a full installation on a USB flash drive**. I will give it a try.

---

### Post by actionmystique on 2014-05-13
Finally, I did not follow [this thread]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS") to make a full installation of Ubuntu on a USB stick for 2 reasons:
- it is too complicated; I suppose all these steps were necessary in these old days.
- it is outdated

I found a **much simpler and straightforward way to make a bootable USB stick on UEFI systems**. Let me know if you're interested, I can make a tutorial.

---

