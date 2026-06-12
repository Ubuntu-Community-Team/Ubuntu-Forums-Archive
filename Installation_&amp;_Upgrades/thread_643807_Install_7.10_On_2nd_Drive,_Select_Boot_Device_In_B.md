---
title: "Install 7.10 On 2nd Drive, Select Boot Device In Bios"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by pd2004 on 2007-12-18
In an effort to downsize my life, I want to use my work laptop for both work and personal computing. Instead of dual booting, which IT Admins at work would hate, the plan is to have an alternate removable boot drive. 

My Plan:
1. When the system is starting I will select the boot device in bios.
2. Selecting Drive 1 will boot normally from the main HDD. I will remove my personal drive before booting.
3. Selecting Drive 2 will cause bios to boot from my Ubuntu drive.

Facts:
1. My system is a Dell Latitude D620, 4Gb Ram, 2 x 100Gb HDD.
2. Use Daemon Tools soft dvd for the ubuntu install iso.

My Question:
How to install Ubuntu on the second drive without modification of the bootloader on the plrimary system drive?

Thanks.

---

### Post by src2206 on 2007-12-18
>  My Question:
How to install Ubuntu on the second drive without modification of the boot loader on the primary system drive?You can always press **F8** just before the time of booting but after the POST screen, that will give you options to choose boot device.

Though I would suggest the following:

[LIST]
[*] Start the install process of Ubuntu.
[*] Fill up all the necessary details.
[*] In the confirmation screen (most probably) at the bottom right corner you should find an option "Advance".
[*] Choose it and enter the location of the boot loader/GRUB as (fd0).
[*] This will install Ubuntu GRUB in the floppy.
[*] Now just get in the BIOS and change the boot sequence to Floppy as the First Boot Device. Keep your Windows HDD as later boot devices.[/LIST] 
Now if you have the Floppy in the FDD bay, Ubuntu GRUB will load, otherwise your PC will boot as usual in Windows.

BTW,

How do you plan to use DAEMON TOOLS to install Ubuntu? You must have a Ubuntu disc to physically boot from a PHYSICAL CD/DVD Drive. Daemon tool creates virtual drive and requires Windows to run (AFAMKG). Sothese drives are temporary in nature.

---

### Post by logos34 on 2007-12-18
If you don't have a floppy drive or would rather boot from hard disk, in the Advanced>Grub bootloader dialog box mentioned above you would type **(hd1) **in place of the default (hd0)--this will put grub on the MBR of the usb drive.  Follow these instructions (->[post #502]("http://ubuntuforums.org/showthread.php?t=80811")) to change menu.lst afterward so you can boot straight to usb.

---

