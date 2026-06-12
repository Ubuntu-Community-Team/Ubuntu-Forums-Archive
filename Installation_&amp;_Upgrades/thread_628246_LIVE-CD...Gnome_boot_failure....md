---
title: "LIVE-CD...Gnome boot failure..."
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by ghstwalker on 2007-12-01
My live-cd is failing to boot into gui... I press CTL+ALT+F1 and get my terminal... I have used commands i found searching the forums such as 
> startx

I also copied /etc/X11/xorg.conf /etc/X11/xorgold.conf to backup 
and then edited the xorg.conf with some options under the monitor section 

none of this seems to work as i still get 
*Starting GNOME Display Manager...     [FAIL]

any ideals

oh, ASUS p5n32-sli deluxe
pentium e660
2x Geforce 7050gt in sli
2GB ram

---

### Post by Pumalite on 2007-12-01
Did you finished the install or are you unable to boot the Live CD?

---

### Post by ghstwalker on 2007-12-01
still on live cd...

---

### Post by Pumalite on 2007-12-01
Here is a tutorial and a collection of boot parameters you might want to try:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

If nothing works; go with the Alternate CD.

---

### Post by ghstwalker on 2007-12-01
doesnt the alternate cd just install linux? i don't see how an install of cd is going to boot normally if the live-cd wont boot correctly.

---

### Post by Pumalite on 2007-12-01
The Alternate CD was made for hardware problems that can be fix during or after the installation.

---

