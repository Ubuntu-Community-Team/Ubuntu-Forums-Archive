---
title: "Problem booting from hard drive without SBM boot floppy"
date: 2005-03-24
forum: Installation &amp; Upgrades
---

### Post by packardbio on 2005-03-24
I recently got Hoary working on an old low memory Dell PC (P133, 48M RAM, hda=1.6G, hdb=8G, 4xCDROM, Number 9 Motion 771 video w/ 2M VRAM (S3 968 chip)). Partitions as follows:

hda (Maxtor 1.6G):
     primary "/boot" ext3  (48M)  bootable
     primary "swap"          (128M)
     [free]                         (1.4G)

hdb (WD 8G):
     primary "/"        ext3  (3.0G)  bootable
     primary "swap"          (128M)
     [free]                         (4.8G)

I followed the mini-RAM HOWTO, using "server" at the boot prompt instead of "custom" (there's no "custom" option in Hoary evidently). I couldn't boot from the CD-ROM drive directly so I made a boot floppy with SBM (Smart Boot Manager) and chose "CD-ROM" when it booted from the floppy.

Everything installed fine and I wound up with a nice text-mode system to play with.

There's a point in the install process when the installer asks you to remove any disks (I removed both the floppy and the CD) and then it will reboot itself and continue the installation. The system rebooted fine directly from the hard drive during this step without the boot floppy or the CD-ROM inserted. 

But since then, I haven't been able to boot from the hard drive without having the boot floppy in. The system goes through the power on self test as follows: init video card, perform memory check, recognize and initialize each disk (hda, hdb, CDROM then floppy), then it will hang and do nothing. If I put the boot floppy in and reboot, I'll get the SBM from the floppy, choose to boot from HD0 and everything will work fine with GRUB loading up from the hard drive and Ubuntu starting justthe way it should.

Any ideas anyone? Thanks in advance.

---

### Post by packardbio on 2005-03-29
I can get this to boot from the hard disk  if I change the BIOS boot sequence from "Diskette First" to "Hard Disk Only". I would consider this a work around until I figure out why it's not going to the hard disk after detecting nothing in the floppy drive. It's puzzling, since I've gotten other distros (Fedora Core 1, Slackware & Debian) to boot from the hard drve without needing to disable booting from the floppy (using both LILO & GRUB).

If any of you have come across this, please let me know.

Cheers!

---

