---
title: "[lubuntu] Cannot find a way to install Lubuntu on older PC"
date: 2013-12-24
forum: Installation &amp; Upgrades
---

### Post by mihnea13 on 2013-12-24
Hi, I wanted to use Lubuntu 13.10 on an older PC (about 7-8 years old, P4 processor @ 3.2 Ghz, graphic card with 128 mb I think, and 1 GB RAM) but nothing works:

First I tried installing from a live session, but when I get to the screen where I can set up the partitions no partitions appear, and if I click on "Change" or + the installer crashes. If I click on -, I get an error message saying ubi-partman crashed with error code 141. I`ve read about this error on the web and found out it was a bug which occured when you tried installing Ubuntu on a PC that already had a variant of Ubuntu installed. Since I used Xubuntu 12.04 on this PC, I`ve formatted its partition and tried again, same result. I`ve then tried backing up my data and formatting the entire drive, still the same error. I`ve tried installing with no partitions setup (all the space on the hard drive as unallocated) and with a single partition created (tried ext2, ext3, ntfs) but I always get the same error.

Then I tried the alternate installer, but here I have another problem: the USB keyboard doesn`t work so I can`t install it. The strange thing is that in BIOS it works perfectly fine. The same keyboard problem was present also with the live CD: it works in BIOS, then it doesn`t work in the menu where you can change the language (I always have to wait for the counter to run out) and then works perfectly fine after entering the live session.

Other than using a PS2 keyboard, which I no longer have, what else can I do to install Lubuntu? Thank you.

---

### Post by ubfan1 on 2013-12-24
Did you hashcheck the downloaded iso with md5sum?  Do you get output from programs like "sudo fdisk -l"  or "df" for the disk from the live session?

---

### Post by mihnea13 on 2013-12-25
> **ubfan1 said:**
> Did you hashcheck the downloaded iso with md5sum?  Do you get output from programs like "sudo fdisk -l"  or "df" for the disk from the live session?

I did check the hash and it was alright, I didn`t try fdisk or df but in gparted all the partitions were there, that`s what`s weird. Anyway, I managed to find a friend who has a PS2 keyboard and used it with the alternate installer and everything works fine. Thanks, the thread can be closed.

---

### Post by holycow131415 on 2013-12-26
in the future, you could always buy a usb to ps2 adapter.

---

