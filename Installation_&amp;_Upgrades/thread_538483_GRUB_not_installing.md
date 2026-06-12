---
title: "GRUB not installing"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by AaronFinn on 2007-08-30
Hi!

I tried installing Ubuntu feisty from live-CD, and it goes perfectly smoothly... Until the very end of installation, when it is time to install GRUB. I got error about grub-install (hd0) not being able to execute. So now i have linux which i cannot boot.

When i boot without live-cd, i get the following error :
Grub loading stage 1.5...

Error 17: Cannot mount selected partition.

If i boot to console with live CD, and try to install grub by following:
sudo su
grub
root (hd0,5)
setup (hd0)

i get error 17 again. My ubuntu is installed to hda6.

My partitions are following:
/dev/sda1 is NTFS, my windows XP installation
/dev/sda2 is extended partition
      /dev/sda5 is NTFS, my windows data
      /dev/sda6 is EXT3, my ubuntu installation
      /dev/sda7 is EXT3, my ubuntu data
/dev/sdb1 is FAT32, for both linux and windows
/dev/sdb2 is extended partition
      /dev/sdb5 is SWAP, for linux

Strange thing is, that my previous kubuntu installation, which i screwed up, listed those as hd, not sd. And they are all IDE-disks, not SATA or SCSI. Maybe that's the problem?

I even tried changing sdb to primary boot disk from BIOS, and trying following:
sudo su
grub
root (hd0,5)
setup (hd1)

and Error 17 again.

Grub is latest version. I have no idea why GRUB cannot mount my disks... Any advice anyone? thanks:)

---

### Post by merlinus on 2007-08-30
You might try supergrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

More info here:

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

-merlin

---

### Post by AaronFinn on 2007-08-30
SuperGRUB is no good... still error 17. Maybe i format root as EXT2, it could help... maybe

---

### Post by Pumalite on 2007-08-30
Try this: [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

