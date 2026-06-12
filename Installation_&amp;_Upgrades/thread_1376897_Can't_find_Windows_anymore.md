---
title: "Can't find Windows anymore?"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by mooseman99 on 2010-01-09
My primary OS (Windows 7) which I had installed before ubuntu is not in the Grub Menu and I can't figure out how to boot it up. (It's not in menu.lst either)

I just installed ubuntu, I partitioned it by shrinking my window 7 partition (in windows) and formatted the free space for ubuntu.
I can see the windows file system and access the files (143 GB Filesystem in Places) but I can't boot to it

Anybody know how to fix this?

---

### Post by darkod on 2010-01-09
First try updating grub by executing in terminal:
sudo update-grub

Notice if it lists that it found Win7 loader. Reboot and check if it worked. Then we'll see.

---

### Post by mooseman99 on 2010-01-09
Nope, no luck.  Still only lists 5 versions of Ubuntu when i boot it:
ubuntu 9.10 kernel 2.6.31-17 generic
ubuntu 9.10 kernel 2.6.31-17 recovery mode
ubuntu 9.10 kernel 2.6.31-14 generic
ubuntu 9.10 kernel 2.6.31-14 recovery mode
Ubuntu 9.10, memtest86+

weird cause i can mount the filesystem and access all my windows system files
Note: it also did not detect it during installation, and didn't prompt me to import settings

---

### Post by mooseman99 on 2010-01-09
Also when i go into ntfs config the only thing I see is a popup with a checkbox to enable or disable writing to external hard drives

and fdisk -lu says /dev/sdb doesn't contrain a valid partition table

please help!

---

### Post by mooseman99 on 2010-01-09
Solved it
did some detective work and found this article
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

which wasn't really about my problem but I tried the bit at the bottom, adding the windows section to the boot menu, and it worked

Thanks to all who tried to help

---

