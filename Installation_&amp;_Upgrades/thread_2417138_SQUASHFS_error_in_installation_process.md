---
title: "SQUASHFS error in installation process"
date: 2019-04-21
forum: Installation &amp; Upgrades
---

### Post by alirezaemad94 on 2019-04-21
I am trying to install Ubuntu 18.04.2 LTS as a dual boot beside Windows 10 using a bootable usb-drive. After booting from usb and choosing "Install Ubuntu", I get Errors as shown in the attached picture saying:

    SQUASHFS error: Unable to read gragmennt cache entry [2ceca39d]
    SQUASHFS error: Unable to read page block 2ceca39d, size bb4d.

Can anyone help me with that please?

---

### Post by Dennis N on 2019-04-21
This may help:
[https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)

---

### Post by Rubi1200 on 2019-04-21
First try looking for solutions in the link Dennis N provided. 

Generally speaking those errors often occur because of a corrupted image or a bad burn.

Try downloading the image again and use a different software, I am using Rufus at the moment and have found it to be quite capable.

---

### Post by alirezaemad94 on 2019-04-28
Just to clarify the solution for anyone who may have a problem like me in future, I just changed the usb drive and it worked perfectly!

---

