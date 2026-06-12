---
title: "Make Linux Partition Bootable"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by arcwelder on 2010-02-07
I have been using a new System76 Pangolin Performance for a few weeks now with Ubuntu 9.10, and decided that I needed to make it dual-boot with windows (XP home SP 2, since that's the only windows disk I had lying around). 

I followed the instructions on System76's Knowledge Base site, but when it got to the part about using grub to make both OSes bootable it didn't work as expected.  First, it said I needed to install grub, so I did sudo apt-get install grub and then ran sudo grub as it said and followed the instructions with this result:

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found


so... at this point I can boot into windows, and I can run the ubuntu liveCD (which I'm running now) and I can mount my linux partitions and view the file systems... but I can't seem to make them bootable

I tried to make them bootable using "Disk Utility" but when I checked the box "make bootable" it just waited for a few minutes and then returned an error (something about a message and not enough memory...)

in case you couldn't tell I'm very new to linux/ubuntu/dual booting... and I'm sorry if I'm not providing the correct information/explaining things very clearly... I just want to be able to dual-boot windows and ubuntu and hopeully without having to reinstall either.

PLEASE HELP, thank you! :)

---

### Post by mikewhatever on 2010-02-07
You seem to be using the procedure for Grub1, but 9.10 has Grub2. Hence the errors of non-existent files. Check out the link below for reinstalling Grub2.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

