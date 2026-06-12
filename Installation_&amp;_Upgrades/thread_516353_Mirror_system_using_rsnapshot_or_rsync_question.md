---
title: "Mirror system using rsnapshot or rsync question"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by dumpster25 on 2007-08-03
I got two disks on this system. One SAS-drive and one SATA-drive. Both are mounted and working. The SAS-drive is the system disk. While the SATA-drive acts as a storage backupdisk.

I've created a partition on the SATAdrive as big as the SAS-drive and I'm rsyncing the contents of the / of the SASdisk to the SATA partition. My question now is. Is it possible to boot from the SATAdrive if the SAS drive fails by booting in single user mode and doing changes on /fstab in the new partition and with grubinstall?

Could anybody give me any pointers on how to do this please? Thanks

---

### Post by talby on 2007-08-03
> **dumpster25 said:**
> My question now is. Is it possible to boot from the SATAdrive if the SAS drive fails by booting in single user mode and doing changes on /fstab in the new partition and with grubinstall?

Well if the SAS drive fails, it will be difficult to boot into single-user mode :)

here are a couple of ideas:

**1 - clone the bootloader from your current disk to the backup disk**
```
#assume /dev/sda is live disk, /dev/sdb is backup disk
sudo dd if=/dev/sda of=/dev/sdb bs=446 count=1
```
The first 512 bytes of the hdd is bootloader+partition table so the first 446 bytes is bootloader only.  If you remove the SAS drive and the SATA drive becomes /dev/sda then you will not have to worry about /etc/fstab changes.  I know it works if you have similiar disks but not sure if it will in this case since you have SAS controller for primary and SATA controller, the bootloader may get confused.  If this is the case...

**2 - reinstall grub using rescue mode**
There is a good example of this [here (@users.bigpond.net.au]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")), you will have to remove the current disk (and possibly change BIOS to boot up from the sata disk in boot order) then go through the motions.  It also describes backing up the bootloader(MBR) info using dd to a file.

Good luck!

---

### Post by dumpster25 on 2007-08-03
> **talby said:**
> Well if the SAS drive fails, it will be difficult to boot into single-user mode :)

Hehe I know. Well i meant actually booting with a rescue cd.

Thanks for the input I'll check on it! :-)

---

