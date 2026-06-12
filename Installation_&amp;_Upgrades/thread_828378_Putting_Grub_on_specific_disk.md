---
title: "Putting Grub on specific disk"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by JohnPChambers on 2008-06-13
[FONT="Times New Roman"][SIZE="3"][/SIZE][/FONT]
I have been loading 8.04 from disk I created onto a hard drive of 500 Gigabytes. I however, can't figure out how to get it o load Grub on this same disk. This somehow because of my bios keeps me from booting on the hard drive. I am able to with Mandriva Power Pack on another 500 Gigabyte hardrive, but it allows me to  select drive for login. 
Thanks,
John

---

### Post by logos34 on 2008-06-13
To help us, please post your fdisk

sudo fdisk -l

specify which linux install is which (mandriva, ubuntu), clarify which is bios boot drive, and where you want to install grub

---

### Post by JohnPChambers on 2008-06-13
I have removable disks on a tray. I have both 500 Gigs on a different trey. One is Mandriva, the other is Ubuntu. The Mandriva works fine. The disk is identified in the bios. The channel, etc. may change. However no problem having it boot if the boot loader and it are on the same drive. Just can't figure out how to get boot loader loaded onto that drive when I install Ubuntu.
John

---

### Post by logos34 on 2008-06-13
it's still not clear to me, but try this to reinstall grub onto the desired disk:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

