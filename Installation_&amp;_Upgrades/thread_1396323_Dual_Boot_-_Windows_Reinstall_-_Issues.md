---
title: "Dual Boot - Windows Reinstall - Issues?"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by bluetomgold on 2010-02-01
My old-ish Dell laptop is currently running Windows 2000 and Ubuntu 9.10. I originally installed 2000 to try and squeeze a bit more performance out of the laptop for general use, but in practise Ubuntu is running great and sees far more use than the Win2K installation so I've decided to create a stripped-down (i.e. non-networked) XP installation purely to run a few favourite audio applications.

I plan to do a fresh Windows install and wipe the current C: partition. Is there anything I should be aware of in terms of the GRUB bootloader. Will it simply recognise the new XP installation? Obviously I will back up my data before I continue, but are there any other precautions to take with respect to dual-booting? I could do without having to reinstall Ubuntu too!

Thanks!

---

### Post by kansasnoob on 2010-02-01
Boot into Ubuntu and run:

```
grub-install -v
```

Then we'll know what version of grub you have.

---

### Post by bluetomgold on 2010-02-01
Gnu grub 0.97

---

### Post by kansasnoob on 2010-02-02
> **bluetomgold said:**
> Gnu grub 0.97

Then follow the "**How to restore the Ubuntu grub bootloader (9.04 and older)**" steps here:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I realize you have 9.10 but it was obviously an upgrade from 9.04, or you've converted to legacy grub.

---

### Post by bluetomgold on 2010-02-02
Thanks - worked a treat! In the boot menu it still shows up as "Windows 2000" but I'm not about to lose any sleep over that.

---

