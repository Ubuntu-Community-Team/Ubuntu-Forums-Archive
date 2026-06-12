---
title: "Ubuntu 6.10 (Edgy Eft) + Abit VP6 with HighPoint ATA-RAID and Sweex S-ATA (SiI3512).."
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by CescoAiel on 2006-12-28
Hi all,

My Intel D865GLC mobo is having issues, so I decided to try to use my
existing Dual PIII Abit VP6 board.

The Mobo has - aside from 2 normal IDE busses - a built in HighPoint
ATA-RAID controller. I also put in an S-ATA controller by Sweex, which is
based on the Silicon Images 3512 controller chip...

I tried installing from the Ubuntu DVD, but it doesn't recognize the extra
controllers.

When I modprobe sata_sil and/or hpt34x, the modules are loaded, but none
of the drives are recognised.

Neither DMESG nor /var/log/syslog show *anything* of the loading of these
modules  ](*,) 

When I move the PATA drive to the standard IDE controller, it is recognized.

When I connect the array of 3 drives to my Intel D865GLC, they are all
recognized, and all works well, except for the fact that the board keeps
shutting down due to Thermal events (that aren't really there) :-? 

Does anybody have experience in installing Edgy Eft (Ubuntu 6.10) on
either HighPoint or SiI3512 based controllers?

Any help would be appreciated!  \\:D/

EDIT:
It's even weirder than I thought!

When I do lspci from the live-DVD command prompt, it returns nothing.

Even requesting the tree gives nothing:
# lspci -v -t 
[0000:00] -

/proc/bus/pci/devices is empty as well

It also doesn't recognise the NIC I put in (first a 3Com 905, then a Realtek 8139), and even manually loading it doesn't help!

So apparently something is wrong with the mobo support, as it seems to be unable to parse the pci bus...

---

