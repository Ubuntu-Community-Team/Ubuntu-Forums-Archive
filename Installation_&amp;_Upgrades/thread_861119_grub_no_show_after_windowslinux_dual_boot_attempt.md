---
title: "grub no show after windows/linux dual boot attempt"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by deaniopo on 2008-07-16
Hi, im new to Ubuntu and have been doing the best i can to put off asking you guys for help as this is probably and hopefully something really simple. 

I reinstalled XP and defraged then followed this tutorial to instal Ubuntu ready for dual boot:

[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

this seemed to work really well, and at the last stage, it installed grub and detected my XP install as it should do. Only problem is, when i restart, it just boots into XP as usual. No grub to speak of. 

Ive tried using superGrub disk and after using "liveswap" as it suggested (as i have multiple hard drives), i then used the "fix boot of linux" option where it hung trying to embed something in the boot/grub/ directory. So i then used the liveCD to try and do it manually using:

sudo  find /boot/grub/stage1

and i get the error "/boot/grub/ does not exist". so i went and checked and there does appear to be no grub directory in /boot/

im fairly sure the linux install went fine as it completed properly and i checked gparted and its all partitioned correctly with a big windows one (sdb1) and a smaller partition (sdb2) seperated into a linux partition (sdb5) and a swap partition (sdb6)

so this is where im at. all id like it to get grub to show up at startup so that i choose Windows or Linux.

If you guys can help me out that would be much appreciated. Thanks lots and lots

---

### Post by VMC on 2008-07-16
Boot up using the Livecd and from a Terminal ("Applications > Accessories >Terminal"), type the following:

```
sudo fdisk -l
```

Then come back with the results. Also if you know how to mount the linux partition and output grub menu, that would help. If not just wait until we see how your drives are configured.

---

