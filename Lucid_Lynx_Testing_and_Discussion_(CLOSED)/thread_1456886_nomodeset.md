---
title: "nomodeset"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wojox on 2010-04-17
Okay, I couldn't get lucid to boot. It would show me the options screen and when I would choose try or install the screen would turn black.

So I hunted around and found that by selecting F6 and nomodeset it would work and it did.

I installed and figured I could edit it again ( the kernel ) after Grub loading... came up. Except it never did. So I kept on rebooting and holding down different keys, left Shift, Esc. but nothing. 

I then thought I would boot The live CD and mount the drive and add nomodeset after quit splash. I let me but when I ran update-grub it said the drive was not mounted.

Any ideas anyone, besides waiting for the final release and hope it works?

---

### Post by ronparent on 2010-04-17
Left shift should've worked. Hold it down as the initial bios splash screen passes. You can use the live cd to make permanent changes to the boot parameters by **sudo gedit /etc/default/grub** - add nomodeset to the kernel boot line. 

Post how you make out.

---

