---
title: "What If ???"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2012-06-13
I have a functioning installation of 12.04.  

If I change the video card and reboot, will Ubuntu pick this up, adjust, and start normally - or must I do something special?

If I change the motherboard and reboot, will Ubuntu pick this up, adjust, and start normally - or must I do something special?

If I clone the hard drive to a larger one, will Ubuntu pick this up, adjust, and start normally - or must I do something special?

Thanks!

---

### Post by pissedoffdude on 2012-06-13
Depends on the hardware.  If you have proprietary video drivers currently installed, uninstall them before you change your video card, unless both cards use the same drivers to avoid having any problems with X.  If you change the motherboard, whether or not you have to do something afterwards depends on if it's compatible with ubuntu, but I haven't heard of many which aren't, so there probably won't be anything you need to do.  Cloning the hard drive will be the trickiest part.  You should install grub onto that drive and make sure the configuration in /etc/fstab is set up correctly, meaning you need to configure the cloned drive to be mounted as the root drive, etc.  Also, you need to make sure the grub configuration files point to the new, cloned drive instead of the old one.  I'm not familiar with how grub2 does this, so hopefully someone can fill me in here.

---

### Post by roelforg on 2012-06-13
> **RogerDavis said:**
> I have a functioning installation of 12.04. 
 
If I change the video card and reboot, will Ubuntu pick this up, adjust, and start normally - or must I do something special?
 

 
The worst thing that you might have to do in install additional drivers, but it shouldn't prevent booting. I've done it a million times already myself.
 
> **RogerDavis said:**
> 
 
If I change the motherboard and reboot, will Ubuntu pick this up, adjust, and start normally - or must I do something special?
 

 
It doesn't really care. For ubuntu it's the same as if you'd rip the hdd out of one computer and put it in another one, none of my systems have complained yet. Though i do advise you to empty /etc/udev/rules.d/70-persistent-net.rules so that udev will redetect any onboard network before changing mobo.
 
> **RogerDavis said:**
> 
 
If I clone the hard drive to a larger one, will Ubuntu pick this up, adjust, and start normally - or must I do something special?
 
Thanks!
 
If you'll make a separate thread, me or someone else will happely give you the exact instructions to do this because the cloning only works on identical sized drives. It's not too complex, it just involves some steps to adjust the system. Burn a livecd beforehand because you'll need it for this.

---

