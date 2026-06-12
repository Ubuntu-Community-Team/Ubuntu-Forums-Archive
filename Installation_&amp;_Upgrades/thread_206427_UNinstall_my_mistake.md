---
title: "UNinstall my mistake"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by thepocketdrummer on 2006-06-30
Ok, I got the file from Nvidia and tried the instructions I was given to install them a while ago, only i used the gcc-4.0 instead of gcc-3.4
After I rebooted it said that it was installed incorrectly forcing me to use vesa to get back into the desktop.

Also, when I installed using synaptic, it was still set to vesa and not nvidia.

These are the steps I took to install the drivers...

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc-4.0
sudo apt-get remove --purge nvidia*
sudo /etc/init.d/gdm stop
sudo -s
export CC=gcc-4.0
sh NVIDIA
```
Hit tab for the rest to pop up. Went through the installation.
```
sudo reboot
```

After that it reboots, the screen is all jacked up, and I have to go back to vesa. From here, how do I uninstall these drivers. Or, better yet... how do I make these drivers actually WORK?

PLEASE help #-o

---

### Post by woedend on 2006-06-30
sudo sh NV* --uninstall  
will uninstall the nvidia drivers you built
installing from synaptic will not automatically change xorg.conf
use sudo gedit /etc/X11/xorg.conf  and set the driver to nvidia.  If all else fails use tseliots script.

---

### Post by thepocketdrummer on 2006-06-30
When I install nvidia-glx, it also installs the linux image 2.6.15.23. But I already have linux image 2.6.15.25. Does that mean I have to use an older version to use the drivers? Can I still use them if I go into 2.6.15.25?

I'm confused.

---

### Post by thepocketdrummer on 2006-06-30
Ok, I uninstalled the other drivers, reinstalled the one's you suggested, changed vesa to nvidia, rebooted... X server failed. Had to switch it back :_(

Any suggestions?

---

### Post by tseliot on 2006-06-30
[QUOTE=thepocketdrummer]Ok, I uninstalled the other drivers, reinstalled the one's you suggested, changed vesa to nvidia, rebooted... X server failed. Had to switch it back :_(

Any suggestions?[/QUOTE]
Please, follow Method 1 of my guide:
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)

---

### Post by thepocketdrummer on 2006-06-30
Call me stupid... but which is the Athlon 64? I'm using the 32-bit ubuntu... do I get K7, 386, or 686?

---

### Post by tseliot on 2006-06-30
[QUOTE=thepocketdrummer]Call me stupid... but which is the Athlon 64? I'm using the 32-bit ubuntu... do I get K7, 386, or 686?[/QUOTE]
K7

---

