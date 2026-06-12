---
title: "Clean Re-install of Ubuntu - Live Disk Not Recognized in GRUB"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by cftsr71 on 2011-04-18
I have an old HP PC with 2 drives: Primary (C = 20GB) and a slave (E = 60GB).
I have Windows XP Pro OS (which I want to completely replace with Ubuntu). 
Ubuntu 10.10 is installed on E as a side-by-side (with XP on C). 
I am done testing Ubuntu and now want to completely replace the XP OS.
Ubuntu is installed on E-drive as a partition. 

ISSUE: When I log on the PC goes directly to the GRUB menu
but I get no option to boot from the Live Disk 10.10 during the boot-up.

HISTORY: I have tried (unsuccessfully) to remove Ubuntu from my E-drive 
by use of the uninstall function from Windows control panel. 
I have also tried to remove it using the manage/Disk Management process 
but the "Format" and "Delete" options are unavailable (grayed out) so cannot use that. 
 I would like to do a complete clean up and fresh install of Ubuntu as my only OS.

I have read and tried a number of internet articles / recommendations about 
opening  BIOS and redirecting the start-up to the disk, but I do not get any 
 option or any time during the boot to do that.

QUESTIONS:
1) How can I get my HP PC to boot from (recognize) the Ubuntu Live Disk (CD)?
2) Would a complete removal and clean reinstallation be a better approach?
3) And how can I remove Ubuntu from the partition on E (as I want to dedicate the C-drive exclusively for Ubuntu)?

This is my first post so please be patient.  I am unfamiliar with this part of the installation process.

Thanks.

---

### Post by mörgæs on 2011-04-18
Hi, welcome to the fora.

You could boot into Ubuntu and open Gparted. From here you can delete the Windows partition(s).

A complete reinstall is also an option, but Gparted should do the job, if it all right with you that Ubuntu will sit on the 60 GB drive.

---

### Post by cftsr71 on 2011-04-18
Thank you for the extremely prompt and clear reply!
I will investigate this and let you know the results!
Best to you!

---

### Post by garvinrick4 on 2011-04-18
In Bios set CD to boot first: You can usually get into BIOS by hitting f2 or f10 or esc on some during boot. Have to be quick.
Windows reads drives by C,D,E and so on gives them letters.
Linux gives drives sda or sdb or sdc and the partitions are the sda1, sda2,sda3 and so on.
A second drive is the sdb and partitions are sdb1, sdb2,sdc3 and so on.
Can get your linux partition list by running this in Terminal in live cd (install cd using Try Ubuntu) or from a install by:
sudo fdisk -l (lower case L that is)
#Can reformat only when a partition is not mounted and use gparted in live Cd because nothing is mounted in Live cd.  Grayed out usually means partition is mounted. 
How did you install if cannot get CD to mount?
If you are using WUBI install you can uninstall by a folder in Windows called Ubuntu right
next to users or add and remove programs in Windows. Preferable in UBuntu folder.

##Must get CD to boot before Hard Drive in BIOS before can do anything with Live CD .

---

