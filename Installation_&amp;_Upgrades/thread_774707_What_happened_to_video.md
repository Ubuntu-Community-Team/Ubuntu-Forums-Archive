---
title: "What happened to video?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by daemon3 on 2008-04-29
Video (NVidia Geforce driver) worked just fine in Gutsy Gibbon.  I had nice 3D effects and 3D games without much problem.  However, with the recent Hardy Heron upgrade, I don't have my 3D support.  What went wrong?  I tried to reinstall the NVidia new drivers with aptitude, but it didn't help. :(
Hardy's great, but I'm starting to regret my upgrade.
Thanks in advance.

---

### Post by Pumalite on 2008-04-29
What are you confronted with? A blank screen? Bad graphics?

---

### Post by daemon3 on 2008-04-29
The desktop can function just fine, but Compiz can't be enabled, and cool 3D games are out of the question.

---

### Post by Pumalite on 2008-04-29
System>Preferences>Appearance>Visual Effects>Enable

---

### Post by daemon3 on 2008-04-29
That's the problem.  I already tried doing that, but Compiz CANNOT be enabled.  It's a problem with the video driver.

---

### Post by Pumalite on 2008-04-29
What driver did you install and how did you install it?

---

### Post by daemon3 on 2008-04-29
nvidia-xgl-new.  I used aptitude in order to install it.  I think I see where this is going...I may have to configure the X server, right? :(

---

### Post by Shazzner on 2008-04-29
Welcome to Linux Video Driver Hell!

---

### Post by chek2fire on 2008-04-29
Download envyng from synaptic and try to install the drivers with this programme.

---

### Post by Pumalite on 2008-04-29
Post:
cat /etc/X11/xorg.conf

---

### Post by daemon3 on 2008-04-29
How do I find out the exact make and model of my video card?  I need it for envyng

---

### Post by daemon3 on 2008-04-29
How do I find out my video driver make and model?  I need it for envyng.  I tried lspci, but that didn't work.

---

### Post by daemon3 on 2008-05-02
Never mind.  My problem was that I didn't let the upgrade finish.  Now it works fine.

---

