---
title: "Problems installing Ubuntu 6.06"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by rziegler72 on 2006-10-06
Hello,

Forgive me if I'm in the wrong place.  I'm new to Linux & Ubuntu, and know little about hardware.

I'm having problems trying to install Ubuntu 6.06 on a brand new system:

Intel motherboard with integrated video/sound
1 Intel 6600 Core 2 Duo 2.4 ghz CPU
2 gb RAM (4 x 512mb)
2 x 320GB SATA hard drives

I can boot from the CD to the initial install screen and choose the option to 'Start or install Ubuntu'.  It says 'Loading Linux kernel...' but then just hangs at 'Uncompressing Linux... Ok, booting the kernel.'  The CD light just stops and it goes no further.

The CD itself should be fine, since I've used the exact CD on 2 other smaller systems which installed fine.

I don't think it's a problem with the new system, since I tried a WinXP install and that worked fine, but I don't want to go back to that...

From some Googling I found a couple boot options (using F6 at the menu) that I've tried at the initial boot menu.

Using the boot option 'noapic acpi=noirq nolapic' tells me:

Uncompressing Linux... Ok, booting the kernel.
[17179569.184000] BIOS bug, no explicit IRQ entries, using default mptable. (tell your hw vendor)
[17179569.828000] BIOS bug, local APIC #0 not detected!...

If I try the boot option 'noapic acpi=off' this gets a bit further ang goes to the screen with the brown Ubuntu progress bar:

Loading essential drivers     ok
Mounting root filesystem

but then I get this again:

Uncompressing Linux... Ok, booting the kernel.
[17179569.184000] BIOS bug, no explicit IRQ entries, using default mptable. (tell your hw vendor)

I'm not sure what these boot options really mean, and they haven't really gotten me further, but just given me different error messages.

Any help is greatly appreciated.  Please let me know if there is any other info I can provide.  I really don't want to go back to Windows.

~Rick

---

### Post by Cynical on 2006-10-06
Yes its a problem with every p965 chipset based motherboard. The patch is already in the latest daily builds.

[http://cdimage.ubuntulinux.org/daily-live/current/](http://cdimage.ubuntulinux.org/daily-live/current/)

---

### Post by rziegler72 on 2006-10-06
Thank you for the prompt reply.

So, does this mean I'd have to use 6.10 (Edgy Eft) instead of 6.06 (Dapper Drake)?  A fix like this isn't available in 6.06?  Would I lose Long Term Support (LTS) benefit by going with 6.10?

~Rick

---

### Post by ColDebug on 2006-10-06
I would like to know the answer to that as well. None of the 2.6.17 - 2.6.19 builds work with my tv card (no sound) and I really don't want to wait another two weeks to see if the desktop is stable (it wasn't when i tried it three days ago).

I really don't see how this could be called an LTS release if a solution isn't on the way - or will edgy also be an lts release?

---

