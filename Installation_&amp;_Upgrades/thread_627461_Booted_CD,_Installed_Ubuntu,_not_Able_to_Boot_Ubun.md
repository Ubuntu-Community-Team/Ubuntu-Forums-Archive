---
title: "Booted CD, Installed Ubuntu, not Able to Boot Ubuntu . . ."
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by IeU on 2007-11-30
Hi Everyone,


i have 3 HDs,
sda Seagate 7.2krpm 160gb ( For Ubuntu )
sdb WD 10krpm 150gb 10k rpm ( Vista Here )
sdc WD 7.2krpm 500gb ( BackUP / Garbage HD )


Vista is already installed and running, i would like to have a dual boot, with grub showing me both systems, defaulted to boot Vista.

I downloaded the latest 64bit Ubuntu, burned it, and booted it, installed ( throu LiveCD ).
The installation went good, no problems at all, but it seems it does not install grub by default, because when it asks to restart the pc, it boots Vista. No Grub or so . . .

I am kind Linux noob, what am i missing here . . .?

---

### Post by logos34 on 2007-11-30
change the bios to boot from one of the other two drives...grub should be on one or the other

---

### Post by IeU on 2007-11-30
i can not set my bios to boot a specific HD.

edit,

i think, i have a solution. i could boot the Ubuntu-CD and there there is an option to "boot a hard disk". I am not sure i can choose which Hard disk to boot. If yes, cool i can boot Ubuntu.
BUT this isn't the solution i was looking for.

I would like while booting my PC, to be prompted with two options "Ubuntu" and "Windows Vista", countdown on 10 seconds and after that booting on default Windows Vista, if no selection was made . . .

any help so i can achieve my objective ?

hehe

thanks ^·^

---

### Post by IeU on 2007-11-30
no1 ?

---

### Post by IeU on 2007-11-30
:/

---

### Post by mozkill on 2007-11-30
i think the solution might be to do the install with only 1 of the hard drives connected.  can you try that and let us know what happens?

---

### Post by meierfra on 2007-11-30
Post the output of

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```
(both l are lowercase L)

---

### Post by IeU on 2007-12-08
> **meierfra said:**
> Post the output of

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```
(both l are lowercase L)

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef38ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   82  Linux swap / Solaris
/dev/sda2   *         244        1459     9767520   83  Linux
/dev/sda3            1460       19457   144568935   83  Linux

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
240 heads, 63 sectors/track, 19381 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcbed35df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19380   146512768+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x909e622d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sde: 1014 MB, 1014497280 bytes
65 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0x32b73a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         953      990704    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(967, 64, 32) logical=(952, 39, 32)
ubuntu@ubuntu:~$ 

```

cat /boot/grub/menu.lst

im on LiveCD, does not seem to be possible from it . . .

---

