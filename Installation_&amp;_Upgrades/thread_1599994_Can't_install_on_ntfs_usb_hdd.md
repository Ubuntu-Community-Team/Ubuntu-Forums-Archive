---
title: "Can't install on ntfs usb hdd"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Hairo C on 2010-10-18
When i install xubuntu 10.04 in a ntfs patition of my usb hdd using wubi i get the grub shell...
but when i install it in a fat32 partition (i use it for other purposes)   it works fine... but the 4gb limitation is very painfull...

any help for installing it on the ntfs partition??

---

### Post by C.S.Cameron on 2010-10-18
If the only problem with installing to FAT32 is the 4GB limit for persistence, then you can make a ext2, 3 or 4 partition and name it casper-rw.
Then run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

---

### Post by Hairo C on 2010-10-18
As i posted the fat32 partition is being used for other purposes (softmodded wii)....
There's a way to installing it on the ntfs partition??

---

### Post by bcbc on 2010-10-18
It shouldn't make any difference to wubi whether it's ntfs or fat32 other than the size limitation for fat32 (in which case you get a separate usr.disk if you go over 4GB). Or the fact that it's a USB drive.

---

