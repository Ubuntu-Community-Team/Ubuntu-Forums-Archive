---
title: "screen is blank, help!"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by tehsyco on 2005-08-12
When my laptop goes into xorg after booting up, screen is completely black. I've tried control+alt+f1 and control+alt+backspace and those don't seem to work. 

I'm using a brand new Dell Inspiron 6000, help!


*sobs* I was so close to getting everything working and then it blanked out on me ;/

---

### Post by tehsyco on 2005-08-12
I was told to go into recovery mode and try to fix xorg so that's what I'm doing now. I have no idea what could be wrong though...any help would be appreciated - I'm looking at the xorg config.

---

### Post by kenyi on 2005-08-14
I had the same issue, I temporary fixed it by changing the /etc/X11/xorg.conf file. Just search for i810 and replace it with vesa.

This should be a temporary fix until I can find out why is i810 driver failing. Changing permanently to vesa shoud not be a good idea

Other users had fixed it by switching their BIOS to A05. I haven't test it though...

good luck!!

Kenyi

---

