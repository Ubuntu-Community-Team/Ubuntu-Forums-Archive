---
title: "boot disk"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by fredJones840 on 2006-11-17
so heres the dilemma .. ive got this old ibm 300pl computer that i was planning to install ubuntu ontu .. heh .. but its so old that the bios doesnt have the boot from cd option .. so what i need is a boot disk that can give the bios the option to boot from cd .. or does ne 1 have ne other better ideas on how to get this linux installed? with no cd boot option .. any ideas??

---

### Post by bernied on 2006-11-17
This is doable, you can chainload a cd using grub. Here's a gentoo howto (you don't need gentoo but you will probably need some linux):
[http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB)

---

### Post by fredJones840 on 2006-11-17
ah i c .. ill give it a try .. ive heard of the grub
thanks for the help

---

### Post by bernied on 2006-11-17
You can also try a network install, if you're adventurous, but you still need to get some linux booted on the machine somehow.

---

### Post by fredJones840 on 2006-11-17
network install?

---

### Post by bernied on 2006-11-17
Right, this howto is old (it's for Warty - two releases back I think), but I think it still works. You'll need to adapt a bit:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by bernied on 2006-11-17
...or look for a newer howto...

---

### Post by fredJones840 on 2006-11-17
cool i finally found a disk imaging program to make a smart boot manager disk so i could boot from the cd drive .. awesome .. thanks alot for your help!

---

