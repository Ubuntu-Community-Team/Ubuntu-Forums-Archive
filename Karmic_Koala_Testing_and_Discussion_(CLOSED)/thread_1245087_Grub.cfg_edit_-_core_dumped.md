---
title: "Grub.cfg edit - core dumped"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-08-20
I have a number of versions of Ubuntu on my PC. When I boot the PC it now shows 
```
Ubuntu 9.04 (9.04) on /dev/sda7
```
(for example) as one of my options. When I select this it boots kernel 2.6.28-14 and not 2.6.28-15 as expected (I know this is installed as it appears in the /boot directory on sda7). I'm able to view grub.cfg but as soon as I try to opened it with gedit I get 
```
Segmentation fault (core dumped)
```
even though I've enabled write privileges with
```
sudo chmod 644 /boot/grub/grub.cfg
```
I've done a grub-update and that makes no difference.  It seems the grub.cfg file is in a mess (see attached) as I've only installed desktop versions of Ubuntu and Kubuntu.  I've also tried generating an 07_custom file to try to resolve the displayed list at bootup but again I get a segmentation fault.

[EDIT] I've just found that the list is in reverse order as the -15 kernel is the second instance of 
```
Ubuntu 9.04 (9.04) on /dev/sda7
``` and all kernels listed are shown as oldest first for each OS (as per grub.cfg file).

---

### Post by xebian on 2009-08-20
> **Kevbert said:**
> I have a number of versions of Ubuntu on my PC. When I boot the PC it now shows 
```
Ubuntu 9.04 (9.04) on /dev/sda7
```
(for example) as one of my options. When I select this it boots kernel 2.6.28-14 and not 2.6.28-15 as expected (I know this is installed as it appears in the /boot directory on sda7). I'm able to view grub.cfg but as soon as I try to opened it with gedit I get 
```
Segmentation fault (core dumped)
```
even though I've enabled write privileges with
```
sudo chmod 644 /boot/grub/grub.cfg
```
I've done a grub-update and that makes no difference.  It seems the grub.cfg file is in a mess (see attached) as I've only installed desktop versions of Ubuntu and Kubuntu.  I've also tried generating an 07_custom file to try to resolve the displayed list at bootup but again I get a segmentation fault.

[EDIT] I've just found that the list is in reverse order as the -15 kernel is the second instance of 
```
Ubuntu 9.04 (9.04) on /dev/sda7
``` and all kernels listed are shown as oldest first for each OS (as per grub.cfg file).
While in the grub menu, you can see the details by selecting it and then press e (for edit).  Press escape when done, or while editing Ctl + x to boot.  There are helpful hints at the bottom while editing.

---

### Post by Darkshade on 2009-08-20
I think the segfault has nothing to do with the grub.cfg file. Gedit segfaults on my system almost every time I try to open something. Try opening gedit with sudo and then open the file from the gedit "Open" menu.

You can also try sudo update-grub.

---

### Post by ranch hand on 2009-08-20
I love gedit but have been using screem in 9.10 because it works.

---

### Post by Kevbert on 2009-08-20
Thanks for the commands xebian.
Gedit should not segfault - it works fine in Ubuntu 9.04, 8.10, 8.04.

---

### Post by Darkshade on 2009-08-20
> **Kevbert said:**
> Gedit should not segfault - it works fine in Ubuntu 9.04, 8.10, 8.04.

Welcome to Karmic Alpha :lolflag:

---

### Post by VMC on 2009-08-20
I have same problem opening files by double-click. gedit opens then closes. I have to open gedit first then drag file into gedit.

---

### Post by sparker256 on 2009-08-21
> **VMC said:**
> I have same problem opening files by double-click. gedit opens then closes. I have to open gedit first then drag file into gedit.
I also have the same problem when double clicking. I just got done reinstalling alpha4 from cd and will see if any better. It is very annoying when trying to write some code and it opens and closes on you. Yes I know only for testing so I go back to my 9.04 partition to work.

Bill

---

### Post by ranch hand on 2009-08-21
This is a known bug don't havethe number handy.

Report it.

---

