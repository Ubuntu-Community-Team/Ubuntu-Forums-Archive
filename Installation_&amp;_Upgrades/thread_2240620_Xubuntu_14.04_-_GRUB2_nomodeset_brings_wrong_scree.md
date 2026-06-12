---
title: "Xubuntu 14.04 - GRUB2 nomodeset brings wrong screen resolution"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by ekajogja on 2014-08-21
Hello, I'm using Xubuntu 14.04 on Acer TravelMate 4740 with Intel HD Graphics.
Yesterday, during boot I got white screen instead of login screen.

Edited /etc/default/grub with these values:


[LIST]
[*]nomodeset
[*]GRUB_GFXMODE=1366x768
[*]GRUB_GFXPAYLOAD_LINUX=keep
[/LIST]

Then sudo update-grub.
After reboot, everything works normal.

Problem is, after some reboot (3-4 times), screen resolution get stucked in 1024x768 instead of 1366x768.
Checked grub file, above settings are still there. Also confirmed that without nomodeset I always get whitescreen.

Are there any different method to fix the screen resolution?
Or, are there any alternative instead of nomodeset?

Thanks in advance :)

---

### Post by oldfred on 2014-08-21
Usually with Intel you do not use nomodeset but other boot options. Often to explicitly set size. See post by ubfan1 below.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

LInk shows several others also, but with Intel it usually is one of these instead of nomodeset, but use your 1366x768 not example shown:
i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

---

### Post by ekajogja on 2014-08-21
Thank you very much oldfred, it works :p

---

