---
title: "Acer Aspire One Ubuntu 9.04 (Input needed)"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by patrickclover on 2009-04-04
Hi, i have just bought an acer aspire one and wow its sexy. 
as soon as i opened it i booted to the "lunpus"? and thought F$#@ this so like the ubuntu lover that i am i installed 9.04 (Jaunty) all is good.

wifi = yes
webcam = yes
mic = yes
speakers = yes
trackpad = yes

now on to the part where i need some input off some of you wise chaps :).

i recently bought a 16GB SD card (class 6 best speed) on linpus in pops up saying "Expansion added" and the hard drive on Thunrar just grew by 16GB. well done to acer nice little feature, now to the point i want ubuntu to do this... both the systems are linux, why can i not do this in ubuntu well maybe i can if so how?? all cards are detected (apart from XD) but i want the expansion to add on to the internal SSD. 

ANYONE please! :( help me out :D

Thanks all helpers, Patrick

---

### Post by ozorba on 2009-04-04
What you are asking is not possible with Ubuntu at the moment.

---

### Post by taavikko on 2009-04-04
> **ozorba said:**
> What you are asking is not possible with Ubuntu at the moment.

Actually it is to some extent.
It just involves little bit of tweaking.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
> pciehp module does not exist - It is compiled into kernel (Needs pciehp.pciehp_force=1 to be passed to kernel in /boot/grub/menu.lst for right side reader to work. Left side slot works out-of-box with kernel 2.6.28-11. Caveat: This option doesn't play nice with kernel and will slow resume from suspend and fill your kern.log with warnings.)

---

### Post by bennachie on 2009-04-04
> **ozorba said:**
> What you are asking is not possible with Ubuntu at the moment.

It does work in Fedora 10 and Fedora 11 beta, both of which are actually, in some respects, easier than Ubuntu to install on an eeePC (mainly because the installer recognises the screen resolution properly, and adjusts the dialogue panels appropriately). The downsides are that both versions chew up a lot of disk space, and Fedora 11 beta could charitably be described as being considerably less ready for prime time than Jaunty.

I actually prefer having the external SD card explicitly mounted; allowing me to carry and use more than one card without stuffing up the file system. Since Jaunty installs into ~2.7GB, there is no actual need for the internal SSD to be expanded, even on my modest 701 4G.

---

### Post by patrickclover on 2009-04-04
Thank you all :) so lightweight linpus can do it and ubuntu jaunty cannot?? hmm

the card reader works "out of the box" but the left one (expansion storage) performes just the same function as the right?? :S i would rarther it just added 16GB on too my home folder when it was in? any way ? thanks for the input guys! much appreciated

---

