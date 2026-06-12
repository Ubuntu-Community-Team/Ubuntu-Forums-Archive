---
title: "How to backup to another HDD?"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by cci[RR]us on 2011-05-03
Hi,

I would like to backup my entire Ubuntu installation (/boot, swap and /) at **/dev/sda (4GB)** to **/dev/sdb (10GB)**.

I recreated the exact partitions on /dev/sdb, formatted and cp -rp all the files over.

For /boot, I used
```
dd if=/dev/sda1 of=/dev/sdb1
```

It didn't boot successfully as the system kept rebooting. I then tried to install grub onto the MBR and boot partition (mounted at /mnt/tempboot).
```
grub-install --force --no-floppy --root-directory=/mnt/tempboot /dev/sdb
```
But I get an error:
```
grub-setup: warn: Your embedding area is unusually small. core.img won't fit in it.
```
I read up more on this [here](http://ubuntuforums.org/showthread.php?t=1528529).

Anyhow, since I forced grub-install, I believe the grub is installed. I rebooted the system and I get a grub prompt:
```
grub>
```
I am stuck here. Grub seems to not find my grub.cfg but it is present.:confused:

Can someone please help me? :(

---

### Post by lmarmisa on 2011-05-03
Sorry. I was wrong. I thought you cloned the entire hard drive but you tried to clone only the first partition.

I think your procedure is wrong. The command dd is nonsense.

Try to use Clonezilla Live for making a complete backup of your hard drive.

[http://clonezilla.org/](http://clonezilla.org/)

---

