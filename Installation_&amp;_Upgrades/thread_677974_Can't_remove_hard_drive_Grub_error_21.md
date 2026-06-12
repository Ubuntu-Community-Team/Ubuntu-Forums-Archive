---
title: "Can't remove hard drive Grub error 21"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Deadheded on 2008-01-25
I have 4 hard drives in my system

hd0 /dev/hda  (windows)
hd1 /dev/hdc  (NTFS storage)
hd2 /dev/hdd  (FAT32 storage)
hd3 /dev/sda  (Ubuntu 7.10)

I need to take out hd2 but when I do I can not boot.  I get the grub error 21

I changed the root section in the menu.lst from hd3,0 to hd2,0 but I still get the same error

even edited the device.map but that had no affect.

any help out there TIA....

Hed

---

### Post by Pumalite on 2008-01-25
Post:
sudo fdisk -lu

---

### Post by Deadheded on 2008-01-25
Answer my own question

shutdown and remove the drive.

Boot with live CD, open terminal and run 'sudo grub'

enter command:

"root (hd2,0)"    (hd2,0 is the location of my linux kernal7)

then enter:

"setup (hd0)"  (This updates the MBR of the primary disk)

"quit"

then reboot.

at the grub menu hit 'e' to edit and 'e' again to edit the line "root (hd3,0) and change it to (hd2,0)

press 'b' to boot your system

Once you are in your system edit the '/boot/grub/menu.lst' file and change (hd3,0) to (hd2,0).  save and reboot and all should be working
7

---

