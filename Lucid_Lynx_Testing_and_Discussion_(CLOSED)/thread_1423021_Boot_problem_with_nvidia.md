---
title: "Boot problem with nvidia"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by usien on 2010-03-06
I have a Nvidia Geforce 7300 GT card and i can't boot lucid daily live build (5th march). Does anyone else have this problem?

---

### Post by _R2D2_ on 2010-03-06
Please describe your problem more exactly. What driver do you use? Is the problem stay active when booting in single user mode?

---

### Post by usien on 2010-03-06
I am talking about the live CD as of 5th March and i cannot boot to the desktop.

---

### Post by ntetreau on 2010-03-06
I had this problem as well and only found a walkaround.

Add xforcevesa to your boot options, then I CTRL-ALT-F2 to a console, edit the etc/X11/xorg.conf to replace vesa by nv. Optionnally, you can install install nvidia drivers on the LiveCD once booted using the System Hardwear Drivers utility which loads the latest nvidia-195x series.

---

