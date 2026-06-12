---
title: "'You are not authorised to perform this action&quot;"
date: 2010-01-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tchoklat on 2010-01-04
I have upgraded Karmic to the latest testing distro Lucid with the command; "do-release-upgrade -d". Upgrade went fine. Upon restarting I get an error message that the system will be started in low graphics mode - that is OK. 

I now enabled 3rd party repos disabled by Lucid installer and ran ...update etc and noted an NVidia driver was upgraded.

I start System > Administration> Hardware Drivers and get four options for my NVidia card and select the recommended one only to be greeted with this error; "You are not authorised to perform this action".

Apart from the low res graphics mode using the standard graphics driver all is fine. Any thoughts out there?

tchoklat

---

### Post by wilee-nilee on 2010-01-04
Lucid seems to miss my graphics card about half the time, a restart fixes it. I would do a restart and see if it goes normal then try the graphics driver, I don't think it will upgrade in low graphics possibly.

---

### Post by Belizeian on 2010-01-04
did you try to sudo the nivida driver? could be a permisons issue as to who can execute it.

hit alt f2 and 


type in 
gksu /usr/bin/nvidia-settings

---

### Post by tchoklat on 2010-01-04
Did this and I get to the NVia settings screen with this error; "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server". To which I then get:

tony@tony-desktop:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found

If I try;

tony@tony-desktop:~$ nvidia-xconfig
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-glx-173
 * nvidia-glx-185
 * nvidia-glx-96
Try: sudo apt-get install <selected package>
 ... and then try to install the nvidia-glx-185 binary drivers, synaptic tries to remove X-Org and all the Xserver-Xorg files ?!?

tchoklat

---

### Post by tad1073 on 2010-01-04
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

add that ppa to your sources.list update and try the hardware drivers again.

---

### Post by tchoklat on 2010-01-04
did this, then apt-get update/upgrade installed software, though I am still getting the same message ....

---

### Post by tad1073 on 2010-01-04
try alt+f2 then type in:
```
gksu /usr/bin/jockey-gtk
```

---

### Post by tchoklat on 2010-01-04
> **tad1073 said:**
> try alt+f2 then type in:
```
gksu /usr/bin/jockey-gtk
```
did it. Thanks :p

---

