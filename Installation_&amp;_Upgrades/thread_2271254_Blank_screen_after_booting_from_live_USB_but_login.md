---
title: "Blank screen after booting from live USB but login sound audible"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by mirz-hq on 2015-03-28
A couple days ago I've finally bought a new desktop PC (with nvidia gtx 960). I  installed Windows 8.1 in legacy boot mode and then I wanted to install  Ubuntu 14.04 from USB stick. After the very first screen (with small  image at the bottom, I can go to advanced options there), screen becomes  black (only caret is blinking) and nothing happens. After a short time I  can hear ubuntu login sound, so I assume that something is wrong with  video. I've tried set nomodeset, acpi=off and nolapic but It didn't  help. What can I do?

After one of the attempts following log shows up:
```
nouveau E[  DEVICE][0000:01:00.0] unknown chipset, 0x126010a1
nouveau E[     DRM] failed to create 0x80000080, -22
```

---

### Post by Vladlenin5000 on 2015-03-28
Hello and welcome.

Whatever the problem is with whatever "unknown chipset" nouveau is complaining about, ***nomodeset*** should have worked, ie, it should result ina a live session with generic vesa video. Are you absolutely sure you've set the option? *acpi=off* and *nolapic* shouldn't be needed for any recent hardware and can actually give unexpected weird results. And considering it's a new, UEFI enabled hardware, why did you installed Windopws 8.1 in legacy mode? If you intended to have a dual boot either mode can do as long as both OSs are installed in the same mode -and- there are advantages with UEFI and GTP partitioning. If you intended to do things the "old way" you should have used up to Windows 7.
Anyway...
Please give more info regarding the hardware.

---

### Post by mirz-hq on 2015-03-29
I actually had no idea in what mode I had been installing win 8. I had just booted win 8 from usb and installed. After that I realized that win is installed in legacy mode.
Should I install it once again in uefi?
Nomodeset had no effect when I set it in graphical menu (f6 after booting ubuntu). But it works when I had edited grub entry for live usb.

---

