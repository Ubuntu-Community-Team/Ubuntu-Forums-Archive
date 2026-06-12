---
title: "Installed kubuntu 17.04, now boots to black screen"
date: 2017-09-05
forum: Installation &amp; Upgrades
---

### Post by kendall316 on 2017-09-05
So basically I had multiple os's on my laptop. Kubuntu 17.04, windows 10, elementary, and deepin. Decided to clear things out and put in my same install CD of kubuntu. I chose to use the whole HD and it installed on my computer. Prompted me to restart and now after I get the Asus logo, then kubuntu, then it just goes to a dark purplish/ black screen. Putting the CD back in doesn't do anything, nor my CDs I had for the other OS's. Any ideas how to fix it since now I have no working computer? Thank you I really appreciate it.

---

### Post by ubfan1 on 2017-09-05
Do you have any proprietary video hardware, like Nvidia?  Can you force grub to display by holding down the shift (or maybe tab?) key at boot up, and then you can edit the grub boot command (type e,... instructions at bottom of screen) to add the word "nomodeset" at the "quiet splash" location on the  linux boot line.  Can you switch to a virtual terminal with ctrl-alt F3  (function keys 1-6) should be virtual terminals, f7 is the gui login.

---

