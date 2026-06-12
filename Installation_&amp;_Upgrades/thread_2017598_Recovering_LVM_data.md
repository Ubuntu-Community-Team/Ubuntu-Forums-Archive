---
title: "Recovering LVM data"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by derelict888 on 2012-07-05
While upgrading my home server I accidentally selected my 1tb drive in gparted and dropped the partition table on it. The hd was setup with LVM and I need to recover the data on it. I'm pretty confident the data is still there, but because it's an LVM I can't use gparted to try and auto recover the partition tables. When I run pvs -v / pvscan -v or lvscan/lgscan it finds nothing. How can I go about recovering the data? Searching around online hasn't returned any results that have worked for me.

Here is what fdisk & proc show for the 1tb hd;

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1ae7e811

   Device Boot      Start         End      Blocks   Id  System



major minor  #blocks  name

**   8        0  976762584 sda**
   8       16   78149687 sdb
   8       17   73956352 sdb1
   8       18          1 sdb2
   8       21    4190208 sdb5
  11        0    1048575 sr0

I'm afraid to just try and recreate the LVM (PV, LV, LG), any ideas?

---

### Post by darkod on 2012-07-05
Not sure if anyone has tried it with LVM, but testdisk is very good recovering deleted ext4 and ntfs partitions.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You can download and run it from ubuntu live mode. DO NOT boot from that disk any more.

In case testdisk can bring back the lvm partition (physical device), after that the pvscan and vgscan should work fine.

---

### Post by derelict888 on 2012-07-05
Thanks I'll check it out.

---

### Post by derelict888 on 2012-07-06
> **darkod said:**
> Not sure if anyone has tried it with LVM, but testdisk is very good recovering deleted ext4 and ntfs partitions.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You can download and run it from ubuntu live mode. DO NOT boot from that disk any more.

In case testdisk can bring back the lvm partition (physical device), after that the pvscan and vgscan should work fine.

Looks like the file systems supported here are the same as gparted, no love for LVM.

---

### Post by darkod on 2012-07-06
Since you are probably working from live mode, add the lvm2 package first. It might change how testdisk views the disk.
sudo apt-get install lvm2

After that open testdisk.

---

### Post by derelict888 on 2012-07-06
Anybody else have any ideas? All the recovery tools I've looked at do not support LVM and my experience with LVM isn't good enough that I could comfortably recover on my own.

---

### Post by derelict888 on 2012-07-06
> **darkod said:**
> Since you are probably working from live mode, add the lvm2 package first. It might change how testdisk views the disk.
sudo apt-get install lvm2

After that open testdisk.

Thanks for the reply. I actually have 2 HDs, the first is an 80GB which holds the OS. I just put a new copy of 12.04 LTS x64 server on it, I do have lvm2 installed. The other HD, my 1TB drive, is the LVM which holds all my data like ISOs, movies/music/pictures, etc... when I use tools from the lvm2 group, like lvscan/vgscan/pvscan/pvs I get no results. Fdisk shows unpartitioned space.

I guess my question at this point is can I simply recreate the PV & LV & LG and expect it to all magically work again? I do have a copy of my old fstab so I should have the old UUID if it would be any different now.

---

### Post by derelict888 on 2012-07-06
Here is whats from my old fstab (no UUID);
```
#LVM
/dev/Files/files        /var/share      ext2    rw,noatime,auto    0    0
```



This is from an automated backup of an LVM tool;
```
creation_host = "media-server"  # Linux media-server 2.6.32-24-server #43-Ubuntu SMP Thu Sep 16 16:05:42 UTC 2010 x86_64
creation_time = 1341244615      # Mon Jul  2 09:56:55 2012

Files {
        id = "PlhCNp-8ou0-Lprs-9BJJ-KBti-KIHD-fRnBfZ"
        seqno = 6
        status = ["RESIZEABLE", "READ", "WRITE"]
        flags = []
        extent_size = 8192              # 4 Megabytes
        max_lv = 0
        max_pv = 0

        physical_volumes {

                pv0 {
                        id = "iQyM5m-8xEe-6fxg-f3Hc-I53d-RIED-ucPr7Y"
                        device = "/dev/sda1"    # Hint only

                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 1953520002   # 931.511 Gigabytes
                        pe_start = 384
                        pe_count = 238466       # 931.508 Gigabytes
                }
        }

        logical_volumes {

                files {
                        id = "NIHwgG-Fz35-6QQg-1DvC-8VhY-S6u4-kbB9Jc"
                        status = ["READ", "WRITE", "VISIBLE"]
                        flags = []
                        segment_count = 1

                        segment1 {
                                start_extent = 0
                                extent_count = 238464   # 931.5 Gigabytes

                                type = "striped"
                                stripe_count = 1        # linear

                                stripes = [
                                        "pv0", 0
                                ]
                        }
                }
        }
}
```

