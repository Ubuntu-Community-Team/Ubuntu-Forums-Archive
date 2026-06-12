---
title: "Latest kernel image and headers upgrade issues..."
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by Jose Catre-Vandis on 2006-12-17
The latest batch of kernel headers and image upgrades (still 2.6.15.27 though) had a couple of impacts on my systems.

dvb tv

For my card to work I have to install the latest v4l-dvb set from linuxtv.org. The ubuntu updates appeared to have killed by dvb tv I could get no connection or reception when scanning. So reinstalled the latest v4l-dvb kernel set as before and dvb-tv back up and running again

grub

After these upgrades I rebooted and received boot errors from grub (15 and 22 on two different machines). On the first machine grub had clearly done some updating and moved my main boot linux from hd0,6 to hd0,11 (hda7 to hda12). Oddly i do not have an hd0,11/hda12, although have had in the past) Needed to edit the grub menu.lst to get the thing with the right settings again. The second machine was a bit wierder. Two entries in grub, with exactly the same settings: hd0,0/hda1, but one with saveasdefault in the list would not boot whilst the other would.

vmware server survived this upgrade :)

---

