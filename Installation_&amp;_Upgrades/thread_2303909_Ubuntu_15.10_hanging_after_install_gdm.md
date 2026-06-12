---
title: "Ubuntu 15.10 hanging after install gdm"
date: 2015-11-22
forum: Installation &amp; Upgrades
---

### Post by streak3 on 2015-11-22
I recently installed upgrade to Ubuntu 15.10 on my Toshiba Satellite.. all working fine, and then lost my cursor (sigh).. 
Found a post that indicated perm fix for this:
sudo apt-get install gdm
Did this, restarted, and I hang on a screen:
fsck from util-linux 2.26.2 
/dev/sda1: clean, 392249/30277632 files, 20849708/121099264 blocks
[OK] Started LSB: Tool to automatically collect and submit kernal crash signatures.
....       20 -30 other lines   ....
[OK] Started GNOME Display Manager. 

I then hang there.. at least I know know what GDM stands for ](*,)


Any help greatly appreciated..

---

### Post by streak3 on 2015-11-22
I went back to lightdm .. so now back to original issue of missing cursor :(

---

### Post by SantaFe on 2015-11-22
I don't know if this is the post you saw, but there are several other suggestions here: [http://askubuntu.com/questions/626078/mouse-cursor-invisible-after-15-04-update](http://askubuntu.com/questions/626078/mouse-cursor-invisible-after-15-04-update)

Maybe one of the other options might work?  Not sure though as Xubuntu 15.10 doesn't seem to have this bug.

---

### Post by streak3 on 2015-11-22
Thx .. I did try these.. wasn't able to find the magic key :)

---

