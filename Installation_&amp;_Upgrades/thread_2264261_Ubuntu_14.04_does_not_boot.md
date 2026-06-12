---
title: "Ubuntu 14.04 does not boot"
date: 2015-02-06
forum: Installation &amp; Upgrades
---

### Post by ffideles on 2015-02-06
Hello guys,

I'm having problems when booting my computer. I have a dual boot computer. The windows works fine, but when I try to boot the ubuntu a black or purple screen appears. I already followed the instructions on [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

The link that boot repair gave me was paste.ubuntu.com/10092455

Thanks!

---

### Post by oldfred on 2015-02-06
If you get grub menu and choice of which to boot, you are booting ok. 
But then issue may be video related. You do show Intel i915 which is a default open source and usually works.
But some need boot parameters. Often nomodeset does not work with Intel, but you add parameters just like adding the nomodeset parameter.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710

[/URL]
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]
[/URL]

---

