---
title: "Lost grub menu"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by Aya Dream on 2007-11-05
I had Ubuntu 7.4 up and running perfectly in a dual boot environment using grub. WinXP on C: drive and Ubuntu on S: drive. Grub sitting in mbr of C: drive with Ubuntu and WinXP options.

C: drive crashed (lots of brownouts here) and mbr corrupted. Couldn't access WinXP or Ubuntu 7.4. Recovered mbr via fixmbr from Windows recovery console and lost the grub menu.

Inspection of the S: drive still shows the whole Ubuntu file structure including /boot/grub with stage1, stage2 and *stage1_5 files. Also menu.lst and device map are present and look correct.

How do I get Ubuntu to boot without putting grub in to my C: drive mbr. How do I recreate my grub to either put it on a floppy (i.e. boot Ubuntu from floppy when I need it) or put it on to the C: drive and have the windows boot.ini invoke the Ubuntu boot 

I've seen many tips on creating FAT32 partitions and amending boot.ini or putting the grub onto floppy at the end of installing Ubuntu. My problem is that Ubuntu is already installed and I really don't want to have to re-install from scratch again. How can I recreate the grub install process without re-installing?

Any help appreciated
Thanks 
AD

---

### Post by bulldog on 2007-11-05
[http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make](http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make)

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Something to read.........

---

### Post by Aya Dream on 2007-11-05
Bulldog, thanks a lot for you prompt and informative reply. I'm sure those articles will sort me out one way or the other.

Believe it or not I did google 'boot ubuntu from floppy...' etc but never came across those articles. I appreciate your knowledge and experience. Thanks
AD

---

