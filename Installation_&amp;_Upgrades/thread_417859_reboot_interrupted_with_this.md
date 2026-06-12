---
title: "reboot interrupted with this:"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by ecionci on 2007-04-21
Has anyone experienced this problem of restarting being interrupted and I have to control-D to have it
continue. I looked in /var/log/fsck/checkfs  and found this:

Log of fsck -C -R -A -a 
Sat Apr 21 23:32:02 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=de60d610-18b3-43c8-a816-05e605eec803'

/dev/sda6: clean, 127431/2113536 files, 1030883/4225087 blocks
fsck died with exit status 8

Sat Apr 21 23:32:02 2007
----------------
I can't figure what the heck is the "UUID stuff" and also my partitions labeled sdaX instead of hdaX as
before. I (thursday past) upgraded to feisty.

tia
eci

---

### Post by autocrosser on 2007-04-21
UUID has been the "recomended" way to identify your drives from the testing days of Edgy--Feisty now ships with a kernel that polls for SATA instead of IDE/ATA--that is the reason for the sdX instead of hdx. I would guess that Feisty mis-identified your boot partition during the install, look for threads about UUID (I've posted several) to repair the problem.

If you have a hard time---E me.

---

### Post by ecionci on 2007-04-22
Thanks much, I was just doing a man fstab when I saw that you replied. I'll do as you suggest.
tnx

---

### Post by ecionci on 2007-04-22
> **autocrosser said:**
> UUID has been the "recomended" way to identify your drives from the testing days of Edgy--Feisty now ships with a kernel that polls for SATA instead of IDE/ATA--that is the reason for the sdX instead of hdx. I would guess that Feisty mis-identified your boot partition during the install, look for threads about UUID (I've posted several) to repair the problem.

If you have a hard time---E me.

Again thanks. I found in a post that one can do "blkid" which I did. I then went to /etc/fstab with gedit as
root and entered the proper uuid's. No wonder feisty had a small problem. I am using THREE distros of
linux and winxp.  My preferred distro, of course is UBUNTU most of all because of it's makers philosophy
and friendlieness of it's users.

thanks all
eci

---

