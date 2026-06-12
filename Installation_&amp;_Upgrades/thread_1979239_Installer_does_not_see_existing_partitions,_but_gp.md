---
title: "Installer does not see existing partitions, but gparted does"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by thatguymark on 2012-05-13
I was able to resize and use gparted to create a ext4 and swap partition, but it seems all the distros I tried (I think possibly non-ubuntu ones even) does not see it - and since at this point I want to set up a dual boot I don't want the existing partition to be wiped.

From my search so far it sounds like it might be the installer isn't 100% compatible with the BIOS being in AHCI mode, and some people can get it to work if switched to IDE but I'd rather not do that if I can help it. Since gparted can see things with no problem aren't there anything that can manage to install?

---

### Post by wilee-nilee on 2012-05-13
> **thatguymark said:**
> I was able to resize and use gparted to create a ext4 and swap partition, but it seems all the distros I tried (I think possibly non-ubuntu ones even) does not see it - and since at this point I want to set up a dual boot I don't want the existing partition to be wiped.

From my search so far it sounds like it might be the installer isn't 100% compatible with the BIOS being in AHCI mode, and some people can get it to work if switched to IDE but I'd rather not do that if I can help it. Since gparted can see things with no problem aren't there anything that can manage to install?

How about a screenshot of gparted, ubuntu will use a ide, or ahci.

---

### Post by darkod on 2012-05-13
Sometimes if you have raid meta data on the disk the gparted sees it OK but the installer ignores it thinking it's part of raid array. Has this disk been used in raid earlier?

If that's the issue, and if you ARE NOT running raid right now, you can remove the meta data from live mode in terminal:
sudo dmraid -E -r /dev/sda

That should get it going.

Another reason might be if the disk is dynamic in windows, check that in Disk Management. Ubuntu will not install on dynamic disks and better not to force it. That's MS format and that's why it's ignoring it.

Another option is corruption in the partition table but in that case usually gparted would also have problems reading it correctly.

Check the above two options first and let us know.

---

### Post by thatguymark on 2012-05-13
Well the drive was never used in a RAID and I checked to see if it's dynamic under Windows disk management, nope. 

And actually, I don't even see an option to choose between IDE or AHCI mode in the BIOS.

This IS a cheap Zotac board, when I run Speccy I get:

> Manufacturer	To be filled by O.E.M.
Model	To be filled by O.E.M. (CPU 1)
Version	To Be Filled By O.E.M.
Chipset Vendor	NVIDIA
Chipset Model	MCP61
Chipset Revision	A3
Southbridge Vendor	NVIDIA
Southbridge Model	MCP61
Southbridge Revision	A2

I've never seen those fields not filled out. Anyway, as a workaround I'm thinking I may just put a PATA drive (the one I'm working with is SATA) in there and clone it for the transition, once we can abandon Windows then that entire drive can be used by Linux anyway.

---

