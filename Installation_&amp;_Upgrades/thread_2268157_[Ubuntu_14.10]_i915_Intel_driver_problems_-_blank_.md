---
title: "[Ubuntu 14.10] i915 Intel driver problems - blank screen on boot"
date: 2015-03-06
forum: Installation &amp; Upgrades
---

### Post by Wesley32 on 2015-03-06
Hey everyone, 

Weird issue that I can't seem to trace down and eliminate. I have the Intel i915 driver that was installed with the Ubuntu 14.10 installation. 

First time booted up fine, everything worked for the whole day. Then, I go to reboot, and it reboots to a blank screen. Can't get past it, have tried multiple things. 

- Have tried setting nomodeset in the GRUB2 menu for ubuntu. didn't do anything different. 
- Set i915.blacklist=1    Also did nothing
- set i915.nomodeset=1 nothing
- also tried the brightness settings that people have talked about on various forums. Where you set it to 30% in some config file, can't remember the name and place ATM.

Although, I can boot to the text menu if I put "text" after the "no quiet splash" part in the grub file. 

So, to fix this, I think I need to uninstall all packages and drivers that are new for the i915 chipset, then reinstall older drivers that will be compatible. Does this sound on the right track? 

Can anyone help me out?

---

### Post by oldfred on 2015-03-06
Have you tried these also?
 Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

There is only one i915 driver except for a direct download from Intel of the experimental version.

---

### Post by MAFoElffen on 2015-03-06
+1 with oldfred with a few additional's:

The video driver for the old Intel i915 *IS* the xorg driver. Intel gives their linux code away as opensource to Xorg. So if you think for some reason that the driver went south, it would be reinstalling xserver-xorg-video-intel or if not that then the whole xserver package... But before doing a whole Xserver replace, [COLOR=#ff0000]tell me[/COLOR], as there is a trick to doing that and having everything hardwired back in the right order...

But before doing any of that... If you boot it to text... then copy your /var/log/Xorg.0.log over to something to post here. If you do, I'll try to keep an eye out for your post to look at it for you. It would be good to include the lightdm log also... why? Because even if it did use the right driver, the old i915 is a @D capable video GPU (No 3D) so will not do Unity3D nor Gnome3 (full effects/3D)... so just does the older Gnome fall-back graphics (Unity 2D went away).

Heck. Just for grins, post the results of this to confirm what GPU you do have:
```

sudo lshw -c video -n

```

But if it was working and all of a sudden now doesn't... we can see what may be going on from those 2 files.

---

