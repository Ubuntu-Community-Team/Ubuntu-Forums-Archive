---
title: "Ubuntu 15.10 Live USB.  Dell Alienware 13. Live USB won't boot at all"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by sevenfourk on 2015-12-21
Hi guys,

Trying to boot Ubuntu 15.10 Live USB on Dell Alienware 13 R1.

Laptop specs:
Screen Size: 13 inches
CPU: 1.7 GHz Core i5-4210U
RAM: 16G DDR3
Hard Drive: 1000 GB SATA
Graphics: NVIDIA GeForce GTX 860M with 2GB GDDR5

During boot I see some messages about Nouveau video driver, then unexpectedly laptop just reboot by itself and this behavior repeats again.

Sometimes the process goes further to Ubuntu logo with red lights switching, right before the Ubuntu system has to be started, but it hangs or reboots like before.

For now my mission is only to boot Ubuntu, at least boot.

Any ideas?  Thanks.  

Ivan.

---

### Post by ubfan1 on 2015-12-21
There are a variety of options to try for the Nvidia chips, the first one is "nomodeset" (one of the function keys for kernel options).  Then install the proprietary Nvidia drivers, and things should work better.

---

### Post by oldfred on 2015-12-21
If an UEFI system, you need to boot installer in UEFI boot mode and manually add nomodeset boot parameter. But if boot is with Intel video, it may need different boot parameter. Do you know if Intel or nVidia is default video when booting?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
      [/URL]
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]

[/URL]

---

### Post by sevenfourk on 2015-12-22
Thanks guys.  Will try this and let you know.  Indeed [COLOR=#000000]UEFI system.[/COLOR]

---

