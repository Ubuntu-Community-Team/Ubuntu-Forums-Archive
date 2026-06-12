---
title: "probs with installng ubuntu 6.06 on my frndz PC"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by yasasvy on 2007-02-05
1.hi.. well i have started usign ubuntu 3 months back.. liked it so much that i recommended all my frndz to install this.. i even ordered cd's for them.. my prob is that my palz system isnt supporting the live cd.. it simply hangs(even the mouse pointer isnt working) so.. couldnt install.. his PC confic is similar to mine.. got really confused. any solutions?
P IV 2.8 Ghz, 512 MB RAM, INTEL 845 chipset.


2.and in one more occasion( a diff frnd) the live cd works fine but it isnt supporting resolution greater than 640*480. when i tried to change the screen resolution it shows only one option of 640*480. soo wht shall i do!!, shall i proceed with installing ubuntu?

---

### Post by an.echte.trilingue on 2007-02-05
In the first case, don't know exactly.  What is his/her video card?  Do you get any error message? which version of Ubuntu?

In the second case, reconfigure the display with 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then restart the display with CTRL+ALT+Backspace.  I would do this after the install, personally.

Take care
-mat

---

### Post by yasasvy on 2007-02-05
hmm.. thnx for that.. and BTW he dosent have an external video card! he just has the default one inbuilt with the mother board. .. shall i try the alternate CD?? if yes where can i get it?

---

### Post by yasasvy on 2007-02-05
ohh the version is drapper drake (6.06)

---

