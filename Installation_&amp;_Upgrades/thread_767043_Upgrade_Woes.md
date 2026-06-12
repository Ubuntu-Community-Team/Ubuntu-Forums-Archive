---
title: "Upgrade Woes"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Pord on 2008-04-25
Ive done the upgrade from 7.10 to 8.04 and all seemed to be fine. Now the problem came when I tried to run a program wanting 3d acceleration. It crashed and now I cannot boot properly at all. Everytime the x server tried to load it seems to freeze. The mouse can be moved but nothing loads at all and busy icon is on all the time. 
I tried with and without the proprietry drivers for ati (fglrx) and tried from the ati site and one using apt-get.
I looked in the xorg file and it doesnt show much anymore about what sort of graphics card it is in the device section as it shows 

Section "Device"
Identifier "Configured Video Device"
EndSection

Ive tried to boot the live cd and it does the same after the intro music plays on the boot and I cannot do anything again.

So I cannot use the opensource or proprietry for ati cards. I was able to boot into a low resolution VESA xorg but this meant I could only use a low resolution and then it would not pick up my graphics card properly when I tried to make a new xorg.

My graphics card is an ATI Mobility 9700. Can any1 help?

---

### Post by Pumalite on 2008-04-25
Try Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

