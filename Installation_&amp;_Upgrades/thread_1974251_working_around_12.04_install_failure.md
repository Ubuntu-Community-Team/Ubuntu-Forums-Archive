---
title: "working around 12.04 install failure"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by aaronbp on 2012-05-05
So the install program is consistently failing. Tells me my hdd or disk drives are either broken or overheating. Maybe they are overheating, but they aren't broken. 

I tried rsyncing / to a mounted /dev/sda1. It seemed to work, but when trying to boot from it I get stuck at

```
Verifying DMI Pool Data
```I don't have a backup system, so I can't exactly try re-burning the live-cd. I'm on an older PC and my motherboard doesn't support booting from USB. What I'd *like* to try to do is modify grub and boot from USB that way, hopefully to get this thing properly installed. That's within the realm of possibility, isn't it?

---

### Post by aaronbp on 2012-05-07
Thanks for the help, you guys. :P 

For posterity, here's how I solved the problem. I ran grub-install on /dev/sda, and downloaded a utility called the plop bootloader.

Extract the bootloader, cd to the Linux directory, and copy the files to $sda1mount/boot.

type

```

> linux16 /boot/plpbt.bin
> boot

```

when grub runs. It'll load a menu that allows you to boot from USB, even if your motherboard doesn't support it. So I boot into Ubuntu that way, but even still the install failed. So I downloaded the mini.iso from the usb install and burned it to a cd (which I would not have been able to with a livecd because I only have one disk drive), and was able to install from there.

---

