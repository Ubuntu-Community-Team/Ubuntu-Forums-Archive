---
title: "Feisty Fawn installation woes, please help!"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by PolarisNexus on 2007-05-05
Hello, Iam very stumped on this problem, and I have tried many things to get this to work.

I have successfully installed Ubuntu Desktop 7.04 on my Core 2 Duo/ Intel P965 setup back at the office, and being rather satisified with the OS in general, I decided to proceed with the install at home.

However, when I try and install Ubuntu off the disc, it takes a very long time - and props up with a heap of

'buffer I/O error drive fd0 logical block 0'
'atax.00 xfermode err_mask 0x40'

type error messages... And when it finally loads up the live session, the mouse is EXTREMELY slow, and the OS seems very sluggish in general. I try to install it to my hard drives, but only my IDE/PATA drive shows up, and not my SATA ones. I guess thats because of those error messages...

I have tried to set ACPI off in the bios, and with the 'acpi=off noapic nolapic' command lines during installation, to no avail. I consulted the Core 2 Duo issues thread I found somewhere, and it says my motherboard has issues with stability on an older version of Ubuntu, but with the OS only choking after installation, and not during.

I feel this is a bit odd, as the machine in my office at university had very similar specs to my home one. Perhaps its just the motherboard.

Foxconn P9657AA -- Core 2 Duo 6400 -- 2 x 1GB DDR2-800 dual channel ram -- 2 x 250GiB sata -- 1 x 250GiG pata -- nVidia 7900GS.

There are the specs of my home machine. I am trying to install version 7.04 (Desktop).  I could install it to my Pata drive, but i'm sure that if it doesn't recognise my sata drives in the installation, it wont be able to recognise in the installed OS.:( :( 

Any help would be MUCH appreciated. I'm getting sick of Windows, and I've fallen in love with ubuntu already. Thank you!

---

### Post by zek725 on 2007-05-06
ensure that the cd has no defects.

I had a similar problem with that when installing from scratched so I switched cds twice and it worked. 

Upgrading from edgy:
To eliminate cdrom hardware error, i've [mounted the .iso as a virtual cd ]("http://www.mail-archive.com/linux-users@it.canterbury.ac.nz/msg45922.html")then upgraded from edgy.

---

