---
title: "Triple boot with Ubuntu, Mac OS and Joli OS"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by iangarforth on 2011-09-18
Hi all,

I'm sorry about this - I'm a bit of a n00b and not totally sure what I'm doing...

In a perfect world, what I'm really after is a triple-boot MacBook.  I want to go straight to rEFit (or something else if necessary) and default to my Ubuntu install, but be able to select my Mac OS or Joli OS when required.

My hard drive is partitioned with a 200MB efi partition, a 70GB hfs partition, and then it did have a 30GB Ubuntu partition (on ext4), a 1400MB swap area, and then an 8GB partition with my old Ubuntu install.

In this scenario, everything showed up in rEFit, and though I actually didn't go back into check that my old Ubuntu install was still working when I installed my new one, I shot straight in to installing Joli OS over the top of the last partition.  

Though it installed fine, and booted fine, I now only had one Linux choice showing up in rEFit.  Nuts, thought I.  I thought they were fine sharing the swap space, but wasn't sure, so re-installed Ubuntu, and at the same time split its 30GB partition into a 1.5GB swap space and a 28.5GB install.

I've just rebooted that, and again, I still only have one Linux install to choose from though this time it boots to Ubuntu.  So as far as I know, the Joli OS installation is fine - it's just sat there fat, dumb and happy waiting to go, but nothing from the boot menu allows it to.

I know also have two swap spaces, and I have no idea which installation points to which one.  Is there a way to find this out?

Any help would be very gratefully received.

Cheers all.

---

### Post by iangarforth on 2011-09-18
Idiot.  Scrub that...

Though only one penguin shows up in the rEFit splash screen, choosing the Tux icon takes me to the GRUB choice screen, from which I can choose Ubuntu or Joli OS.  It ain't pretty, but everything works, which is all cool.

Can anyone suggest a way to make it prettier?

Also, how do I assess which swap space Ubuntu is using, and which Joli OS is using?  Is it pointless having two?  Have I wasted 1GB for no reason?

---

