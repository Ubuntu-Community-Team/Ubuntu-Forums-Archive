---
title: "Multiple Distros"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by markr on 2005-11-24
I have Ubuntu breezy as my primary desktop at the moment but fancy trying Fedora as I'm a tinkerer!

Currently my partition is 

WinXP
Ubuntu
Swap

Couple of questions:

1. Can I share my SWAP parition between Ubuntu and Fedora (I'm not sure if it gets cleared when you shutdown or not)

2. I'm assuming I can instruct Fedora not install GRub, and then just add it manually to my Grub list held on Ubuntu?

Thanks

Mark.

---

### Post by Pablo_Escobar on 2005-11-24
1. Yes swap sharing is safe (but if You're using hibernate function - laptops - there are something to be remembered)
2. Yep, it shouldn't be to complicated.

---

### Post by markr on 2005-11-24
Hmmm, I do have a laptop and although it's not working at the moment I do intend on using hibernate - what issues do I need to worry about?

Mark.

---

### Post by Pablo_Escobar on 2005-11-24
I'm not an expert in laptops but that is a post by azz from a different thread:
> If you do not like to turn off your computer in the usual fashion, but put it into hibernation, it writes the contents of memory onto the swap. Then, when you boot, the swap is probed and if there is an image there, it will load it into memory and resume from there. If you use hibernation, you could not use the swap for another installation since that would screw up your saved session.

If you do not use this, then sure, you can use the same swap for different linux installations.


From what I understand : Do not switch to other distro while the image from other distro is on the swap.

---

