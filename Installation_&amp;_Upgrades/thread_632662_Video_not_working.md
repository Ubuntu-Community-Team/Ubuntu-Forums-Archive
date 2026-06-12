---
title: "Video not working"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by jayman7227 on 2007-12-05
I am trying to install Ubuntu on my computer and when I run the live CD the video never displays.

I have a Dell Inspiron 531 with an integrated NVIDIA GeForce 6150 SE video card.

Is it just a lack of driver support, what can I do to get it to install.

Thanks for your help.

---

### Post by Pumalite on 2007-12-05
Try the Alternate CD.

---

### Post by Thanoulis on 2007-12-05
I myself have the plain NVIDIA 6150 and the video output worked like a charm (3D graphics,etc). Maybe it is your LCD monitor. Especially if it is a wide one. Try to install from an alternate CD, and after installation, modify your xorg.conf (located at /etc/X11/) with HorizSync and VertRefresh options (the exact values vary from lcd to lcd...though).
That way the Xserver will know what screen resolution your monitor may have.

---

### Post by jayman7227 on 2007-12-06
Thank you both Thanoulis and Pumalite.

I installed use the alternate cd, and the monitor still was not working.  I booted into recovery mode and edited the xorg.conf file.  I had to update the file to reflect my monitors specs and bada bing bada boom SUCCESS!!!!

The help was much appreciated.

:)

---

