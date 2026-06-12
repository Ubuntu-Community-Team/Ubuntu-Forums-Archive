---
title: "Boot problems"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by eolsen on 2007-10-25
I just installed Ubuntu, however, I am having trouble booting. The computer I installed it on, is a little old and slow, so I actually plugged in the hard drive to my new computer to do the install and such. Worked fine on that computer, but now when I boot to it on the older computer, this is what happens. The Ubuntu splash screen comes up, and the loading bar loads relatively quickly. After that, the following appears:

*Starting anac(h)ronistic cron anaeron [OK]
*Starting deferred execution scheduler outd [OK]
*Starting periodic command scheduler crond [OK]
*Checking Battery State... [OK]
*Running local boot scripts (/etc/rc.local) [OK]

And then that's as far as it gets :/

---

### Post by Shazaam on 2007-10-25
Looks like your hard drive numbering is off. Does the pc have a cd drive?
Boot up your Ubuntu livecd, open terminal (Applications>Accessories>Terminal) and enter this command and post the output here...
```
sudo fdisk -lu
```

You will probably end up editing fstab with the right numbers.

---

### Post by eolsen on 2007-10-25
Ok, so for whatever reason, my computer doesn't detect the install disk. But I rand that code on my new computer with the HDD with Ubuntu and here is the output:

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000c7a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   114880814    57440376    7  HPFS/NTFS
/dev/sda2       114880815   229408199    57263692+  83  Linux
/dev/sda3       229408200   234372284     2482042+   5  Extended
/dev/sda5       229408263   234372284     2482011   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0017ab60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   240107489   120053713+   7  HPFS/NTFS

---

