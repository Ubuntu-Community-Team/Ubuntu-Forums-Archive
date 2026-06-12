---
title: "Boot Sector?"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by sooqing on 2006-08-12
Hi!

I found out that whether I used the GUI partitioner, cfdisk or fdisk to partition my HDD (entire drive as one volume), the HDD will always starts from 0.3 MB instead of 0 MB. Is this normal for you guys too or do I have a boot sector virus?

I tried to 'dd' my HDD with zeros too but nothing changed.

---

### Post by Herman on 2006-08-12
> sooqing     Hi!
I found out that whether I used the GUI partitioner, cfdisk or fdisk to partition my HDD (entire drive as one volume), the HDD will always starts from 0.3 MB instead of 0 MB. Is this normal for you guys too or do I have a boot sector virus? I tried to 'dd' my HDD with zeros too but nothing changed. :confused: sooging, I'm sure that I do not understand your question.

Are your asking if it is normal for the first 63 sectors of 512 bytes per sector (the first track of the hard disk) to be not formatted with a filesystem?
63x512=32256 bytes,    32256 /1024 =31.5 kB,  31.5 /1024= 0.03 mB. ?

Then the answer is 'Yes', this is conventional. 

Most partitions begin and end on cylinder boundaries when we use most Linux partitioning software. If they don't we run into problems. (Some partitioning software does not conform with this standard, or is 'buggy').
The exception to this rule is the first cylinder, of which the first track only is not formatted with any file system. 
The first sector contians the MBR, and the rest of the first track is normally empty and is reserved for bootloader codes and similar software. Sometimes hard disk software is installed there, like Samsung's 'Disk Manager'.
When we install Grub, it instalsls it's 'stage1' to MBR (the first sector), and then Stage1_5 to the next 15 sectors, and Stage2 and the rest of Grub (menu.lst and other files) are installed in the Ubuntu partition.

If anyone wants to see for themselves that the first partition does not begin until after sector 63, just enter the following command in your terminal, ```
sudo fdisk -lu
```If you look closely at the fdisk output, you will see that this is true.
Regards, Herman

EDIT, So to make myself perfectly clear, sooging, this is normal, and you have nothing to worry about. :D

---

