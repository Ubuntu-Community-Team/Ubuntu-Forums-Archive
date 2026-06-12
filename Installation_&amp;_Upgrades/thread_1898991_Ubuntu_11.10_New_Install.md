---
title: "Ubuntu 11.10 New Install"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by blksilver on 2011-12-22
I just installed Ubuntu 11.10 and after I login I get a blank pink screen.

---

### Post by BC59 on 2011-12-22
So do you reach the Grub menu?

---

### Post by blksilver on 2011-12-22
no just a pink screen after i log in under my name on the main page of ubuntu

---

### Post by Basher101 on 2011-12-22
maybe a video driver issue? what graphics card do you have

---

### Post by blksilver on 2011-12-22
not sure, I was running ubuntu 9.10 and it was ok

---

### Post by BC59 on 2011-12-22
Try this
Boot and press SHIFT key after the bios to get the grub menu
Select the default ubuntu kernel, and not press enter but press E to edit.
Go down until the line that starts with

**linux /boot** and to the end of "quiet splash&#8221; change it to "quiet splash nomodeset&#8221;.

then press CTRL+X to boot

---

