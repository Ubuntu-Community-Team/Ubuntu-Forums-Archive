---
title: "Uninstall OR stop booting on laptop"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by samiles on 2008-08-12
Hi, 

When I turn on my laptop it comes up asking if I want to run ubuntu or windows.

After a few secs it selects ubuntu.

I am giving my laptop to my Nan, and to make iut easier for her to use, is there a way to either:

uninstall ubuntu completely;

OR

make it so that ubuntu does not show up in the list of operating systems (I dont really care if a ll of the ubuntu files are there but just can't be accessed;

OR

make it so that windows is the one selected instead of ubuntu so that if you do not use the arrow keys to change list it just selects windows after a few secs.

Thank you very much for your help,

Sam

---

### Post by ibutho on 2008-08-12
You can use the [SuperGrubDisk]("http://www.supergrubdisk.org") to restore the Windows bootloader. If you want to keep grub and let Windows be booted by default, you need to edit /boot/grub/menu.lst and change
```
default 0
```
to whatever number matches the entry of Windows. You start counting the entries from 0. If you want to completely remove Linux, get the [Parted Magic]("http://www.partedmagic.com") disc and use it to remove the Ubuntu partitions. You can then use the Super Grub Disk to restore the Windows boot loader.

---

