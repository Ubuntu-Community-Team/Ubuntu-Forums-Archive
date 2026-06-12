---
title: "Black screen at startup after updating ubuntu 10.04"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by jorn1233 on 2010-09-12
After updating ubuntu 10.04 a few days back, I get a black screen at startup without a flashing cursor or anything. i'm kind of new to ubuntu but not completely.

system specs:
processor: q6600
graphicscard: xfx nvidia gforce 9800gtx+
motherboard:asus p5ql pro
2 hd's 320gb and 250gb

I'm dualbooting with windows 7.

help would be much appreciated I don't want te reinstall everything:/

Jorn.

---

### Post by bob12564 on 2010-09-12
I just started my own thread on this problem about a half hour before yours.

What kernel are you using?  Is it 2.6.32-24-generic?  Try booting using an older kernel from the grub startup menu and see if that boots.  That's my workaround for now.

---

### Post by oldfred on 2010-09-12
I have nvidia & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

---

### Post by bob12564 on 2010-09-12
My problem turned out to be video related too.  I found the solution here:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

