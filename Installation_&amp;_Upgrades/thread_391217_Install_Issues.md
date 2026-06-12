---
title: "Install Issues"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by asdfasdf128 on 2007-03-22
Hi, I've tried to install version 6.06 and 6.10 on a completely formatted hard-drive which I plan to use entirely for ubuntu.  The problem is that when I put the CD in and boot from CD it gets to a certian point and then stops and gets to like a dos prompt screen.  After typing ubuntu.exe it opens a program up to set up partition and all, however its in german.  Someone help because I thought this would be a breeze to install.

---

### Post by Kateikyoushi on 2007-03-22
Boot from the cd at the menu press F6 then press E to edit the startupline remove quiet and splash and add these options to the end of the line.

noapic
nolapic
pci=irqroute
pci=noacpi
acpi=off
pci=acpi
framebuffer=false
linux irqpoll

Tell us if you get an error message during the boot.

---

### Post by asdfasdf128 on 2007-03-23
no luck...I get a screen that says:

NWCache R1.02 Disk Cache

Using DPMS DOS Protected Mode Services.

Current options:

/MLX              Program is loaded into conventional and XMS memory using DPMS
/BL=16          Lookahead buffer is in conventional memory, size is in KB
/LEND=ON     Lend memory to other applications- 6646KB available
/DELAY=OFF  Write delay is disabled, caching is write-through

[DR-DOS] A:\

When I do "Dir", there is an option for WWBMU.exe however when i type that in the prompt, its in german. :(

---

### Post by asdfasdf128 on 2007-03-25
any ideas people?

---

### Post by asdfasdf128 on 2007-04-23
bump...still waiting

---

