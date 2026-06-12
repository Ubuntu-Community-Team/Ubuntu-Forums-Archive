---
title: "usb installation of 20.04 dose not offer installation alongside existing Windows 10"
date: 2020-09-18
forum: Installation &amp; Upgrades
---

### Post by itzhakyg on 2020-09-18
Prepared a usb stick with ubuntu 20.04. Tied to install it on Lenovo Thinkpas Yoga . I don't get an option to install alongside the existing Windows 10.
would appreciate help.

---

### Post by CelticWarrior on 2020-09-18
Welcome.

Two things to check before anything else:

1. How did you create the the USb installation media? If you used Rufus with the default settings it boots only in Legacy/CSM ("BIOS") mode. your (preinstalled) Windows 10 is surely in UEFI mode. The second OS - Ubuntu - should be installed in the same mode. 

2. In UEFI settings, SATA/Drive mode or similar setting you need AHCI, not "Intel RST" or "RAID". Make sure to install AHCI support in Windows first.

I summary, wrong mode or incompatible drive settings are typically the only causes for your reported issue.

---

### Post by itzhakyg on 2020-09-18
Thanks for the prompt reply.
I prepared the usb on with ubuntu 20.04 on another computer.

---

### Post by Impavidus on 2020-09-18
Have you used Windows tools to create unallocated space on that drive? When Ubuntu sees the hard drive and sees unallocated space (and you haven't hit the limit on the number of partitions, but that applies to the older mbr partitioning), it should be willing to install alongside Windows.

And the Ubuntu installer must be able to detect Windows, so that means disabling FastStartup. If you don't, it may still be possible to install as dual boot in uefi mode, but grub won't boot Windows. Windows will still be bootable through the uefi.

---

### Post by CelticWarrior on 2020-09-18
Oh yes, FAST STARTUP.

In my previous post I forgot about that nasty thing. Yes, it must be disabled (Windows) because it's just hibernation. So, even if all the conditions are met an hibernated Windows won't be detected therefore the option to install alongside won't be offered.

There's a lot more to know now then it was some 10 years ago.

---

### Post by tea for one on 2020-09-18
> **CelticWarrior said:**
> Oh yes, FAST STARTUP.

In my previous post I forgot about that nasty thing. Yes, it must be disabled (Windows) because it's just hibernation. So, even if all the conditions are met an hibernated Windows won't be detected therefore the option to install alongside won't be offered.

There's a lot more to know now then it was some 10 years ago.

Yes, it was certainly easier years ago.

Now, there are various speedy boot iterations with similar names:-

Fast Start Up  (Widows system setting)
Fast boot        (UEFI setting)
fastboot          (grub setting to prevent file system check at boot) e.g.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash fastboot"
```

It's not surprising that dual boot is now more complicated with all these similarly named choices.

It is especially difficult if English is not your native language.

Fortunately, there are now more PCs and Laptops with two drives which allow Windows on one drive and Ubuntu (or other distro) on the second drive.

Then, the easy way to choose the OS is via UEFI boot screen and you hopefully eliminate the dual boot difficulties that pervade the forums.

---

