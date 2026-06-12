---
title: "USB Ubuntu with &quot;own programs and configuration&quot;"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by dempate on 2010-07-17
Hey,

I have a question concerning the USB install feature in Ubuntu.

Can I install the Ubuntu from my Harddrive to the Pendrive with (some) of my own installed programs as well as my own configuration files?
But I don't want the possibility to install more or delete these files. Pretty much like the normal USB install with some additional programs/tools & their configuration so that I don't have to configure them all the time manually.

If yes then could you please give me a link or anything that could help me?

Thank you in Advance.
Dempate

---

### Post by viralmeme on 2010-07-17
> **dempate said:**
> Can I install the Ubuntu from my Harddrive to the Pendrive with (some) of my own installed programs as well as my own configuration files?
Yes, install using the Ubuntu Live USB creator and then using qparted resize the partition and create a new ext2 partition in the remaining space and label it casper-rw. Delete the casper-rw from the fat32 partition. When you boot from the USB any new changes will be permanently stored here.

---

### Post by dempate on 2010-07-17
> ...create a new ext2 partition in the remaining space and label it  casper-rw...
How big should I make the ext2 partition?Bigger than the file is on the usb drive? That would be then around 700MB.

mfg Dempate

---

### Post by viralmeme on 2010-07-17
> **dempate said:**
> How big should I make the ext2 partition
Use the remaining space .. I set mine to these settings on a 4GB device. I tried with an 8GB device and it didn't work. Which USB device works is a bit hit-and-miss.

/dev/sda1             710M /fat32
/dev/sda2             3.1G /media/casper-rw

---

### Post by efflandt on 2010-07-17
If you use the Startup Disk Creator to put bootable iso on USB, you can have a persistent filesystem (casper-rw file, limited to 4 GB - 1 byte, due to FAT32 limitations).  It is best if the slider for that is at least one click (0.1) down from maximum or the install may fail.  I have not tried making a separate partition with casper-rw as its partition label, which is also supposed to work.

You can install extra programs and settings, however, you should not do system updates to kernel or original programs that are in the squashfs that runs before persistent data is mounted, unless you roll your own iso to use with all desired updates on it.  Although, you can do things like wireless settings, and I even edited /lib/udev/rules.d/70-hid2hci.rules for my Logitech diNovo Edge keyboard/mousepad to work (which 10.04 broke).  Hardware Drivers can be temperamental, because with some, you may need to either manually **sudo insmod** them or do that from a script (I did that from /home/unbuntu/.profile for Broadcom STA wl module in 9.10 for one laptop).

However, a regular iso on USB is insecure, since anyone can boot it without password

So if you have large enough USB flash, a regular installation to USB would be better, since it could be updated, and would be more secure.  8 GB is generally considered minimal for full install, but it may work on 4 GB with little space remaining.  You have to make sure that you put grub on the USB stick from the **Advanced** button in the last step.

---

