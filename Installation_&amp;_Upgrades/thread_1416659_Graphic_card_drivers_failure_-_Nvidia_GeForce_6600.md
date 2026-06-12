---
title: "Graphic card drivers failure? - Nvidia GeForce 6600GT"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by MikeHunt on 2010-02-26
What am I doing wrong?:

1. Install ubuntu (on integrated graphics, when I try to use GF the only thing I see are black and white vertical stripes), system works normally
2. Reboot and install nvidia drivers
3. Another reboot, switch to GF (through bios)
4. Result: stripes.
And yes, xorg is correctly configured (using nvidia instead of vesa), manual congif gives the same result.

In other words nvidia drivers doesn't work with nvidia graphic card. No idea why.



*Sorry for my english and (hopefully not) wrong subforum ;)*

---

### Post by Kevbert on 2010-02-26
Welcome to Ubuntu.
Have you tried installing the driver via System-Administration-Restricted Drivers ?
You may need to run
```
sudo apt-get update
```
via Applications-Accessories-Terminal first in order to see the available drivers.

---

### Post by cascade9 on 2010-02-26
If you get the boot screen, etc (not the ubuntu boot screen, the initial boot screen) is displaying normally, then you might have an software issue. If the boot screen  is 'striped' (ie. you never get a 'normal' display) then you've got a totally different issue......your video card is dead.

---

### Post by MikeHunt on 2010-02-26
@Kevbert
yup. same effect (tried terminal (apt-get and manual download), synaptics, restricted drivers, envy).

@cascade9
It crashes after grub, when loading system but card isn't dead. I'm currently on W7 and it works normally, games too.

linux mint, xubuntu, kubuntu - same. Why it works on windows and doesn't work on *buntu?

---

### Post by Kevbert on 2010-02-26
Found [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1390813"). See post #2.
[[COLOR="Red"]One other solution[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1328549") seems to replace the BIOS on the graphics card.

---

### Post by MikeHunt on 2010-02-26
#1 nope. stripes. or white screen.
#2 no information about bios. but i found something interesting in log:
> (...)
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: _**PCI 00@00:02:0**_
(EE) No devices detected.

Fatal server error:
no screens found

Please consult (...)00:02:0 is my DISABLED integrated vid. card, not 6600. So: how can i force it (reconfigure xorg) to use 6600?

---

### Post by Kevbert on 2010-02-27
See [[COLOR="Red"]post #3[/COLOR]]("http://www.linuxquestions.org/questions/linux-hardware-18/disable-integrated-graphics-before-new-card-install-513665/"). It's a BIOS setting that needs to be changed (if available to turn off onboard graphics).

---

### Post by MikeHunt on 2010-02-27
still no change. integrated turned off, agi as default/primary.

---

