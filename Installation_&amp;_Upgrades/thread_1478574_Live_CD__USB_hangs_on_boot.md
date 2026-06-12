---
title: "Live CD / USB hangs on boot"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by ghaspias on 2010-05-09
Hi,

I have upgraded my ubuntu install (started with 5.10) quite a few times, with success most of the times, and I think I've booted almost all the ubuntu live cd's in the last years, but I can't get the Lucid Lynx to run.
I downloaded the RC and the final release, ubuntu-desktop-i386.iso and ubuntu-netbook-i386.iso, burned two cd, and installed to an usb device with usb-creator. Tried in qemu, both the iso, the (physical) cd, and the usb device; also tried running in the bare metal, even tried the iso using the loopback device in grub; tried acpi=off, nomodeset, irqpoll, pnpbios=off, in several combinations, but with no success.
I noticed a few messages:
In bare hardware:
Something about a bios-related crash, and suggesting to use pnpbios=off
"ehci (...) no-IRQ? (...)"
lots of
"IRQ #1 - no-one cared", followed by stack trace
lots of
"usb-x-x not accepting address"
and
"/dev/sr0 - no medium found"

In virtualbox:
"Performance Events: unsupported p6 CPU model 15 no PMU driver, software events only", and then
"SMP alternatives: switching to UP code"
this is the last message, then it hangs

In qemu, using "... acpi=off nomodeset expert --"I can follow most of the boot process, up to the desktop, but the desktop is all black


I'll try to get some more systematic info, but for now I don't have the time.
Has anyone had some similar problems - perhaps related to the bios?

My hardware is a clevo 671MX laptop with an Nvidia GeForce 9300M GS.

---

