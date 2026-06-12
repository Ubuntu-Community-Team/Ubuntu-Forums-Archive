---
title: "Ubuntu 12.04.02 install on Asus G75VX is not showing any partition table on an SSD."
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by MrCoke on 2013-08-07
I am trying to dual boot install windows 7 and Ubuntu 12.04 with this laptop. it came with windows 8 so I had to disable secure boot and uefi stuff to even get windows 7 installed. about half of the 256gb lite on ssd is currently installed with windows 7 but when I start the Ubuntu install (I have to use the nomodeset option to get the install to boot) it sees the 256gb SSD... but it doesn't show the NTFS partition with windows 7... it says the whole disk is free space. any ideas?

---

### Post by oldfred on 2013-08-07
Did you install Windows 7 in BIOS mode where Windows 8 was UEFI. Windows installer will convert the gpt partition table to MBR(msdos) but does not convert backup gpt partition table. Then Linux sees MBR and backup gpt and does not know what you have?

       sudo parted /dev/sda unit s print

If drive is still gpt install gdisk and run this:

 sudo gdisk -l /dev/sda

If backup gpt table is the issue, you need fixparts.
      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Since system is UEFI capable, and if Windows is in BIOS mode be sure to install Ubuntu in BIOS mode. If Windows is UEFI be sure to install Ubuntu in UEFI mode. You should get both options from UEFI menu, but may need to turn UEFI on or off or turn Legacy/CSM/BIOS boot mode on or off.

---

