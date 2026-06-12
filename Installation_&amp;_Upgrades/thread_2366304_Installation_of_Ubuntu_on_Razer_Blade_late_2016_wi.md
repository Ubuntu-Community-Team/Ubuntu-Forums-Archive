---
title: "Installation of Ubuntu on Razer Blade late 2016 with GTX 1060 freezes upon login"
date: 2017-07-16
forum: Installation &amp; Upgrades
---

### Post by spohnicus on 2017-07-16
Title is as descriptive as I can be. It says it all.

Edit 1: after I log in, the display manager for logging in disappears and freezes instantly after that.

---

### Post by ajgreeny on 2017-07-16
What version of Xubuntu (or perhaps it's Ubuntu with added xfce-4.12?) are you using and what video driver do you have?

You may need to boot with the nomodeset option for that nvidia card but we need more info to help you properly.

---

### Post by efflandt on 2017-07-16
You did not say which Ubuntu version. It is possible that the default nouveau graphics driver might not support the mobile GTX 1060 yet. I was going to suggest booting recovery mode (which automatically uses nomodeset), enable networking (which also remounts partitions from read-only to read-write), and then back at menu go to root console add the graphics-drivers ppa and install nvidia-381 or nvidia-384 package. I think I had to do something similar for my desktop GTX 1060, but maybe nvidia-375 at that time.

But that is easiest if you could temporarily connect Ethernet which that laptop does not appear to have, and it has been a long time since I configured WiFi from a terminal. So even if you could boot normally and at the login gui switch to a text terminal with Ctrl+Alt-F1, you would still need to be able to manually configure WiFi unless you did that in the live/install system before installing and those settings carried over to the installed system.

But if one way or another you could get to a text terminal on the installed system with working WiFi you could do this:```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-384
sudo reboot
```[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Spec's for that laptop do not mention if it has hybrid Intel/Nvidia graphics or Nvidia graphics only, but if it does have hybrid graphics, once Nvidia drivers are installed, you can switch which graphics is used from NVIDIA X Server Settings (you may need to log out of X and back in, or maybe reboot).

---

### Post by BenginM on 2017-07-17
> **spohnicus said:**
> Title is as descriptive as I can be. It says it all.

Edit 1: after I log in, the display manager for logging in disappears and freezes instantly after that.

Salutations!

Actually that doesn't say much! .. you need to read the logs and see why it freezes! , beside.. if you disable the GTX in the BIOS and use the integrated built-in Inte HD Graphics 630 , i doubt you'll have the same issue or any issue at all! if that's the case then the fault is the nvidia proprietary driver or maybe you need to blacklist the nouveau free driver!

welcome to the forums!

---

