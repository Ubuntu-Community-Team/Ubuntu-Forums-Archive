---
title: "Dual boot with Windows 10"
date: 2016-02-19
forum: Installation &amp; Upgrades
---

### Post by pieter3 on 2016-02-19
Hello everybody,

I recently bought a new Lenovo ideapad 500s with a 256GB SSD and Windows 10 pre-installed.
I wanted to install ubuntu 14.04, so I grabbed a live USB, shrunk the standard Windows partition and installed it.
Ubuntu did not, however, install its own bootloader. So now I'm stuck with an installation of windows on the first partition, and ubuntu on the second.
If I boot the computer, Windows 10 just boots up. I can't find a way to boot into the second partition with Ubuntu on it. I tried googling around a bit, but I could not find a solution.

Any ideas on this?

Thanks in advance,
Pieter

---

### Post by oldfred on 2016-02-19
Did you install Ubuntu in UEFI boot mode?
May be best to see details. You can run this from Ubuntu live installer in live mode.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by pieter3 on 2016-02-20
The problem was indeed the boot mode. I used the YUMI multiboot USB creator to install Ubuntu the first time, which can apparently only boot in Legacy BIOS mode. I now used Rufus on Windows to install the Ubuntu iso to an empty USB drive, set the BIOS to UEFI boot, and re-installed Ubuntu. Now my laptop boots to GRUB, and everything works as it's supposed to. Thank you!

---

