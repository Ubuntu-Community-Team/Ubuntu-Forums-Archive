---
title: "keyboard does't work in lucid beta 2"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mahdif62 on 2010-04-15
I did a fresh install of lucid beta 2 and the keyboard doesn't work in GDM login screen. The on-screen keyboard also crashes immediately. I googled the problem and the only solution that was suggested was to remove "mouseemu" package. However when I chrooted into lucid from karmic I noticed that no mouseemu package is installed. Please help me because my system is now unusable.

---

### Post by mahdif62 on 2010-04-15
I solved the problem by booting into recovery mode and typing:
sudo dpkg-reconfigure console setup
This time I selected US region and keyboard. Last time I had selected Iran region and keyboard layout. Seems like a bug.
[https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/513932](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/513932)

---

### Post by bapoumba on 2010-04-15
Moved to Lucid

---

