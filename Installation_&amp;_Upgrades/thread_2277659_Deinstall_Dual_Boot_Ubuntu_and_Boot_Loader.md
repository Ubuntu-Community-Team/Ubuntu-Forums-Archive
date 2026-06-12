---
title: "Deinstall Dual Boot Ubuntu and Boot Loader"
date: 2015-05-10
forum: Installation &amp; Upgrades
---

### Post by istvan5 on 2015-05-10
Hi to all !

I have a Windows XP and an Ubuntu (Lubuntu) installed on a separate partition.
Now the Ubuntu should be removed now. 

Is it enougth to delete and use if needed, the Ubuntu partition?

OR do I REALLY have to repair the "Windows boot loader" ? Maybe it will only don't work
if I select this Ubuntu in the boot menu?


thx for your answers

---

### Post by grahammechanical on 2015-05-10
Do you still want that machine to load Windows XP? If you do then you will have to restore the Windows boot loader. And you must do it before you delete any Ubuntu partitions. The Ubuntu boot loader looks for its configuration files in the Ubuntu partition. Delete the partition and you break the Ubuntu boot loader. You will not get a boot menu.

Regards.

---

### Post by ubfan1 on 2015-05-10
I you are using grub to boot, its files are typically stored on the Ubuntu partition, so you will either have to reinstall grub so its files are on one of the FAT partitions Windows usually has around, or reinstall the Windows bootloader.

---

### Post by istvan5 on 2015-05-10
thx !!!

---

