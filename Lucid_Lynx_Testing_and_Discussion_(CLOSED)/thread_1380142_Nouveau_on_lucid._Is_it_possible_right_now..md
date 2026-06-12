---
title: "Nouveau on lucid. Is it possible right now."
date: 2010-01-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by orlox on 2010-01-13
I just installed lucid (x86_64), but I was previously using the 32 bit version of lucid. In both cases, I wasn't able to use the nouveau driver, because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/496100](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/496100)

In a nutshell, nouveau tries to remove all xorg to get installed. Is there a possible work around for that??

---

### Post by SevenMachines on 2010-01-13
not at the moment. the last time i checked ppa:xorg-edgers/nouveau was suffering the same problem****

---

### Post by SevenMachines on 2010-01-13
actually, a no change rebuild of xserver-xorg-video-nouveau will allow it to be installed if your feeling brave (i'm using the xorg edgers version). modesetting causes a freeze here but if its disabled at grub with the  'nomodeset' option it seems to work fine

---

### Post by orlox on 2010-01-13
I just installed it from the xorg-edgers ppa. Don't know why it didn't uninstalled evrything, I just tried it in the morning and it did...

What do you mean with a "no change rebuild"??

---

### Post by orlox on 2010-01-13
Currently using nouveau :D

I didn't need to specify nomodeset, using a Geforce Go 6150. Perhaps there's a particular issue with your video card...

On a different note, I'm getting an 18 second boot, from grub to a complely usable desktop. NICE! (It's probably due to other stuff besides nouveau though...)

---

### Post by SevenMachines on 2010-01-13
there does seem to be a couple of problems with my card, the modesetting problem and detecting the wrong resolutions at desktop start, nothing major.
hopefully the microcode issue will be resolved and this will enter the kernel tree soon which is bound to help, i'd quite like to make the permanent switch rather than flitting back and forth between the two available drivers in indecision :)

* by no change rebuild i just meant making no changes to but rebuilding from the packaging source.

---

### Post by gnomeuser on 2010-01-13
This no-change rebuild thing really should be resolved, it has been preventing easy testing for most of the Lucid cycle.

---

### Post by Jimmyfj on 2010-04-27
Just wondering: Would I have any issues on my Gee-Force 8600 GT 1GB PCI-E graphics card if I try to install Nouveau?

---

