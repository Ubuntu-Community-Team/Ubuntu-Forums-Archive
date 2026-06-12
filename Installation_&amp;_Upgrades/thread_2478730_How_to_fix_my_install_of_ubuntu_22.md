---
title: "How to fix my install of ubuntu 22?"
date: 2022-09-03
forum: Installation &amp; Upgrades
---

### Post by artunix on 2022-09-03
How do fix my install of ubuntu 22? I currently have it installed on 160gb hd, and it works ~ok~
recently I installed on a 128gb hd and ran two maybe three times, but then I could not get it to boot into ubuntu any more.
Sc160 is my 160gb laptop, lets do the math 160gb – 127gb = 33gb used; sc128 is my 128gb hd lets do the math again 128gb – 33gb used =  95gb free; BUT my 160gb laptop also has the following installed:
o160installed1, o160installed2, and o160proinstalled. 


The 128gb just has the newly installed 22 with defaults installed(and updates), nothing like the items or amount of items installed on the 160gb hd!
Sc128prep show the info on the 128gb hd.

160gb – 127gb = 33gb used

128gb – 33gb =  95gb free

right now the 128gb will not boot to ubuntu. it only has ubuntu on it!

Any ideas; don’t say reinstall, have done that several times now!

---

### Post by artunix on 2022-09-03
reached Attachments limits so here you go:

---

### Post by yancek on 2022-09-04
>  o160installed1, o160installed2, and o160proinstalled.  

I don't know what you are referring to with the above information.  Where do you get the 33GB?  Your first image shows the 160GB drive with 127GB free while the second image with the 127GB drive shows 6GB free.  Once you get close to 95% full on a drive partition, you will begin to have problems as the Linux filesysem saves 5% for its own use.

Your 160GB drive shows the first partition as a FAT filesystem of about 500B which looks like an EFI partition but the only other partition is an Extended partition with a logical partition (sda5) on which you presumably have an Ubuntu installed.  The second drive has similar partitions and the drives are LegacyMBR drives.  Are you using the EFI partition at the beginning of each drive?  Do you have an option in the BIOS firmware to boot from EFI file?

Might be best to post more details which can best be accomplished by downloading and running boot repair.  It is at the link below.  Use the 2nd option explained on the page using the ppa and when you run it, make certain to select only  Create BootInfo Summary.  Do NOT try to make any repairs as that could lead to further problems.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Impavidus on 2022-09-04
Find out what files take all that disk space. It could be overflowing log files, a backup routine that attempted to copy something to a backup drive that wasn't mounted.

---

### Post by artunix on 2022-09-04
> **yancek said:**
> ...  Where do you get the 33GB?  Your first image shows the 160GB drive with 127GB free .....
yes which mean that the 160gb drive with all it's programs, etc., is  using 33gb.

> **yancek said:**
> ...
while the second image with the 127GB drive shows 6GB free....   yes that should not be, because as stated the 128gb drive does NOT have all the programs, etc that the 160gb drive has, _BUT even_ if you were to allow for a use of 33gb you/i should still _have 95gb free!_

math

---

