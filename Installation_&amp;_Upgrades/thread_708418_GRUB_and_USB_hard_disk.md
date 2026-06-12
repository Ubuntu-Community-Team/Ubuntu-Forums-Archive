---
title: "GRUB and USB hard disk"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by T_Beermonster on 2008-02-26
I'm finding that i get various Grub errors when installing Xubuntu 7.10 to an external USB disk.

I have managed to muddle through the various error2s and error 14s and now find myself at the encouraging stage of error 17.
The forums include a wealth of information on error 17 and it seems very likely that the problem can be resolved by editing grubs device.map and reinstalling grub.

Unfortunately I find that the device map looks like this:
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

now I can change round dev/sda to be (hd1) easily enough, the problem lies with what to put as (hd0). Now that may sound silly because obviously it should be dev/sdb. except that the USB hard drive doesn't always show up as sdb. It seems to be fairly randomly assigned either sdb or sdf if booting with my internal drive attached or if I disconnect the internal drive it is assigned either sda or sde.

Is there some way to tie the hd0 to a UUID or device label rather than the movable feast of /dev/sd* ?

---

### Post by dstew on 2008-02-26
Grub is a fairly capable program, but it is dependent on the BIOS detecting drives during its boot phase, so it does not use UUIDs to designate disks, only BIOS numbers. That is a cause of much confusion, because a BIOS can change how it enumerates disks depending on whether a disk is plugged in or not, or if a USB drive is plugged in or not, or if a disk goes from Master to Slave, or if the BIOS boot order is changed.

It is important to install grub into a system that has a stable disk arrangement. If you want to boot from an external disk, you have to set up your system so that the BIOS will boot that drive before the HDD if it is present, and you have to install grub onto the external drive only, *while the BIOS is in that configuration*, so the disk enumeration is correct. Unfortunately, there is a catch-22: if the BIOS is set to boot from the external drive, but the external drive is not bootable, as it is before Xubuntu is installed, then the enumeration might not be the same as when it it bootable! It depends on the BIOS.

Usually, you can get it to work using educated guesswork as to the correct grub disk names. If your BIOS cannot boot a USB drive (which is often the case) you either have to install grub stage 1 on the internal hard disk, or boot the USB partition from a grub floppy or CD-ROM.> it seems very likely that the problem can be resolved by editing grubs device.map and reinstalling grubThat is unlikely. The device.map is an issue only when grub is installed properly, but the kernel selection is not working right. If grub is not installed properly, you will get no menu, but still get an error. Usually the error has not explanation. If you get a menu, and get an error when you pick a kernel to load, that is only a configuration error, not an installation error.

So, exactly what happens when you boot? Do you see the grub menu?

---

