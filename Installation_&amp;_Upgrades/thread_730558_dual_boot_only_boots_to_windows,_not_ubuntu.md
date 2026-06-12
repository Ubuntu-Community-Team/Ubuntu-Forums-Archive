---
title: "dual boot only boots to windows, not ubuntu"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Frijole on 2008-03-21
I tried to dual boot ubuntu with my existing xp install and now it only boots to ubuntu.No sign of windows. Anyone know how to deal with this?

---

### Post by Existentialist on 2008-03-21
Does the windows install show up in the grub menu at boot?

---

### Post by Frijole on 2008-03-21
no, I looked at the GRUB list as well, and there is no listing for windows.

---

### Post by Existentialist on 2008-03-21
Alright, did you install xp or ubuntu first?  And what is the set up of your hard drives, which drive has which os, or are they on the same drive?  You could try running:

sudo update-grub

This might detect the windows os, and write it in to the grub menu.  If not, post back with the other information.

---

### Post by Frijole on 2008-03-24
I ended up re-installing Windows but this time I did not use the whole disk. I installed XP on the first 80GB of my 120GB drive. I would like to put Ubuntu on the rest of the disk. I heard that it is easiest to dual boot when the drive is partitioned when windows is loaded. Does anyone know the best way to finish setting up the dual boot?

---

### Post by Existentialist on 2008-03-25
Since you already have windows installed, you can boot from the Ubuntu cd and install ubuntu on the remaining 40gb of the drive.  Once installed, it should detect your windows install and give you a menu to select which os to boot.

---

