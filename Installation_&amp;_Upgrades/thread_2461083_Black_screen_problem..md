---
title: "Black screen problem."
date: 2021-04-24
forum: Installation &amp; Upgrades
---

### Post by jijijsdar on 2021-04-24
there is black screen and not continue .
so i did sooooo many things . 
update etc

[LIST=1]
[*]sudo apt-get update
[*]sudo apt-get upgrade
[*]sudo ubuntu-drivers autoinstall
[/LIST]
 after that it work. but only once.
i have to do write this thing everytime.

just my guess there is matter of this 


sudo ubuntu-drivers autoinstall

No drivers found for installation.


and 


 lspci -k|grep -iEA5 'vga|3d'

07:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso (rev c9)
    Subsystem: ASUSTeK Computer Inc. Picasso
    Kernel modules: amdgpu
07:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Raven/Raven2/Fenghuang HDMI/DP Audio Controller
    Subsystem: ASUSTeK Computer Inc. PRIME B450M-A Motherboard
    Kernel driver in use: snd_hda_intel

i went that site and tried download that driver but only window. and i found many information but no work at all.

thanks for read.

---

