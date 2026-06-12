---
title: "HP workstation xw6400 with 16gb RAM 14.04 not installing"
date: 2014-10-09
forum: Installation &amp; Upgrades
---

### Post by aspidistra on 2014-10-09
12.04 will install on above machine. 14.04 the live cd won't even boot. Have tried the
alterative (text) install of lubuntu 14.04 which got me through an install but then
the OS won't boot.

I don't know what to do - how to address this. The bios was reset to factory. I installed
12.04 then manually upgraded to 14.04 then that doesn't boot - won't boot at all
black screen. Can't even get in.

Have tried installation (14.04) from USB key, and from DVD. Neither boot.

Why is this?

---

### Post by sudodus on 2014-10-09
Often an older version works better with ageing hardware.

I have an HP xp8400 workstation and I'm happy with Ubuntu 12.04.5 LTS. I have upgraded the graphics to nvidia GT 430 and I run NVIDIA's 304.88 proprietary driver. I use xubuntu-desktop most of the time, and in April, when it will reach end of life I will test 14.04.1 in my workstation. (I run Ubuntu 14.04.1 LTS in a newer Toshiba laptop, where it works well.) But I will not try hard to squeeze it into the workstation. Instead I might start running [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks"), which promises support until April 2017.

I suggest that you stay with 12.04 LTS :-)

---

### Post by oldfred on 2014-10-09
The specs show many different types of video cards available, what do you have.

AMD dropped mainline support of older cards, but open source driver should work. But you may need nomodeset.
May be difference between an older driver in 12.04 and that driver now not in 14.04?
NVidia often needs nomodeset to get into low quality graphics until you install correct nVidia driver for your card.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by gifford on 2014-10-09
I have a HP xp8600 workstation and have run Ubuntu 12.04 and now 14.04 without problems. You did indicate you reset the bios to factory, what is the boot order now?
Also, what video card to you have installed?

---

