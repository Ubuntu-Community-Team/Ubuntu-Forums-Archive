---
title: "Breezy does not work with ICP Vortex Raid Controller GDT6538RD"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by sawi on 2005-11-23
@1st I would say hello to the community. Ubuntu makes my life a little bit easer in the last year.

But now I have the first problem with an installation on a server. 

I have a server with a  Dual-PIII 450 CPU, Mainboard Asus P2B-DS Bios 1011, an ATI Rage 8MB, 
512 MB SD-RAM - Memory, a GDT6538RD Controller with 4x IBM DNES 309170W disks in a RAID 5 array and a Adaptec Controller AHA-7890 with a Toshiba 6401 CD-ROM and a HP 1537A Streamer connected.

This system runs perfectely with Hoary Hedgehog until I have upgedated to Breezy Badger. After a reboot the system did not start.
After "Loading Kernel.." the system hangs with:

ALERT! /dev/ida/sda1 does not exist. Dropping into shell.

I've assumed that something goes wrong with the update and have reinstalled the system. But after a reboot the system hangs again.

After that I have reinstalled the system again with Hoary and made the update again. As expected the system did not boot. At least not with the kernel 2.6.12-9-386 (also not in recovery mode). With kernel 2.6.10-5-386 by Hoary the system did boot.

Does anyone have an idea whats goes wrong?

Thx!

Frank

---