---

### Post by darkod on 2012-07-06
> **derelict888 said:**
> Thanks for the reply. I actually have 2 HDs, the first is an 80GB which holds the OS. I just put a new copy of 12.04 LTS x64 server on it, I do have lvm2 installed. The other HD, my 1TB drive, is the LVM which holds all my data like ISOs, movies/music/pictures, etc... when I use tools from the lvm2 group, like lvscan/vgscan/pvscan/pvs I get no results. Fdisk shows unpartitioned space.

I guess my question at this point is can I simply recreate the PV & LV & LG and expect it to all magically work again? I do have a copy of my old fstab so I should have the old UUID if it would be any different now.

You said testdisk doesn't seem to recognize LVM, so i thought installing the package might help.

As for pvscan, of course it will not work right now since there is no partition marked as LVM device. The idea was to use testdisk to bring back this partition first, and after that activate the LVM.

Did you try also the deeper search of testdisk?

---

### Post by derelict888 on 2012-07-06
> **darkod said:**
> 
Did you try also the deeper search of testdisk?

I apologize I didn't actually try the tool yet, I just checked for supported file systems. I'm using the tool now and it does find the lost partitions, it hasn't been able to recover them yet. I will keep fiddling with the tool (doing a deep scan currently) and will report back, thanks.

---

### Post by derelict888 on 2012-07-06
```
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
**Analyse cylinder  2950/121600: 02%**


  Linux LVM2               0   1  1 121600 254 63 1953520002
  ext2                     0   7  7 121599 152 24 1953497088
  ext2                     0   7  5 121599 152 22 1953497088
  ext2                     0   7  7 121599 152 24 1953497088
  ext2                     0   7  5 121599 152 22 1953497088
  ext2                     0   7  7 121599 152 24 1953497088
  ext2                     0   7  5 121599 152 22 1953497088
  ext2                     0   7  7 121599 152 24 1953497088
  ext2                     0   7  5 121599 152 22 1953497088
  ext2                     0   7  7 121599 152 24 1953497088
  ext2                     0   7  5 121599 152 22 1953497088
  ext2                     0   7  7 121599 152 24 1953497088
  ext2                     0   7  5 121599 152 22 1953497088
  ext2                     0   7  7 121599 152 24 1953497088
  ext2                     0   7  5 121599 152 22 1953497088
  ext2                     0   7  7 121599 152 24 1953497088
check_FAT: Unusual, only one FAT
check_FAT: Unusual media descriptor (0xf0!=0xf8)
Warning: number of heads/cylinder mismatches 16 (FAT) != 255 (HD)
  FAT16                  547 130 51   555 209 19     133466
  ext2                     0   7  5 121599 152 22 1953497088
  ext2                     0   7  7 121599 152 24 1953497088
  ext2                     0   7  5 121599 152 22 1953497088
  ext2                     0   7  7 121599 152 24 1953497088
Warning: number of heads/cylinder mismatches 64 (FAT) != 255 (HD)
Warning: number of sectors per track mismatches 32 (FAT) != 63 (HD)
  FAT16                 1572 135 51  1574  15 56      24576
  ext2                     0   7  5 121599 152 22 1953497088

```

---

### Post by darkod on 2012-07-06
Was the LVM partition taking the whole disk?

The first entry in this list looks like LVM2 partition taking the whole disk, from cylinder 0 to 121600.

Not sure why there are so many other partitions "detected" and about that error about the number of heads. But it looks like it does detect LVM2 partition.

---

### Post by derelict888 on 2012-07-06
> **darkod said:**
> Was the LVM partition taking the whole disk?
 heads. But it looks like it does detect LVM2 partition.

Yes it was the entire disk. I wasn't able to recover anything though after the deep scan finished. It gave me a list of some garbage and some files, but since the partition type is "unknown" it can't recover the partition table or files.  >_>

---

### Post by derelict888 on 2012-07-09
I quickly tried the photorecovery tool and found that it was recovering some pictures, which is actually my biggest concern. I dont have enough space where I started the restore so I'll have to report on this later but the initial results are promising.:)

---

### Post by aadam12 on 2012-07-28
I'm in a similar situation. I'm running Ubuntu 12.04 64-bit. I have 4 500GB hard drives on LVM.  
dev/sda1 is the OS on ext4,
 dev/sda2 is swap, 
/dev/sda3 /dev/sdb1 /dev/sdc1 /dev/sdd1 are LVM  with a VG called 4drives

/dev/sda3 partition crapped out for some reason and killed the LVM (which is about 99% full)

I can restore the LVM using pvcreate but I cannot seem to restore the data.

Any ideas?

---

