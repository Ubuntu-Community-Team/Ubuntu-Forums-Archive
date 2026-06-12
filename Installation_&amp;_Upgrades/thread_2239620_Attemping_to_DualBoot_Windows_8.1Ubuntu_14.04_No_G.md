---
title: "Attemping to DualBoot Windows 8.1/Ubuntu 14.04: No GRUB2 Boot Menu"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by daniel181 on 2014-08-14
Hello everyone! This is my first time posting on this forum. Recently I have attempted to dual boot my new Toshiba Satellite S55 - A5167. I have still had no success thus far. This is not my first time trying to dual-boot but it is my first time trying to do it in UEFI. 
I have followed the following guide: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
It appears as if Ubuntu is installed in my machine but I am not getting the GRUB2 bootloader when I reboot my machine. Here is the log from the boot-repair I ran: [http://paste.ubuntu.com/8049129/](http://paste.ubuntu.com/8049129/)

Before posting, I tried to identify the problem. I noticed the following from the log:
```
No boot loader is installed in the MBR of /dev/sda.
```

So I tried to do an installation of GRUB by booting into the live session and attempting to install it on the partition. I have had no success. 
I would like some guidance on how I could attempt to solve this problem. Thank you very much for taking the time to read my post.

---

### Post by ubfan1 on 2014-08-14
Having no Master Boot Block bootloader is perfectly expected in a UEFI machine, even if it existed, it would be ignored.  UEFI uses firmware to point to bootloaders (as many as you can fit) in the FAT file system in the EFI partition.  Ubuntu's bootloaders get put into /EFI/ubuntu.  An entry in the nvram should point to the ubuntu bootloader (run sudo efibootmgr -v to list them from the live media).  Maybe the Windows bootloader is just first, and grub never even gets to run.  You should be able to select grub (providing it was installed properly), by starting the EFI boot menu (usually some function key at power-on) to select boot devices.  Your Toshiba may just list HDD for the hard disk, select that, then you should get another window with the Windows and Ubuntu bootloader choice.  Choose ubuntu and see if you boot.  You can reorder the boot order wth efibootmgr too, but Windows will keep changing the order back, so learn how to use the efi menu.

---

### Post by daniel181 on 2014-08-14
Well, I hate it when stuff like his happens but as of 10 minutes ago, I got Ubuntu running in my machine. What I did was simply reset the BIOS settings to its factory values. The things is, I actually am not sure of what changed. Now I am greeted with the GRUB loader and I can select the OS I want to boot into. Thanks for the assistance though. I greatly appreciate it.

---

