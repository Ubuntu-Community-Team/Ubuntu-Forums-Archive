---
title: "No CD, Floppy or USB... Dell C400"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by Mikey_MW on 2008-07-14
I'd like to reinstall Ubuntu on my Dell Latitude C400 but there is a slight problem. It doesn't have a bootable cd rom, floppy drive or usb. I remember using Instlux when I first did it, but it seems that program is openSUSE exclusive now. 

I do have a second laptop (Toshiba Tecra 8000) which does boot from CD. Is it possible to install Ubuntu to that, then pop the hard drive back into my Dell? I wonder because I've tried it with other OS's and it seems to be a hit and miss.

It currently has Win98SE installed.

Note - I looked at buying a CD ROM for this model but the one I've seen doesn't look like it would fit anywhere on my laptop, especially since it is smaller than a cd rom in height.

---

### Post by overdrank on 2008-07-14
> **Mikey_MW said:**
> I'd like to reinstall Ubuntu on my Dell Latitude C400 but there is a slight problem. It doesn't have a bootable cd rom, floppy drive or usb. I remember using Instlux when I first did it, but it seems that program is openSUSE exclusive now. 

I do have a second laptop (Toshiba Tecra 8000) which does boot from CD. Is it possible to install Ubuntu to that, then pop the hard drive back into my Dell? I wonder because I've tried it with other OS's and it seems to be a hit and miss.

It currently has Win98SE installed.

Note - I looked at buying a CD ROM for this model but the one I've seen doesn't look like it would fit anywhere on my laptop, especially since it is smaller than a cd rom in height.
HI and maybe Wubi
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
or 
[https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

---

### Post by Mikey_MW on 2008-07-14
Thanks, you're a life saver :) I'd rather not have Windows at all (as it was, I only installed it to wipe out an ubuntu that had been broken beyond repair by kids) so Wubi is out, but I think this should do it.

---

### Post by SR_ELPIRATA on 2009-04-20
Mike:

I've swapped drives between Dell laptops (using ubuntu 8.10 btw) and other manufacturers and as long as you dont install anything special (like ati or nvidia drivers).. once you put the drive back to your laptop should work, at least on my tests so far and with all IDE 2.5" drives.

This is also true with desktops, I've changed drives from Dell PCs and clones with AMD processors and it just tells you that the display is not the same, it gives you the option to reset the display to defaults, then restarts the x server and you're set.

I'm going to read those links that overdrank provided you as I have a situation with a Latitude X1, in this case the HDD is a 1.8" version, which I dont have in any other laptop I have around. The X1 also has no CD, its got USB but at the moment I dont have pendrives lying around that I can use (the ones I have contain critical data).

ELP

---

