---
title: "[SOLVED] upgrade from edgy to fiesty and no X server plus failure. yay!!!!!!!!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by rickycodie on 2007-04-20
so i just upgraded using the update manager,and now i have a failure, 
[   25.817199] pci: failed to allocate mem resource #6:20000@5000000 for 0000:01:00.0

then it looks for a resume image doesn't find one, then boots normally.

then comes the x server, it says it it failed to start. goes to text input.

help!!! i don't want to re-install!!

---

### Post by creamcheeze77 on 2007-04-20
i have this exact same problem, do you have a nvidia graphics card?

---

### Post by gstool on 2007-04-20
If you have an nvidia card and were using the nvidia driver, find a way to edit xorg.conf and change "nvidia" to "nv".

---

### Post by creamcheeze77 on 2007-04-21
if you go into the error report in X it says the nvidia kernel version and the X version don't match up, but i've installed the latest kernel version.  is there any way to get the newer one?

---

### Post by rickycodie on 2007-04-23
i went the easy way and used knoppix to back eerything up and then did a clean install. then i used automatix and installed the nvidia drivers and was fine.

---

