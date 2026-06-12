---
title: "Intel 82865G chipset: black screen during installation"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Waterboy5281 on 2010-06-29
I have spent the better part of 2 days perusing these forums for assistance. Here is the short story:

I run a 7 year old custom build with a 82865G Intel Chipset and a NVIDIA FX5200 graphics card. Had been running a sluggish XP and after adding 2GB of fresh RAM wished to start fresh with my old friend, Ubuntu. 

I've tried 10.04 LTS with and without my NVIDIA card installed with no luck. I have successfully installed 10.04 using the alternate install, but this also goes to black. I can hold shift to see GRUB and play around there, but no luck so far.

I've also tried 9.10 but have not gotten past the pulsing Ubuntu image.

I've seen plenty of support for NVDIA and Intel onboard graphics chips suggesting boot commands like nomodeset and i9015.modeset=0/1...it's all falling short.

I'm heavily leaning towards just installing an earlier LTS or a different linux distro all together. If there no one can help me debug, maybe someone can suggest a distro that will make me happy.

I appreciate this forum's support in advance.

---

### Post by Waterboy5281 on 2010-07-01
I realize there are plenty of threads discussing similar issues, but I haven't been able to replicate anyone else's success. Is anyone else out there with experience with this chip?

---

### Post by Waterboy5281 on 2010-08-25
Help, anyone?

---

### Post by GenBattle on 2010-08-25
I suggest you try the solutions from the similar threads, here is what i would suggest you do:
[http://ubuntuforums.org/showpost.php?p=9766336&postcount=8](http://ubuntuforums.org/showpost.php?p=9766336&postcount=8)

Edit the grub entires, try the different options i have outlined. At least if you remove the splash and quiet options you will get a little more information about why/where it is crapping out.

---

### Post by Maverick_Meerkat on 2010-08-25
Try using the esc key to boot into safe graphics mode to install. That worked with my intel chipset.

---

