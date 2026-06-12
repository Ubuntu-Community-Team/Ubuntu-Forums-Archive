---
title: "MESSED UP INSTALLATION!!Pls help...urgent"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by narayanb on 2006-10-02
>>>
I have a PC with two harddisks....a 40Gb ATA and 160GB SATA.. i hav my Windows XP on the ATA disk.. and Ubuntu Drapper Drake in the SATA...Now in the SATA drive i created a new partition from windows which overwrote the partition table and hence GRUB i suppose..then i lost my bootloader..
>>>
then i put my XP disk and fixed my MBR and cud load windows..
>>>
now to restore Ubuntu.. i read in some thread that there is an Ubuntu Alternate installation disk which helps you restore your GRUB and downloaded it(took 3 days) and burned it... by the time i had lost the thread...
>>>
Now from this CD i selected the option to fix corrupted install and then in the following menu..
(.)somewhere there was an option to install GRUB...i selected that
then it showed the partition list..i set the current installation         partition's mount point as / and then proceeded...
(.) as i proceeded it began to rewrite the partition table then some error came wrong cluster size or something, relating my windows partition in that drive..i clicked ignore and proceeded..
(.) at last it told that the root partition could not be mounted and should it stop the partitioning..i said yes and gave up.
..........................................................................
Again came here and found another thread for restoring GRUB...
->put my live cd and booted frm it
-> went to console..
->gave sudo grub
-> root (hda1,2) (ubuntu is the 3rd partition in SATA drive)
-> setup (hda0)
and rebooted
Now my old bootloader is fixed!!!
but now when i select the ubuntu option from it, it says, unable to mount kernel!!!
please help
and sorry for the long post

---

### Post by Kateikyoushi on 2006-10-02
You have to edit your menu.lst to point to the right HDD and partition.

---

### Post by narayanb on 2006-10-02
i think i hav messed up the kernel or something...not sure..

---

