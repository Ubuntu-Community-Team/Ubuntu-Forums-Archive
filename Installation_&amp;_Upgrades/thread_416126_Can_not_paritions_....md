---
title: "Can not paritions ..."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by A.I. BOT on 2007-04-20
I have tried everything. Use largest free space, I'v manualy edited my paritions and tried. Nothing works :(

I get an error when I click "Install" after selecting the partition options ...
> The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.

Thanks.

---

### Post by K.Mandla on 2007-04-20
That kind of error kind of scares me; is there any possibility your drive is failing?

Are you trying to dual boot by chance? If not, I would suggest using a disk-blanking utility like [Killdisk]("http://www.killdisk.com") to completely erase the drive, and see if that helps. It's possible you have some old partition information on there that's confusing the installer; blanking the drive might be helpful.

---

### Post by A.I. BOT on 2007-04-20
Yeah I managed to get the hd partitions deleted but somehow grub is still there so Ill try kill disk and report back if that doesent work ill "shred -vfz -n 100 /dev/sda" :P. Thanks.

---

### Post by A.I. BOT on 2007-04-20
Solved. Shredding with 1 pass worked.

---

### Post by K.Mandla on 2007-04-20
Excellent.

---

