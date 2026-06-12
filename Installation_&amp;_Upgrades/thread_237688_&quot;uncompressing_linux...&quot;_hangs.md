---
title: "&quot;uncompressing linux...&quot; hangs"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by scatyb on 2006-08-16
Well, I haven't found an answer yet in my searches, but perhaps there is one out there.

I just did a server install and it installed fine as far as I can tell.  However, when it goes to reboot, this happens:

uncompressing linux..._

and it just hangs.

I have tried the acpi=off option and disabling acpi in my bios and have even reinstalled, but to no avail.  It is the i386 version on an 800mhz machine with 128mgs of ram.

Any suggestions?

---

### Post by scatyb on 2006-08-17
well, anyone?

the machine is 128mgs pc133
pcchips gfxcel mobo 800mhz proc
onboard video,sound,lan
40gig hd
48x cdrom

and thats about it.

---

### Post by scatyb on 2006-08-18
well after looking into it, it appears to be a kernel issue.

My solution?  install fedora.  Works like a dream.  maybe in a release or two, I'll come back and try  ubuntu server again.

---

### Post by XaRoP on 2006-08-18
I had a similar problem. My motherboard is an ASUS one and it has ATA and SATA alltogether. When I changed from "enhanced" to "compatible" mode (I don't know what's this!) for my IDEs everything started to work. I don't know if this will help...

---

