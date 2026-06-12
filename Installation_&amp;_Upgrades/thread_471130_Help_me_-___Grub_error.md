---
title: "Help me -   Grub error"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by ubmania on 2007-06-11
Hi!

I have one HD 160Gb on my portable.


I have 4 partition on my HD.

1) 75Gb for Windows Vista 
2) 35 Gb extended partition on Vista
3) 35 Gb for Ubuntu  
4)    swap linux

I worked very well with this installation.


Recently I buyed a Usb Drive with 40Gb. I instaled PCLinuxOS on it.  ( on the final instalation of PCLinuxOS asked me which partition have the boot,  I think I have made a mistake, I selected Hd on Windows Vista.
After that when I reboot the Computer It's give me a **Grub error**. 

I ran LivePC Ubuntu 6.10 and open Gparted application for viewing my partitions. I have  some questions.


My partitions:

     **HD drive**
 /dev/sda       149.05 Gb
........|-- /dev/sda1 ______ ntsf______  1.46 Gb
........|-- /dev/sda2 ______ ntsf _____  75.22 Gb_______ Windows Vista
........|-- /dev/sda3 ______ ntsf _____ 36.80 Gb
........|-- /dev/sda4 _______extended    
....................|-- sda5________ext 3 _______ 35.60 Gb________Ubuntu 7.04
....................|-- sda6 _______ Linux swap ____1.56 Gb

     **USB drive**
/dev/sbd1________7.81 Gb_______ntfs ________/media/NewVolume       
/dev/sdb2_______29.45 Gb _______extended
.........|-- /dev/sdb5___________________ Linux-swap ________________3.96 GB
.........|-- /dev/sdb6 ___________________ ext2____ /media/usbdisk  ____ 25.56 Gb________PCLinuxOS


 
With Manage Flags I clean "lba" flag and "boot" flag for a new boot instalation and I stoped instalation because I don't have any information about "Iba" flag.

Questions?
What partition (/dev/sda) or (/dev/sdb) have I to place "boot" flags or "Iba" flag ?

Any other suggestion for me, for a good Instalation?
I can reformat Usb drive and Install Ubuntu on it.

Thanks

---

### Post by One Quick Question on 2007-06-11
I wonder if PCLinuxOS reinstalled GRUB to the primary device to list itself the main boot partition, which may have caused failure if GRUB tried to read from the USB drive.

I would suspect you want the boot flag on sda5, since that has the rest of the GRUB at /boot, which is what GRUB expects.

As for the lba flag, I dunno.  I don't recall coming across that before.   Do you have Intel Boot Agent on your machine?

---

### Post by ubmania on 2007-06-11
I bouth a Toshiba with Windows Vista embeded.

I wrote this 2 commands:

find /boot/grub/stage1
(hd0,4)
(hd1,5)

find /boot/grub/stage2
(hd0,4)
(hd1,5)


Sorry my English

---

### Post by ubmania on 2007-06-12
Any Suggestions?

---

### Post by ubmania on 2007-06-12
I have no patience, I want to install Ubuntu on USB Drive.

**Before:**
USB drive
/dev/sbd1________7.81 Gb_______ntfs ________/media/NewVolume 
/dev/sdb2_______29.45 Gb _______extended
.........|-- /dev/sdb5___________________ Linux-swap ________________3.96 GB
.........|-- /dev/sdb6 ___________________ ext2____ /media/usbdisk ____ 25.56 Gb________PCLinuxOS

**After:**
/dev/sbd1________37.26Gb_______extended 
.........|-- /dev/sdb5___________________ Linux-swap ________________1.56 GB
.........|-- /dev/sdb6 ___________________ ext3____  ____ 35.70 Gb________New Ubuntu

I selected the option for formating sdb5 and sdb6.

After that Ubuntu asked me where i want to install Grub? **(hdo)**

**[SIZE="3"]Where do I  install the Grub?[/SIZE]**

Sorry my English

---

