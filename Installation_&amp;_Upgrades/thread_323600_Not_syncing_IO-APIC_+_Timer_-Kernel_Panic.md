---
title: "Not syncing IO-APIC + Timer -Kernel Panic"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by carlb on 2006-12-22
I am attempting to build a new machine using Ubuntu 6.10.  I am encountering a problem  "1719570.946000 Kernel Panic -not syncing IO-APIC + Timer doesn't work". 

I can get the Ubuntu install to work by disabling the APIC in the Bios settings but this results in a very unstable system.  Keyboard characters tend to repeat and hard lockups occur.

The hardware is as follows:
Biostar Tforce 550 Motherboard for AM2
AMD A64 X2 3800
Wintec Memory 2x512 MB (1GB)
Maxtor 40gb IDE drive
Samsung 500gb SATA2 drive
Biostar V7102GL26 Video card (GForce 7100)
DVD drive


The hardware is stable and operational under Windows 2K and XP.

I have tried loading Fedora Core 6 and Debian Etch with the same result - Kernel Panics.  I can get the install started with the noapic boot option, but end up with instability or no ability to restart those distributions.

I would prefer to have the system run Ubuntu. So any advice on how to proceed would be appreciated.  Thanks

---

### Post by hemlut on 2006-12-23
> **carlb said:**
> I am attempting to build a new machine using Ubuntu 6.10.  I am encountering a problem  "1719570.946000 Kernel Panic -not syncing IO-APIC + Timer doesn't work". 

I can get the Ubuntu install to work by disabling the APIC in the Bios settings but this results in a very unstable system.  Keyboard characters tend to repeat and hard lockups occur.

The hardware is as follows:
Biostar Tforce 550 Motherboard for AM2
AMD A64 X2 3800
Wintec Memory 2x512 MB (1GB)
Maxtor 40gb IDE drive
Samsung 500gb SATA2 drive
Biostar V7102GL26 Video card (GForce 7100)
DVD drive


The hardware is stable and operational under Windows 2K and XP.

I have tried loading Fedora Core 6 and Debian Etch with the same result - Kernel Panics.  I can get the install started with the noapic boot option, but end up with instability or no ability to restart those distributions.

I would prefer to have the system run Ubuntu. So any advice on how to proceed would be appreciated.  Thanks

I have the same problem.
It tells me to try apic=debug in the grub string but i don't get any debug information.

---

### Post by hemlut on 2006-12-23
I wrote a bugreport about this issue and you can find it here:
[https://bugs.launchpad.net/distros/ubuntu/+source/linux-meta/+bug/76989](https://bugs.launchpad.net/distros/ubuntu/+source/linux-meta/+bug/76989)

Please feel free to confirm this if you feel that its the same issue you are having.

---

### Post by carlb on 2006-12-23
Thanks .  It is the same issue I am having.  I will try to add to the bug report.

---

