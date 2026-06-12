---
title: "First IDE drive is incorrectly detected most of the time"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by sturreal on 2008-01-02
I've just installed 7.10 server on my server machine and its intermittently booting, I say that just because mainly it fails.

I'm getting the following error "ALERT! /dev/hde3 does not exist. dropping to a shell!" for some reason my first IDE hard drive is detected as hde by the installer. Most of the time /dev/hde can't be found; however it finds the first drive as /dev/hda when booting and not /dev/hde and I've no idea why or how its doing this.

The system is a dual P3 1GHz on a gigabyte GA-6VTXD which has a VIA Apollo chipset. I have 2 hard drives on the primary IDE channel, I also have an ALI sata raid card with 2 SATA hard drives attached.

---

### Post by Pumalite on 2008-01-02
Post:
blkid
cat /boot/grub/menu.lst
cat /etc/fstab
How are your drives detected in BIOS?

---

### Post by sturreal on 2008-01-02
Ah thats the next problem grub wasn't install I installed lilo as grub wouldn't install. The same goes for blkid I can insert a live cd and do it but then the drive is detected as /dev/hda which doesn't really help.

Here is a copy of my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde3
UUID=f2957c41-ec66-454d-8f1c-24213ef0dc40 /               xfs     defaults        0       1
# /dev/hde1
UUID=dec66680-829c-4f5b-96fc-f82f141422bd /boot           ext3    defaults        0       2
# /dev/hde4
UUID=c55b90ce-ea94-47c1-8a08-fb1ddd379b56 /home           xfs     defaults        0       2
# /dev/hde2
UUID=38466072-4cc7-48c9-9839-4610f195b61e none            swap    sw              0       0
/dev/hdg        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

The drives aren't being auto detected, all the data about them is saved in the cmos.

---

### Post by Pumalite on 2008-01-02
Boot your Live CD. At the Terminal:
sudo mkdir /media/hde
sudo mount -t ext3 /dev/hde /media/hde
Now from that drive, post:
blkid
sudo fdisk -lu
cat /etc/fstab

---

### Post by sturreal on 2008-01-02
Output from blkid note that the live cd has detected the first ide drive as hda
```

/dev/hda1: UUID="dec66680-829c-4f5b-96fc-f82f141422bd" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda2: UUID="38466072-4cc7-48c9-9839-4610f195b61e" TYPE="swap"
/dev/hda3: UUID="f2957c41-ec66-454d-8f1c-24213ef0dc40" TYPE="xfs"
/dev/hda4: UUID="c55b90ce-ea94-47c1-8a08-fb1ddd379b56" TYPE="xfs"
/dev/evms/hda1: UUID="dec66680-829c-4f5b-96fc-f82f141422bd" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hda2: UUID="38466072-4cc7-48c9-9839-4610f195b61e" TYPE="swap"
/dev/evms/hda3: UUID="f2957c41-ec66-454d-8f1c-24213ef0dc40" TYPE="xfs"
/dev/evms/hda4: UUID="c55b90ce-ea94-47c1-8a08-fb1ddd379b56" TYPE="xfs"

```

Output from fdisk -lu
```

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63      257039      128488+  83  Linux
/dev/hda2          257040     4257224     2000092+  82  Linux swap / Solaris
/dev/hda3         4257225    53078759    24410767+  83  Linux
/dev/hda4        53078760   160826714    53873977+  83  Linux

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sdb doesn't contain a valid partition table

```

Output from cat /etc/fstab from the installed ubuntu
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde3
UUID=f2957c41-ec66-454d-8f1c-24213ef0dc40 /               xfs     defaults   0       1
# /dev/hde1
UUID=dec66680-829c-4f5b-96fc-f82f141422bd /boot           ext3    defaults   0       2
# /dev/hde4
UUID=c55b90ce-ea94-47c1-8a08-fb1ddd379b56 /home           xfs     defaults   0       2
# /dev/hde2
UUID=38466072-4cc7-48c9-9839-4610f195b61e none            swap    sw   0       0
/dev/hdg        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by Pumalite on 2008-01-03
What is this:

'Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sdb doesn't contain a valid partition table'

---

### Post by sturreal on 2008-01-03
After much frustration, I ripped out all the of hard drives apart from the primary master and the secondary master (cdrom drive)

The machine has an SATA raid card with an onboard IDE channel too, after removing that i found the drives were detected properly. It seems that my motherboard sees to fit to boot the pci ide channel first and then the seconary followed by the primary onboard ide channel, which is why in the kernel doesn't know where to find / There must be some sort of bios setting for or its general idiocy on gigabytes part.

Sorry to have gone through all of that when it was simple remove card and reinstall, What I still don't get is why it sometimes boots them in the right order and more often than not the wrong order, thats still a boggle.

I know /dev/sdb doesn't have a partition table, thats because i haven't given it one yet, it will be part of a raid mirror with /dev/sda once i've set up my system :)

---

### Post by Pumalite on 2008-01-03
I'm glad you got it working. Good luck with Raids. Another headache.

---

### Post by sturreal on 2008-01-04
> **Pumalite said:**
> I'm glad you got it working. Good luck with Raids. Another headache.

Yeah I can know about that one, its a pitty that linux doesn't like bios software raid, but hey i'm sure i'll sort it :)

---

