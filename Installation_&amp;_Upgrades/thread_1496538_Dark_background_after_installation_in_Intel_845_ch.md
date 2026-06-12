---
title: "Dark background after installation in Intel 845 chipset"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by cupid on 2010-05-29
Hello everybody,
My machine is an Intel 845 chipset family with a P4 2.66Ghz. Processor with 1024Mb RAM. 
I installed Ubuntu 8.10, 8.04 . After complete installation when my PC rebooted I got a logon screen that worked, but only got a dark background and a mouse pointer. The mouse pointer was functional, but no menu items or icons were present.

Is it a graphics related issue ? How can i resolve it ?
Or is it not possible to install both the above ubuntu version or hiher version on my above mentioned PC configuration ?

---

### Post by jerrrys on 2010-05-29
804 is still supported.  did you run the live cd without installing to be sure it worked?

---

### Post by cupid on 2010-05-29
> **jerrrys said:**
> 804 is still supported.  did you run the live cd without installing to be sure it worked?

No i didnt !
But i need a clean complete installation !

---

### Post by davidmohammed on 2010-05-29
10.04 is the new LTS.  Give the livecd with that version a try.  What graphics chip set do you have - if its a i8xxx then don't use the lts.  Suggest stick to karmic 9.10.

---

### Post by cupid on 2010-05-29
> **davidmohammed said:**
> 10.04 is the new LTS.  Give the livecd with that version a try.  What graphics chip set do you have - if its a i8xxx then don't use the lts.  Suggest stick to karmic 9.10.

Even 9.10 is also not running properly !
dark background with a  mouse pointer is what it appears to be after the installation !!!
How to check what graphics chip i have ?

---

### Post by cupid on 2010-05-30
I again did a clean install of 8.04 and fortunately 8.04is  working well .
But the problem still remains with later versions ....
still searching for solutions !
If any body would like to suggest feel free ! 
  :)

---

### Post by davidmohammed on 2010-05-31
> **cupid said:**
> 
How to check what graphics chip i have ?

from a terminal type

lspci | grep VGA

if you have an early intel (i8xxx) you will need to boot with

i915.modeset=1

or 

i915.modeset=0 in your grub 

if you have other graphics chips you might want to try

nomodeset
(press shift on boot to display grub followed by e to edit.  Add the above before "quiet splash")

---

