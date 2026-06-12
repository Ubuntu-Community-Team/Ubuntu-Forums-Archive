---
title: "Dual Boot Windows XP and Ubuntu 10.10 without WUBI"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by jxgreat on 2010-11-26
I want a well maintained guide which shows how to dual boot windows xp and ubuntu 10.10 without wubi and not corrupt my Windows Installation.

thanks

---

### Post by dino99 on 2010-11-26
here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

when the installer will ask you to install grub, choose the hdd where ubuntu is installed

---

### Post by sikander3786 on 2010-11-26
This page is worth reading.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

And after that, you should have some queries, post them here and we might be able to guide you till the end.

Good Luck!

---

### Post by xeonmax on 2011-02-22
> **dino99 said:**
> here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

when the installer will ask you to install grub, choose the hdd where ubuntu is installed


i did this......
but when i restart the system it opens windows xp directly...
why is it so?

---

### Post by sikander3786 on 2011-02-22
> **xeonmax said:**
> i did this......
but when i restart the system it opens windows xp directly...
why is it so?
For a basic idea of Ubuntu partitioning, see here.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

If you think Ubuntu was installed correctly and is not booting, boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us dig deep into your boot problems.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

