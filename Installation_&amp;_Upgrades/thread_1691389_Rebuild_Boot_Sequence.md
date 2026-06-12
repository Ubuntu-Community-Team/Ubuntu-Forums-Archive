---
title: "Rebuild Boot Sequence?"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by klausner on 2011-02-19
I've done something to my Lucid system so that it will not boot to graphics mode. Says something like "No terminals found".

The weirdest thing is that if I first boot a USB or CD, then immediately re-boot from the hard drive, all is fine! For one bootup.

Is there a way to rebuild the boot sequence on the hard drive without doing a complete install?

---

### Post by wilee-nilee on 2011-02-19
> **klausner said:**
> I've done something to my Lucid system so that it will not boot to graphics mode. Says something like "No terminals found".

The weirdest thing is that if I first boot a USB or CD, then immediately re-boot from the hard drive, all is fine! For one bootup.

Is there a way to rebuild the boot sequence on the hard drive without doing a complete install?

On the actual boot into the install have you run.
sudo update-grub

Really your going to have to be more specific.

---

### Post by klausner on 2011-02-19
> **wilee-nilee said:**
> On the actual boot into the install have you run.
sudo update-grub

Really your going to have to be more specific.

????? I don't understand your confusion. This has nothing to do with grub. The grub screen is fine. As the post says, I "boot to graphics mode."

---

### Post by PaulReaver on 2011-02-19
klausner
you said you can boot up into your machine after using a live cd? confusing.... could be dangerous but you could try fixing your initrd with

sudo mkinitrd -o /boot/initrd.img-`uname &#8211;r` `uname &#8211;r`


try this as a VERY last resort though... before you wipe it and start again of course.

I would try everyone else's ideas first....

---

### Post by klausner on 2011-02-19
> **PaulReaver said:**
> klausner
you said you can boot up into your machine after using a live cd? confusing.... could be dangerous but you could try fixing your initrd with

sudo mkinitrd -o /boot/initrd.img-`uname –r` `uname –r`


try this as a VERY last resort though... before you wipe it and start again of course.

I would try everyone else's ideas first....

How would the consequences of trying this be worse than what I have now?

Thanks.

---

### Post by PaulReaver on 2011-02-19
what this'll do is rebuild your initial ram disk... 

initrd is basically the kernel and important modules getting loaded into ram before everything else has the chance to load.... kinda like boot strapping for linux....

it might make a new initrd with the correct graphics modules in. 
I don't see how it could make things worse but you never know....

sorry mate... can't promise it'll fix anything

although I would at least try this before committing to wiping the machine and starting again.

---

### Post by klausner on 2011-02-19
> **PaulReaver said:**
> what this'll do is rebuild your initial ram disk... 

initrd is basically the kernel and important modules getting loaded into ram before everything else has the chance to load.... kinda like boot strapping for linux....

it might make a new initrd with the correct graphics modules in. 
I don't see how it could make things worse but you never know....

sorry mate... can't promise it'll fix anything

although I would at least try this before committing to wiping the machine and starting again.

Fair enough. I'll wait a bit though to see if there are any other ideas or explanations. I really don't understand why booting from one device should make another, unmounted device temporarily work. I've put up with this for a week though, so I'll watch the thread for a couple of days before doing anything final.

Thanks again.

---

