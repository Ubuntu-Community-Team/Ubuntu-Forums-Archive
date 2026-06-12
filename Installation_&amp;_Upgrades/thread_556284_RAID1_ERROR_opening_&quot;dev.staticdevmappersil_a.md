---
title: "RAID1: ERROR: opening &quot;/dev/.static/dev/mapper/sil_ahajcfcefgcj&quot;"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by takeawaydave on 2007-09-21
I am working with:
```

    00:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
```


with 2x 500gb RAID1 SATA hd's.

I have installed:

   ```
 root@denali:/usr/share/doc/dmraid# dmraid --version
    dmraid version:         1.0.0.rc13 (2006.10.11)
    dmraid library version: 1.0.0.rc13 (2006.10.11)
    device-mapper version:  4.11.0

```

onto:

```
    root@denali:/usr/share/doc/dmraid# uname -a
    Linux denali 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686 GNU/Linux
```

and get the following:

```
    root@denali:/usr/share/doc/dmraid# dmraid -tay
    sil_ahajcfcefgcj: 0 976771120 mirror core 2 131072 nosync 2 /dev/sda 0 /dev/sdb 0
    ERROR: opening "/dev/.static/dev/mapper/sil_ahajcfcefgcj"
```


Is there any advice anyone can give me as to how to tell if or whether this RAID1 setup can work/is working?

How do I overcome this error?

I can mount the partitions that I have created and run parted for them:

```
(parted) print all

Disk /dev/hdc: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  98.7MB  98.7MB  primary  ext2
 2      98.7MB  35.0GB  34.9GB  primary  ext3
 3      35.0GB  75.0GB  40.0GB  primary  ext3
 4      75.0GB  80.0GB  5001MB  primary  ext3



Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  31.5GB  31.5GB  primary  ext3         raid
 2      31.5GB  94.4GB  62.9GB  primary  ext3         raid
 3      94.4GB  500GB   406GB   primary  ext3         raid



Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  31.5GB  31.5GB  primary  ext3         raid
 2      31.5GB  94.4GB  62.9GB  primary  ext3         raid
 3      94.4GB  500GB   406GB   primary  ext3         raid



Disk /dev/mapper/sil_ahajcfcefgcj3: 406GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End    Size   File system  Flags
 1      0.00kB  406GB  406GB  ext3



Disk /dev/mapper/sil_ahajcfcefgcj2: 62.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End     Size    File system  Flags
 1      0.00kB  62.9GB  62.9GB  ext3



Disk /dev/mapper/sil_ahajcfcefgcj1: 31.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End     Size    File system  Flags
 1      0.00kB  31.5GB  31.5GB  ext3



Disk /dev/mapper/sil_ahajcfcefgcj: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  31.5GB  31.5GB  primary  ext3         raid
 2      31.5GB  94.4GB  62.9GB  primary  ext3         raid
 3      94.4GB  500GB   406GB   primary  ext3         raid



```


What I've no idea about though is the error above:

```
    root@denali:/usr/share/doc/dmraid# dmraid -tay
    sil_ahajcfcefgcj: 0 976771120 mirror core 2 131072 nosync 2 /dev/sda 0 /dev/sdb 0
    ERROR: opening "/dev/.static/dev/mapper/sil_ahajcfcefgcj"
```

---

### Post by takeawaydave on 2007-09-21
I have rebuilt the array and now get the following output:


```
oot@denali:~# dmraid -s
*** Active Set
name   : sil_ahajcfcefgcj
size   : 976771120
stride : 0
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
```

```
root@denali:~# dmraid -r
/dev/sda: sil, "sil_ahajcfcefgcj", mirror, ok, 976771120 sectors, data@ 0
/dev/sdb: sil, "sil_ahajcfcefgcj", mirror, ok, 976771120 sectors, data@ 0
```

```
root@denali:~# dmraid -b
/dev/hdc:    156301488 total, "DWW-AME8725249"
/dev/sda:    976773168 total, "WD-WCAPW4014296"
/dev/sdb:    976773168 total, "WD-WCAPW4399790"
```

```
root@denali:~# dmraid -tay
sil_ahajcfcefgcj: 0 976771120 mirror core 2 131072 **nosync **2 /dev/sda 0 /dev/sdb 0
sil_ahajcfcefgcj1: 0 62508852 linear /dev/.static/dev/mapper/sil_ahajcfcefgcj 63
sil_ahajcfcefgcj2: 0 101578995 linear /dev/.static/dev/mapper/sil_ahajcfcefgcj 62508915
sil_ahajcfcefgcj3: 0 812680155 linear /dev/.static/dev/mapper/sil_ahajcfcefgcj 164087910
root@denali:~#

```

Is the highlighted nosync normal - or a problem?

Is there anyone that can confirmwhether or not thes is working correctly?

Anybody with dmraid knowledge out there?

---

### Post by takeawaydave on 2007-09-22
Any one there before I give up?

---

