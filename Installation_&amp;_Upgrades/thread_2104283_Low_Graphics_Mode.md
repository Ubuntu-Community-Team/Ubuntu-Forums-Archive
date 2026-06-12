---
title: "Low Graphics Mode"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by ajdrew06 on 2013-01-12
Hello all, I cannot boot my laptop. It keeps ATTEMPTING to boot in Low Graphics Mode. I have tried the following:

1) Selecting the option to boot in low graphics mode this one time. However, it goes to the screen the purple "ubuntu" screen with the five dots that rotate from orange to white & vice-versa. However, it gets stuck in an infinite loop. It does not ever reach the log-in screen.

2) I've tried "sudo apt-get install flgrx" in the ctrl+alt+F1 terminal. When I boot, it does not give me the low graphics mode error; however, it goes into the same infinte loop as mentioned above. (I purged flgrx because it wasn't working & that's how my machine is now).

3) I've gone into Recovery Mode from GRUB & tried to boot in failsafexinit mode. However, when I say "yes" to "do you want to continue" something about remounting, it gets hung up & doesn't boot.

I'm not sure of the exact model number of my ATI Radeon video card. I believe it is the 6600. I am running Ubuntu 12.04.

I have not messed with anything in the video drivers prior to this morning. I was prompted to install updates this morning; I rebooted per the installation request, and my computer would not boot properly.

Any ideas??

Please advise!!! Than you!!

---

### Post by ranger1021994 on 2013-01-12
Try this :
Press Ctrl+Alt+F1 after you boot in,login the system and :
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri

sudo dpkg-reconfigure xserver-xorg
sudo reboot
```

---

### Post by ajdrew06 on 2013-01-12
Thank you for your reply. However, the first line of code generates the following error:

sh: 0 Can't open /usr/share/ati/fglrx-uninstall.sh =(

---

### Post by ajdrew06 on 2013-01-12
> **ranger1021994 said:**
> Try this :
Press Ctrl+Alt+F1 after you boot in,login the system and :
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri

sudo dpkg-reconfigure xserver-xorg
sudo reboot
```

I did the above. I already purged fglrx, so the first 3 steps gave errors saying "cannot remove, not installed".

However, I still get the low graphics mode error.

---

### Post by ranger1021994 on 2013-01-12
Ignore the errors related to purging and proceed to next steps and problem should be solved
This happened with me.I followed these steps to get out of Low Graphics Mode.

---

