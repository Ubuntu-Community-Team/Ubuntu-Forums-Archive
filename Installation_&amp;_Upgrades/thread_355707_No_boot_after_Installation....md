---
title: "No boot after Installation..."
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by _Matt_ on 2007-02-07
hi at all! sorry me for my english...

I have a computer with Windows XP installed in a 80 GB SATA Hd in a partition of 45 Gb.
in the unformatted space, with the Ubuntu 6.10 LiveCD, i make a 2 GB partition for SWAP and the other space in EXT3 for linux!
with the with the guided installation i install Ubuntu into my HD.
i reboot as he asked to me but the computer don't start GRUB and so windows is boot up...
i remember that during the installation the programme said that GRUB will be installed in (hd0) and if i don't make an error it is the MBR...
i tried to use Super Grub Disk but the system will block if i click on Fix MBR boot ( or something like that ) or Boot GNU/Linux...

i can use linux only with the Live version!!!
HELP ME PLEASEE!!!

---

### Post by confused57 on 2007-02-07
Don't do "fixmbr", since your Windows boots OK.
Boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L", not a one.

This show your partition table(s) & may help  tell you what you need to do to boot Ubuntu & Windows.

You can try to install grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by housam on 2007-02-07
Try to reinstall grub
[http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by _Matt_ on 2007-02-07
i restored Grub but grub don't start and linux can't boot.....

---

### Post by housam on 2007-02-08
OK, try to use the [super grub disk ]("http://supergrub.forjamari.linex.org/")

---

### Post by _Matt_ on 2007-02-08
I tried to use Super Grub Disk but when i click on "Fix Gnu/Linux Boot " and it tried to search /boot/grub/stage1 it block.... and i had to reset manually...
it's the same thing if i click on "Boot Gnu/Linux Directly"
the other metods to restore GRUB by the LiveCD don't solve the problem....
HELP ME PLEASE :P

---

### Post by adrian15 on 2007-02-08
Can you please try SGD 0.9550?

There are some problems with 0.9575 version but I haven't managed yet to reproduce them myself.

Although Fix Boot of Linux may fail, Boot Linux should work for you in this version. 

Thank you.

adrian15

---

