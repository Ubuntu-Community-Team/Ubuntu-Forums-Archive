---
title: "Dualboot fumble"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by bibbi on 2007-05-04
Hi,

Working on my second install of Ubuntu next to my windows xp (just replaced motherboard, so reinstalled operating systems).

This time round i thought i'd install Ubuntu to the same drive as winXP, to make up the following:

[B]hda: "Backup"

hdc: empty

sda1: "winxp"
sda5: "mydocs"
sda6: /boot
sda7: /
sda8: /swap

sdb: "media"
[/B]
Winxp was installed first, then i created te **/boot**, ** / ** and **/swap** partitions and installed Ubuntu. During the install i pointed Ubuntu to the appropriate partitions and told the boot loader to sit in /dev/sda6 so my MBR would remain intact (had trouble in past messing with my mbr). This is all following the steps on the pages of:

[COLOR="Blue"][http://www.vsubhash.com/writeups/multiboot_os.asp](http://www.vsubhash.com/writeups/multiboot_os.asp)[/COLOR]
and
[COLOR="Blue"][http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)[/COLOR]

So, after installing Ubuntu i made a copy of the boot sector from /boot using the command:
**dd if=/dev/sda6 of=/media/BACKUP/linux.bin bs=512 count=1**
and altered the boot.ini from winXP the add linux.bin to the startup options.

THE PROBLEM:
boot.ini contains the option to boot the boot sector of Ubuntu (which was copied to the c: drive, ie /dev/sda1), but it gave me Grub error 15, partition not found.

My guess was that Grub must be looking for the wrong partition or possible even the wrong drive in menu.lst.
I installed ext2/3 support under winXP and altered menu.lst as follows:

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)
```
used to be: # groot=(hd2,5)

and the kernel:
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=83ab30a1-c54f-4535-bf91-36170f401cf6 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault
```
used to be: root		(hd2,5)

The file "device.map" in /grub remains untouched:
```
(hd0)	/dev/hda
(hd1)	/dev/hdc
(hd2)	/dev/sda
(hd3)	/dev/sdb

```

On reboot, the ntldr presents me with the boot.ini options:
1 winXp
2 Ubuntu

on selecting Ubuntu i now do get to the startup screen of Ubuntu, with the logo and the progress bar. Unfortunately the progress bar goes nowhere and harddisk activity stops there!

My thought is that i am on the right track, by pointing grub to hd(0) instead of hd(2) in menu.lst, because the loading screen shows instead of a Grub error. But what i don't understand is why "device.map" shows /dev/sda to be hd(2).

Any help on fixing this:
***1 possibly edditing references of grub or the Ubuntu boot process to correct partitions***
**or**
***2 installing Grub to the mbr for dualboot***

Help very much appreciated!

---

### Post by bibbi on 2007-05-04
...oh yes. My mbr is still in place, so I can still boot winXP and i have the Ubuntu liveCD.

B

---

### Post by bibbi on 2007-05-04
.. or if more info is required, just ask ;-)

---

### Post by bibbi on 2007-05-06
got it working.

- Booted with the Live CD.
- terminal, 'sudo grub-install' pointing towards the /boot partition for --root-directory option and pointing towards floppy for --file option
- the floppy didn't work as a boot medium ("Grub GEOM Error")
- but booting windows mbr, with Ubuntu added to the boot.ini did work!

---

