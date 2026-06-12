---
title: "&quot;device for bootloader installation&quot;"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by Hologide on 2010-01-19
I messed this up once and don't want to do it again!!

My partition is on the /dev/sdb hard drive. Where do I want to put the boot loader? Does it have to be the actual Ubuntu partition? Or is it okay to just put it on /dev/sdb?

---

### Post by Hologide on 2010-01-19
By the way, it says

The partition tables of the following devices are changed
SCSI3(0,0,0) (sdb)
The following partitions are going to be formatted
partition #7 of SCSI3(0,0,0) (sdb) as ext4
partition #8 of SCSI3(0,0,0) (sdb) as swap

---

### Post by presence1960 on 2010-01-19
> **Hologide said:**
> I messed this up once and don't want to do it again!!

My partition is on the /dev/sdb hard drive. Where do I want to put the boot loader? Does it have to be the actual Ubuntu partition? Or is it okay to just put it on /dev/sdb?

You have 2 choices:

1. Put GRUB on MBR of the first hard disk that boots in BIOS. I.E. /dev/sda, /dev/sdb, /dev/sdc

2. Put GRUB on /dev/sdb by clicking the advanced button on the Ready to install window (see pic below) and choosing /dev/sdb. This will put GRUB on MBR of sdb. When install is finished reboot without CD and go into BIOS and set sdb as first hard disk to boot in the hard disk boot order. Save changes to CMOS and continue booting.

If you have more than windows or another OS on there already that will change things. I will need more info.

---

### Post by Hologide on 2010-01-19
No, on the hard drive I'm installing on there is not other operating system (other than a failed ubuntu installation).

So I should be fine to select /dev/sdb then? My above post has a bit more info too.

---

### Post by presence1960 on 2010-01-19
> **Hologide said:**
> No, on the hard drive I'm installing on there is not other operating system (other than a failed ubuntu installation).

So I should be fine to select /dev/sdb then? My above post has a bit more info too.

If that is the disk you are installing to then select /dev/sdb by clicking the Advanced button on the Ready to install window. Then when installation is complete & you reboot just make sure sdb is set to be the first hard disk to boot in the hard disk boot order in BIOS.

---

### Post by Hologide on 2010-01-19
Okay then, here goes...
Cheers :)

---

### Post by Hologide on 2010-01-19
Everytihng checks out, thanks!

---

### Post by presence1960 on 2010-01-19
> **Hologide said:**
> Everytihng checks out, thanks!

Glad you got it working. Enjoy Ubuntu.

---

