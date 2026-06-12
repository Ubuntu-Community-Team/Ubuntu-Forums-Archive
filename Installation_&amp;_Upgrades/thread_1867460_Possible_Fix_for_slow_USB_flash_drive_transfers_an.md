---
title: "Possible Fix for slow USB flash drive transfers and freezes"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by recluce on 2011-10-23
Appparently, this problem has been around since Ubuntu 8.04 and still is alive and well. Please read the description of the problem as I had it and the solution I found. There is more than one issue with USB file copies, so be sure this is the one you have!

Symptom: when copying large files (let's say larger than 1GB) to a USB flash drive (aka USB Stick or Thumb Drive), the copy starts very fast and slows down to a snail's speed after a while, significantly less than the flash drive is capable of handling. At the same time, you may experience intermittent system stalling - application windows graying out for a couple of seconds, even the mouse cursor might freeze. Once the copy process ends (finished or you yank the flash drive out to end the agony), everything returns to normal.

Solution: on many modern systems, an interrupt that deals with USB on non-ACPI computers, should be disabled during the boot process, but isn't. You can manually disable this interrupt by adding the following to your GRUB's KERNEL command:

```

pci=acpi

```

In Legacy GRUB, you add this code in menu.lst to the kernel command line of your kernel (where it says "ro quiet splash"). In Grub 1.99, you have to add the parameter in grub.cfg to the option line of your kernel. YOu may or may not have to repeat this after upgrading to a new kernel.

All I can say is that it worked for me. (Ubuntu x64 10.04.3 with Natty kernel 2.6.38-12). I found the solution in the 13 pages of this thread:

[http://ubuntuforums.org/showthread.php?t=1306333&page=13](http://ubuntuforums.org/showthread.php?t=1306333&page=13)

Can you believe that bugs like this one (make system unusable, drive people back to Windows) have not been taken care of since 2008? I guess that all that counts nowadays is additional bling...

---

### Post by il3dsm on 2012-01-05
I think... I love you.

I've been looking for a solution to this problem for ages, and this fixed it for me. 

Thanks a lot !

---

### Post by Ylere on 2012-03-21
This bug was a big problem for me for years!!!
I never really found a solution for it but your fix finally works!
Thank you very very much!

---

### Post by kholsheimer on 2012-07-19
Cheers, this was very annoying indeed..

I just wanted to add that if you're using GRUB2 and you want to have the *pci=acpi* option to be preserved by kernel upgrades, you need to edit the file */etc/default/grub*. Simply open ```
gksu gedit /etc/default/grub
``` and add the *pci=acpi* option to the parameter GRUB_CMDLINE_LINUX_DEFAULT. In my case, this meant changing the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=acpi"
```

---

### Post by kholsheimer on 2012-07-19
Damn, I just realized that this doesn't solve the problem on my own system. Transfer is really fast, but it stalls for a relatively long time right before the end.

It seems that there's a bug report on this, but it doesn't seem very active..

[https://bugs.launchpad.net/ubuntu/+source/fl-cow/+bug/599755](https://bugs.launchpad.net/ubuntu/+source/fl-cow/+bug/599755)

---

### Post by nonbeing on 2012-07-31
Thank you very much, recluce and kholsheimer. This simple "fix" worked for me too (Linux laptop 2.6.32-41-generic #94-Ubuntu SMP Fri Jul 6 18:00:34 UTC 2012 x86_64 GNU/Linux, 10.04.4 Lucid). 

I'm easily getting average speeds of > 10 MB/s now. I only got around 0.5 MB/s (average) prior to the fix. And sometimes average speeds are upto 25 MB/s. That's an amazing improvement!

Thanks!!

*sigh of relief*

---

