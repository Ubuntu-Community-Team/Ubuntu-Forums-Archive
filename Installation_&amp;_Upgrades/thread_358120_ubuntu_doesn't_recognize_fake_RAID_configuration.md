---
title: "ubuntu doesn't recognize fake RAID configuration"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by Exa34 on 2007-02-10
I'm trying to install ubuntu onto my sony ar170g laptop. It has a 2x100GB set up in a RAID configuration with Intel Matrix Storage manager in a fake RAID configuration.

I've tried searching everywhere, and asking in IRC channels but I can't find a solid solution.. The closest that I've gotten to recognizing the fake RAID configuration is when using dmraid (dmraid_1.0.0.rc13-2ubuntu2tormod~dapper_i386.deb). When I install and activate it though, it only displays the volume, but not the separate partitions when i look in /dev/mapper.

            root@ubuntu:~# ls /dev/mapper
            control  isw_dgcefjjebe_Volume 0

If i "cfdisk isw_dgcefjjebe_Volume 0" then it shows all the partitions on my hard drive, and if i type "dmraid -an" it displays 

             root@ubuntu:~# dmraid -an
             RAID set "isw_dgcefjjebe_Volume 01" is not active
             RAID set "isw_dgcefjjebe_Volume 02" is not active
             RAID set "isw_dgcefjjebe_Volume 03" is not active
             RAID set "isw_dgcefjjebe_Volume 04" is not active

Those are my four separate partitions that aren't displayed in /dev/mapper. Does anyone know how I might get this to work properly?

---

### Post by cjpwiss on 2007-02-11
Hello!

I have exactly the same problem as you have and also no solution for it yet :( 

I have 2 160GB Western Digital SATA HDs on my Intel ICH8R with RAID 0. My mainbord is Gigabyte 965P-DS4 (BIOS F7).

As in [this]("http://ubuntuforums.org/showthread.php?t=316182") thread I installed the newest versions of libc6, libsepol, libselinux and devmapper before I installed finally dmraid (same version as you). Then I see my Raid Set in /dev/mapper/, but as in your case only the volume and no partitions. It makes no difference whether I use The AMD64 DVD, the i386 Alternate CD as discribed in the FakeRaidEdgy HowTo or the i386 Live-CD.

When activating the RAID set with dmraid, it gives me the following:
```

ubuntu@ubuntu:~$ sudo dmraid -ay -vv
NOTICE: skipping removable device /dev/sdc
NOTICE: skipping removable device /dev/hdb
NOTICE: skipping removable device /dev/hda
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: isw metadata discovered
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sda: sil metadata discovered
/dev/sda: "sil" and "isw" formats discovered (using isw)!
NOTICE: /dev/sda: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdb: sil metadata discovered
/dev/sdb: "sil" and "isw" formats discovered (using isw)!
NOTICE: /dev/sdb: via     discovering
NOTICE: added /dev/sda to RAID set "isw_ecajbhcfi"
NOTICE: added /dev/sdb to RAID set "isw_ecajbhcfi"
INFO: Activating GROUP RAID set "isw_ecajbhcfi"
NOTICE: discovering partitions on "isw_ecajbhcfi_WD Stripe RAID"
NOTICE: /dev/mapper/isw_ecajbhcfi_WD Stripe RAID: dos     discovering
NOTICE: /dev/mapper/isw_ecajbhcfi_WD Stripe RAID: dos metadata discovered
NOTICE: created partitioned RAID set(s) for /dev/mapper/isw_ecajbhcfi_WD Stripe RAID

```

Next checking /dev/mapper:
```

ubuntu@ubuntu:~$ ls /dev/mapper/
control  isw_ecajbhcfi_WD Stripe RAID

```

and fdisk gives me the following:
```

Command (m for help): p

Disk /dev/mapper/isw_ecajbhcfi_WD Stripe RAID: 320.0 GB, 320079134720 bytes
255 heads, 63 sectors/track, 38914 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                                   Device Boot      Start         End      Block    s   Id  System
/dev/mapper/isw_ecajbhcfi_WD Stripe RAID1   *           1        1306    1049041    3+   7  HPFS/NTFS
/dev/mapper/isw_ecajbhcfi_WD Stripe RAID2            1307       38914   30208626    0    f  W95 Ext'd (LBA)
/dev/mapper/isw_ecajbhcfi_WD Stripe RAID5            1307        6074    3829892    8+   b  W95 FAT32
/dev/mapper/isw_ecajbhcfi_WD Stripe RAID6            6075        6267     155024    1   82  Linux swap / Solaris
/dev/mapper/isw_ecajbhcfi_WD Stripe RAID7            6268       11489    4194568    3+   7  HPFS/NTFS
/dev/mapper/isw_ecajbhcfi_WD Stripe RAID8           11490       19322    6291854    1    7  HPFS/NTFS
/dev/mapper/isw_ecajbhcfi_WD Stripe RAID9           19323       31081    9445413    6    7  HPFS/NTFS
/dev/mapper/isw_ecajbhcfi_WD Stripe RAID10          31082       38914    6291854    1    7  HPFS/NTFS

```

And at last when deactivating the RAID set he shows me every partition:
```

ubuntu@ubuntu:~$ sudo dmraid -an
/dev/sda: "sil" and "isw" formats discovered (using isw)!
/dev/sdb: "sil" and "isw" formats discovered (using isw)!
RAID set "isw_ecajbhcfi_WD Stripe RAID1" is not active
RAID set "isw_ecajbhcfi_WD Stripe RAID5" is not active
RAID set "isw_ecajbhcfi_WD Stripe RAID6" is not active
RAID set "isw_ecajbhcfi_WD Stripe RAID7" is not active
RAID set "isw_ecajbhcfi_WD Stripe RAID8" is not active
RAID set "isw_ecajbhcfi_WD Stripe RAID9" is not active
RAID set "isw_ecajbhcfi_WD Stripe RAID10" is not active

```

What really attract my attention is, that we both have space characters in the names of our RAID volumes.
**Is it possible, that those space characters effect some errors e.g. in libdevmapper?**
Unhappily I can't change the name without deleting the array at all. I really don't want to delete the array, because windows and all my data is already on it!

I really hope, someone can help!

Greets

---

### Post by cjpwiss on 2007-02-13
WOW! I made it!

The problem is really caused by the space characters! I found a way to change my Raid volume name from "WD Stripe Raid" to just "Raid" and now it works fine! I see all the partitions and can mount them!!!

To change the name of an Intel Raid just use the Intel Matrix Storage Manager under Windows!

I hope, it will work for you, too!

---

