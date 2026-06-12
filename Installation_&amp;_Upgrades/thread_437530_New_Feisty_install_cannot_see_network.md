---
title: "New Feisty install cannot see network"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by Ron N on 2007-05-08
Both the Feisty Live CD the Feisty installation on my old HP Pavilion cannot see my network. I've tried 3 ethernet cards but none provide network access. I've tried configuring the system with the domain name that all my other systems use. I've tried setting the gateway to 192.168.0.1 (my router) and still no network access. I've spent hours googling for information on the install option called "Install with driver update CD", thinking that maybe I need to install proprietary network card drivers at install time, but I can't find any information about the option. Currently I have a Realtek RTL-8029(AS) in the PC. Before that I tried a D-Link DFE-530TX and it failed to work too. Any suggestions??

---

### Post by Ron N on 2007-05-11
Well, I solved the problem myself :) and here's what I learned in the process.

It looks like the drivers for the Realtek network card, a Cyclone model using the 3c905B chipset, are not available on the Live CD. Similarly for the D-Link DFE-530TX card. I finally tried an old Digital DE450 card with a 21041 chip (of the DECchip DC21x4x family), which requires a driver called tulip. This one gave me network access with the Live CD! OK, so now I know that any network card that uses the tulip driver should allow network access out-of-the-box.

I discovered the lspci command, which lists all the PCI devices in the PC, and found it useful to get manufacturer, model and chipset information for googling purposes. To coax more information I used the -v (verbose) option like this:

lspci -v

This my first Ubuntu install, and I'm very happy.

---

