---
title: "xserver wont work"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by dethzeppelinx on 2007-10-11
I have installed ubutnu and it says that the x thing doesnt work and the graphical interface wont start. I have a nvidia 8600 gs do i need a certain driver or something for it this is verry frusterating.

---

### Post by Pumalite on 2007-10-11
Try booting in Safe Graphics Mode and run
sudo apt get install nvidia-glx-new, then
sudo /etc/init.d/gdm stop
Then try to boot in normal option

---

