---
title: "Problems installing Ubuntu 8.04 - waiting for root file system"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by Thriell on 2008-11-21
I recently installed Ubuntu 8.04 and it refuses to boot.

I've managed to get it (finally!) to tell me that it's hanging up while waiting for the root file system, but, as a clueless newbie, I'm not exactly sure that means what it sounds like it means.

It sounds as though the system can't find my hard disk. To me, that's just nonsense, because it was able to find it well enough to install all the system files in the first place!

I'm working with an older system:

Gigabyte ga-6vtx motherboard
800MB SDRAM
80GB IDE hard drive

PLEASE, can someone help? This has me ready to scream!

---

### Post by eder.apt-get on 2008-11-21
It looks like your system is not finding or mountin /root.
Can you post the results of these two commands?
sudo df -T
sudo fdisk -l <your_partition> (for example, hda)

Maybe you gonna have to run the live CD and choose to fix the previous installation.

---

### Post by Thriell on 2008-11-21
> **eder.apt-get said:**
> It looks like your system is not finding or mountin /root.
Can you post the results of these two commands?
sudo df -T

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
tmpfs        tmpfs      403892     16512    387380   5% /lib/modules/2.6.24-19-generic/volatile
tmpfs        tmpfs      403892     16512    387380   5% /lib/modules/2.6.24-19-generic/volatile
varrun       tmpfs      403892       100    403792   1% /var/run
varlock      tmpfs      403892         0    403892   0% /var/lock
udev         tmpfs      403892        36    403856   1% /dev
devshm       tmpfs      403892        12    403880   1% /dev/shm
tmpfs        tmpfs      403892        16    403876   1% /tmp

> **eder.apt-get said:**
> sudo fdisk -l <your_partition> (for example, hda)


Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e7c4e7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7994    64211773+   7  HPFS/NTFS
/dev/sda2            7995        8006       96390   83  Linux
/dev/sda3            8007        8068      498015   82  Linux swap / Solaris
/dev/sda4            8069        9964    15229620   83  Linux

---

### Post by Thriell on 2008-11-21
FWIW, when I use the LiveCD to run GpartEd on my hard drive, GpartEd shows warning symbols next to every partirion except the swap partition. Clicking on Partition->information after selecting a partition with the warning gets a message about how it couldn't find a valid filesystem superblock (whatever THAT is) and that the filesystem can't be read, or sumsuch nonsense.

If it can't READ the filesystem, how in the name of all that is holy is the install program able to WRITE the system files to the drive?

This is making less and less sense.

...and to think, some people say Windows is confusing...

---

### Post by Thriell on 2008-11-21
Okay, here's a little more info about my problem.

When I booted from the LiveCD just now, it dawned on me that when I clicked "Computer" from the "Places" menu, it showed an SCSI hard drive. I don't have one of those . . . Mine is an (older) IDE drive, specifically, a Maxtor R080L0, according to Windows' Device Manager.

Why would it decide my IDE drive is an SCSI drive and, more importantly, how can I convince it otherwise?

---

### Post by Thriell on 2008-11-21
Bump!

---

### Post by Thriell on 2008-11-22
Somebody?

Anybody?

I've searched the forums and I've not found any help whatsoever.

---

### Post by Thriell on 2008-11-23
[SIZE="5"]So, what does a guy have to do to get a little help around here!?!?!?[/SIZE]

---

