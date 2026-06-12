---
title: "Dual boot /w WinXP not the 1st partition"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by scb147 on 2005-10-27
First I have a quick question about hard drive speed, etc, then I will get into my main question.

Does the first partition of a hard drive have better response rates compared to a partition that is further out on the platter?

On to my main question:

I have been reading the forums for the last couple hours, and I haven't found anything to describe what it is I'd like to do.  If there is a post, I missed it!

I just recently bought a Dell Latitude D610 with WinXP/SP2 installed.  I want to put both Breezy and XP on it, but I want the disk layout to be similar to the following:

hda1 - /boot
hda2 - /
hda3 - swap
hda4 - NTFS for WinXP

I want to use GRUB for the MBR.

How do I get this to work? :confused: 

Thanks for the help!

---

### Post by fannymites on 2005-10-27
Are you planning re-installing windows xp?  If so you can just partition the disk how you want, install xp to the partition you want then install breezy and that will take care of everything else.  I have XP on a different partition and the breezy install detected it and added it to grub automatically.
If you want to partition and move xp without losing it, that might be more difficult.  
I think I used the partitioner on a pclinuxos live cd to it.

---

### Post by superhew on 2005-10-27
I have had problems with partitioning a disk with windows on it. Something always seems to go wrong :). However, if you defragment and measure your partitions correctly, it should work.  

If you decide to format first (easiest option in my opinion), then make sure you install xp first. using the cd dell gave you probably wont work, since most oem's give "recovery cd's" and not retail windows cd's. if you have an actual install cd that allows you to partition and stuff, thats awesome. you are in luck! 

assuming you have a retail install cd:
format the disk with the xp installer partitioner. partition it how you like, you can either format the partitions other than the ntfs one, or just leave it. since you will have to format it again anyway during ubuntu setup, just leave it unformatted.

finish the install for xp, THEN install ubuntu. windows doesnt give you the option of writing to MBR or not, so to use grub, you have to do linux last.

hope this helps a little. if you have just the oem cd, or this wont work, i can try to think up some other ideas. i have one in mind now, but its a long process, not usually a fun one. 

anyone else have anything to add? im sure im missing something.:D

---

### Post by scb147 on 2005-10-28
Yes, I do have the actual WinXP CD media, not a restore CD.

I've decided that I will just give into WinXP and give it the 1st partition.  I know this way works.

I was trying to come up with an easy way to get Breezy on the 1st partition and put WinXP on the 2nd, but I think it's just going to be a PITA.

If I were to partition my hard drive with:
0GB - 20GB : ext3
20GB - 21GB : swap
21GB - 23GB : FAT32 (transfer b/w Breezy & XP)
23GB - 40GB : NTFS

WinXP wanted me to format the ext3 partition to install it's boot crap on.  That is where I think the problem lies.  So I've decided to just partition my disk as follows:

0GB - 17GB : NTFS
17GB - 19GB : FAT32
19 GB - 39GB : ext3
39GB - 40GB : swap

Install WinXP first, install Breezy, GRUB gets installed in the MBR and recognizes WinXP and viola, dual boot system.

---

### Post by davidsrsb on 2005-10-30
Many laptops have a hidden FAT32 1st partition with the Windows recovery files and have XP installed on the rest of the drive as second partion.
I use partion magic to shrink this back and then use cfdisk from the linux cd to set up my new partitions

---

