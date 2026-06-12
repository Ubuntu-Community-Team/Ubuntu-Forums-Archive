---
title: "Unable to install Ubuntu 18.04: MODSIGN"
date: 2018-08-16
forum: Installation &amp; Upgrades
---

### Post by mrblacknuel on 2018-08-16
Hi,
When I boot into my USB and I install Ubuntu it shows this message:

[COLOR=#696969]Couldn't get size: 0x800000000000000e
MODSIGN: Couldn't get UEFI db list[/COLOR]

Afterwards, the installation begins normally and once it finishes my computer freezes for 2 minutes and shows the following messages:

[COLOR=#696969]https://imgur.com/a/W3Y7dcB[/COLOR]

I power off the pc and try to run Ubuntu but it doesn't work.

I have a Hp Pavilion Power Laptop 15-cb0xx and I've tried resetting the BIOS configuration and made sure Safe boot was disabled but anything worked. Does someone know how to solve the issue?

---

### Post by jabrilm on 2018-12-07
Have you had any luck with this? I am also getting this error even with Secure Boot disabled.

On my computer, I was able to add [FONT=courier new]noapic noacpi nosplash[/FONT] and got past this error.

---

### Post by mrblacknuel on 2018-12-08
Yes, the problem solved when I added the command 'nomodeset' in the grub line belonging to Ubuntu. 
By this way the system does not load some graphical features and it boots despite the screen freeze of the installation.

---

