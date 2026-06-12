---
title: "Big problems with MSI K8N Neo and Athlon64 (32bit mode)"
date: 2004-11-04
forum: Installation &amp; Upgrades
---

### Post by snorkel on 2004-11-04
Hi,
I downloaded the warty release and I had a hell of a time installing on my MSI K8N Neo with a Athlon64 3200 (32bit mode)
It also failed to correctly install the Nvidia Geforce 6800 GT installed in the PC.
I had to set all that up manually.
Also USB does not work and the system won't shut down properly, I have to hold down the power button.
Previously on this PC I was running Gentoo with a stock 2.6.8 kernel from kernel.org and everything worked fine, I can't imagine why the kernel included with Warty fails at the shutdown and USB.

Has anyone got a board based on the Nivida nforce3 gb250 chipset to work properly?

If I could just fix these two issues I would be totally in love with Ubuntu :-)

Thanks,

Snorkel

---

### Post by snorkel on 2004-11-05
Well,
I seem to have figured this one out, so i will post what I did, maybe it will help others.

For what ever reason the grub menu.lst had acpi=off in the boot parameters, I removed acpi=off and now I my system shuts off automaticly when I select shut down.  Also the USB errors that where poping up during boot are now gone.

Anyone know why the default install puts acpi=off in the grub menu?

Thanks,

Snorkel

---

### Post by Vlammend on 2004-11-06
I have the same motherboard. Everything worked fine from the start with Ubuntu.

---

### Post by jdong on 2004-11-06
The only reason it'd do that is if you put it there when you launched the installer  :---)

---

