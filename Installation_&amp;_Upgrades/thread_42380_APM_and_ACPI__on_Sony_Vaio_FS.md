---
title: "APM and ACPI  on Sony Vaio FS"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by lgiomi on 2005-06-17
Hi folks,

I just installed Hoary on my Sony Vaio VGN- FS115S and I'm experiencing a bounch of problems related with the power management. First of all, in order to successfully run the kernel, I have to boot the system with the acpi support disabled (i.e. boot:linux acpi=off apm=on). Then I tried to use apm instead of acpi by including it as module and following the  instructions found on the [SuspendHowto](https://wiki.ubuntu.com//SuspendHowto), but apm simply doesn't recognize the battery of my laptop:

```
luca@elianto:~$ apm -vd
APM BIOS 1.2 (kernel driver 1.16ac)
On-line, no system battery
Using device 0x0a86, 1.16ac: 1.2
APM Flags      = 0x03; Line Status   = 0x01
Battery Status = 0xff; Battery Flags = 0x80
Battery %age   =   -1; Battery Time  =   -1, use_mins=0

```

do you have any suggestions?

thanks,
- Luca

---

