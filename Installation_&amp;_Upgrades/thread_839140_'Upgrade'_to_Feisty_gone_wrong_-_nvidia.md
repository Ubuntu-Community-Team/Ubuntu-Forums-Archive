---
title: "'Upgrade' to Feisty gone wrong - nvidia"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by The Brain on 2008-06-24
Clicked the Synaptic upgrade from 7.04 to 7.10. Feisty come up OK when I rebooted post-install. Installed the restricted modules to get my wireless NIC working. I rebooted and now X doesn't work - just seems to hang on a blank screen but the gdm comes up perfectly. 

Envy didn't work for me. 
Installed NVIDIA's drivers from the website. Get prompted to adjust video settings...looks promising...then get the blank screen hang again. Xorg.conf settings are fine. 
Blew away the restricted modules..no luck.

Where to from here ? Like an idiot I have everything in / and didn't create a home directory. Do I use gparted live CD to resize the partitions, then install 7.10 from CD ?

---

### Post by Pumalite on 2008-06-24
Do you have build-essential installed? What commands did you use to install the driver?

---

### Post by The Brain on 2008-06-24
Yes, I have build-essential installed.

Installing the driver was just 'sh NVIDIA-Linux-x86-169.12-pkg1.run' and following the standard prompts. Didn't report any errors during the build. Its a GeForce 8600 video card. 

I'm able to get X working OK if I boot into recovery mode.

---

### Post by Pumalite on 2008-06-24
Did you do it through a Virtual Terminal? Did you let it reconfigure your xorg.con file?

---

### Post by The Brain on 2008-06-24
Yes I did. And checked the xorg.conf settings and there's nothing that sticks out as being wrong. I don't get fuzziness or the image shaking when gdm logs in..just never comes up with the Panels etc..

Wonder if there's any way to compare or run a diff on the normal X settings and the recovery mode settings..

---

