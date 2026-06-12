---
title: "windows and ubuntu dual boot question"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by mcg1sean on 2007-03-25
hi, currently I have windows on my main hard drive (C drive) and Edgy on my secondary slave drive. but lately I have run out of space on the hard drive with windows on it and would like to remove edgy (gasp!) so that I can use that hard drive as extra storage but the trouble is I dont know how. all I know is that Id have to do something with the GRUB bootloader and possibly the MBR in windows. I just dont know where to start. any instruction would be much appreciated. 

THANKS!!

---

### Post by mardawi on 2007-03-25
Do you have the windows CD?

If you do. Boot form the Windows CD, Choose recovery command line by pressing "R" on the first menu.
Type:
fixboot
fixmbr

This should over-write grub.

To remove Ubuntu and create new partitions. Right-click My Computer select "Manage". goto "Storage">"Disk Management". Delete the linux partitions and create new ntfs and fat partitions as you need.

Good luck!

---

### Post by mcg1sean on 2007-03-25
thanks for the help, I'll have to give it a try

---

