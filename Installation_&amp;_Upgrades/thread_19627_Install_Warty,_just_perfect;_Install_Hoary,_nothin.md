---
title: "Install Warty, just perfect; Install Hoary, nothing works"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by Olli on 2005-03-12
Hi, you brothers in Ubuntu,

I have been using Warty since October, and distributed it to my adult grandchildren working with computers.

I decided to move one step higher as soon as Hoary preview distribution became available. I reasoned that a clean installation should produce better results than upgrading only. However, this decision started a weird series of calamities.
The installation seemed tp go through cleanly, but as the computer should have rebooted, only two lines appeared: 

        Grub loading stage 1.5

        Grub loading, please wait

and wait, and wait, and wait, ad infinitum.

Grub was installed in the MBR of the first hard disk (hd0).

After ten minutes waiting I reinstalled Warty, to be able to reach my other two OSs, SuSE Pro 9.2, and WinXP. 

A new downloading of the iso file,  checking that md5sum was OK (that succeeded with the fifth (sic!) downloading only), burning to a CD (Nero), and a new attempt to install Hoary.

This time the result was the same, only that the system did not reboot not only after Hoary but also after Warty reinstallation.  WindowsXP installation disk and fixmbr let me open the Windows partition, but no more Linux partitions.

Has anybody experienced the same, and succeeded in correcting the situation?

---

### Post by mips on 2005-03-13
Olli which .ISO did you did you download ? Try Array6 if you havent yet.

cheers
mips

---

### Post by Olli on 2005-03-13
[QUOTE=mips]Olli which .ISO did you did you download ? Try Array6 if you havent yet.

cheers
mips[/QUOTE]

The first attempt was with array6, the latter with hoary-preview-installer, published a couple of days ago.

---

### Post by Olli on 2005-03-17
Mission solved, although by reinstalling Ubuntu.
Operating SuSE I checked the partitioning of hdd, where Ubuntu is installed.
fdisk did not find anything suspicious, but cfdisk /dev/hdd refused to reply what fdisk indicated. Instead it claimed that two partitions did overlap - that I could not understand, as the ends of one partition and begins of the next partition were duly separated according to fdisk. Anyway, cleaning all hdd Linux partitions and reinstalling 4.10 cleared the situation.

---

