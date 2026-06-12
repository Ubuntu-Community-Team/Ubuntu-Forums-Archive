---
title: "Kernel Woes after Lucid Upgrade"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by mikeage on 2010-05-25
I recently upgraded one of my machines (an old Presario 900-series Laptop) to Lucid, and I've been having difficulty finding a suitable kernel.

As part of the upgrade, it installed kernel 2.6.32-22. With this kernel, none of my networking devices are present [eth0 is not found, and the wireless card I use (DWL-650+ PCMCIA) is also not recognized; in fact, the PCMCIA slots don't even recognize that a card is inserted].

If I go back to 2.6.31-21, then all of my devices work correctly, but the screen in X is "dim" [it appears that it's not a gamma problem; I can't get a decent look no matter how much I play with xgamma] and very hard to see. The console looks just fine.

Attached are dmesg logs from several kernels [I also tried 2.6.32-21, but it was the same as 2.6.32-22]

---

### Post by alterpinguin on 2010-05-26
if it is not a hardwar fault,
this sounds like powersaveing works to much for you.
Normally for laptop-users the backlight should dimm after some minutes of no user-action and after more time it should be shut of to save power.
If this is an acpi issue doing it the wrong way,
you might test it with an kernel-boot-option like: acpi=off
there are other flags too
like
noacpi
noapic
and it is possible to disable acpi for special parts like
pci=noacpi
(you can google for more information about such settings)
there could be a kernel<->hardware problem and
i have seen laptops, where the user could set the backlight-power
with special keyboard-keys.
And for laptops with nvidia-graka-chips, there were entries in the
propriatry-module - and there are differnt versions from nvidia, and not all will work the same way. (i remember one laptop with nvidia-graka, that was not able to update for some time, because the newer drivers did not work in a clean way)

---

### Post by dino99 on 2010-05-26
> **mikeage said:**
> I recently upgraded one of my machines (an old Presario 900-series Laptop) to Lucid, and I've been having difficulty finding a suitable kernel.

As part of the upgrade, it installed kernel 2.6.32-22. With this kernel, none of my networking devices are present [eth0 is not found, and the wireless card I use (DWL-650+ PCMCIA) is also not recognized; in fact, the PCMCIA slots don't even recognize that a card is inserted].[COLOR="Red"]kernel 32 have many issues[/COLOR]

If I go back to 2.6.31-21, then all of my devices work correctly, but the screen in X is "dim" [it appears that it's not a gamma problem; I can't get a decent look no matter how much I play with xgamma] and very hard to see. The console looks just fine. remove xorg.conf: [COLOR="Blue"]sudo rm -f /etc/X11/xorg.conf[/COLOR]

Attached are dmesg logs from several kernels [I also tried 2.6.32-21, but it was the same as 2.6.32-22]

stay with kernel 31 or install 33/34

---

### Post by mikeage on 2010-05-26
> **dino99 said:**
> stay with kernel 31 or install 33/34

I don't see any packages for 2.6.33 or 34; is this something I have to install manually [I haven't compiled a kernel for a non-embedded platform since about 2001, but I think I still remember most of it :)]

If I stay with .31, I have the problem with the display, which makes the machine mostly unusable in X.

---

### Post by mikeage on 2010-05-26
> **alterpinguin said:**
> if it is not a hardwar fault,
If this is an acpi issue doing it the wrong way,
you might test it with an kernel-boot-option like: acpi=off
there are other flags too
like
noacpi
noapic

...

i have seen laptops, where the user could set the backlight-power
with special keyboard-keys.

I'll check noacpi and noapic. Thanks.

With the HW keys, I can dim it more, but the default dim setting is as bright as it gets.

> **alterpinguin said:**
> And for laptops with nvidia-graka-chips, there were entries in the
propriatry-module - and there are differnt versions from nvidia, and not all will work the same way. (i remember one laptop with nvidia-graka, that was not able to update for some time, because the newer drivers did not work in a clean way)
It's an ATI Radeon Mobility U1 chipset [like I said... real old]

---

### Post by mikeage on 2010-05-26
> **mikeage said:**
> I'll check noacpi and noapic.

Didn't help. Same problem.

---

### Post by mikeage on 2010-05-28
> **dino99 said:**
> install 33/34

Same problem as 32


Logs attached.

This is quite strange; I have other PCs running Lucid just fine... what could cause both PCMCIA and the onboard eth0 to suddenly disappear?

---

