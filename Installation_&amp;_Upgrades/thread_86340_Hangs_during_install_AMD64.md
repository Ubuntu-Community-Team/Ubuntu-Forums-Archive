---
title: "Hangs during install AMD64"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by 885i on 2005-11-04
The computer hangs during the installation (both using 5.10 and 5.04 CD's).  The last line reads:  "ohci_hcd 0000:00:13.0: un-link after no-irq? controller is probably using the wrong irq"

What gives?  Thanks in advance.

Doug

---

### Post by skylark on 2005-11-05
I've got no idea, but here's a few random thoughts:

Maybe try different ACPI or APIC settings in the BIOS? Or try the boot option: pci=noacpi (I think there is a way to type this this at the grub menu stage, might have to do a google search)
Do you have any external USB drives/devices attached during install? It's a long shot but try unplugging them during the install if you do.

BTW, is it just Ubuntu you are having issues with - can you boot into other operating systems? (eg other Linux distributions, *BSD, windows...?)

---

