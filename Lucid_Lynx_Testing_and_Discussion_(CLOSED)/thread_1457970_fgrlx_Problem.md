---
title: "fgrlx Problem"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lanetherif on 2010-04-19
Most probably, I won't be saying anything new. However, being unexperienced, I need to make sure that my problem is the same as the whole bug reports I have seen around. 
In synaptics I keep getting this error: > E:fglrx: subprocess installed post-installation script returned error exit  status 10
E:fglrx-amdcccle: dependency problems - leaving unconfigured
E: fglrx-kernel-source: dependency problems - leaving unconfigured
E: xorg-driver-fglrx: dependency problems - leaving unconfigured
I followed instructions on [https://help.ubuntu.com/community/RadeonHD#Ubuntu%2010.04/Lucid ]("https://help.ubuntu.com/community/RadeonHD#Ubuntu%2010.04/Lucid")not that I know what they would do, but just to do something in order to solve problem. :) 

Does this problem persist on any machine and do I have to wait for an update or is there a solution? 
Thanks...

ps. I use an Ati Radeon HD4850...

---

### Post by dino99 on 2010-04-19
"dependency problems" its a known issue with Ati cards. 

into console: 

sudo gedit /etc/default/grub

Add nomodeset into /etc/default/grub  --> GRUB_CMDLINE_LINUX="nomodeset"

save and run update-grub then reboot

---

### Post by lanetherif on 2010-04-19
> **dino99 said:**
> "dependency problems" its a known issue with Ati cards. 

into console: 

sudo gedit /etc/default/grub

Add nomodeset into /etc/default/grub  --> GRUB_CMDLINE_LINUX="nomodeset"

save and run update-grub then reboot

I did. I tried it both with fglrx -tough not properly- installed and without it. In both cases my screen resolution was 1024x768 whereas without nomodeset it is 1080x1920 no matter fgrlx is installed or not. I got a pop up information that goes like Couldn't apply the stored configuration for the monitor. X Server does not support the size...
By the way, I don't if it matters, but I tried all those above mentioned both with 33.020633 and 32.21 kernels...

---

### Post by dino99 on 2010-04-19
if settings are corrupted, what it seems, 

remove/purge your video driver, comment all lines into xorg.conf, reinstall your video driver

then goto system -admin - hardware driver and check that driver is activated

reboot

---

### Post by lanetherif on 2010-04-19
> **dino99 said:**
> if settings are corrupted, what it seems, 

remove/purge your video driver, comment all lines into xorg.conf, reinstall your video driver

then goto system -admin - hardware driver and check that driver is activated

reboot

Thanks... I have somehow been able to make it work. :)

---

