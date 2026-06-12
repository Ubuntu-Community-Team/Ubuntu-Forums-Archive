---
title: "audio not working after upgrade"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by warhammerkid on 2008-05-06
After upgrading to 8.04 from 7.10 audio has stopped working. Doing an lspci returns my card: ```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
``` but if I do a ```
cat /proc/asound/cards
``` it doesn't list my sound card. Digging through dmesg I found this error ```
[   45.250939] HDA Intel: probe of 0000:00:1b.0 failed with error -16
```, but I don't know how to resolve it. Any help would be appreciated.

---

### Post by prshah on 2008-05-06
> **warhammerkid said:**
> ```
[   45.250939] HDA Intel: probe of 0000:00:1b.0 failed with error -16
```

I think "error -16" indicates a BIOS issue... is the onboard sound enabled in your BIOS? If it is, try toggling it, or restoring default settings, or changing options if you have any, (Eg, HDA, 5.1, 2.1, legacy etc)

Maybe a clash with some other PnP hardware? (TV Tuner is a prime candidate...)

---

### Post by warhammerkid on 2008-05-06
The full error message in dmesg is this:
```
[   45.499656] PCI: Unable to reserve mem region #1:4000@febfc000 for device 0000:00:1b.0
[   45.499868] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[   45.499966] HDA Intel: probe of 0000:00:1b.0 failed with error -16
```

When I boot with acpi=off, it fixes the issue, but that causes my IDE HD to disappear (I'm using an ASUS P5B motherboard w/ jmicron on). In addition, toggling the bios setting has no effect - although it shouldn't be a bios issue because it worked in Gutsy. Has the kernel upgrade broken support for my motherboard?

---

