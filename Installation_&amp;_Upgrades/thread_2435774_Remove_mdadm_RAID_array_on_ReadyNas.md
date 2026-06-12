---
title: "Remove mdadm RAID array on ReadyNas"
date: 2020-01-25
forum: Installation &amp; Upgrades
---

### Post by IanVaughan on 2020-01-25
This is actually a ReadyNas102 linux box using Debian GNU/Linux 8.

I accidentally switched my two drives into a raid array via the web interface, and now cannot get the commands right to undo this via a SSH term.

As suggested in other posts, I umount and "mdadm --stop", but I cannot do that for md0 as / is mounted there, when I remove that I have unmounted the system (I think)

How can I return these two drives as non-raid normal seperate mounted drives?

[HR][/HR]

Details ::

```
# mount
/dev/md0 on / type ext4 (rw,noatime,nodiratime,data=ordered)
/dev/md0 on /run/nfs4/home type ext4 (rw,noatime,nodiratime,data=ordered)
/dev/md127 on /data type btrfs (rw,noatime,nodiratime,nodatasum,nospace_cache,subvolid=5,subvol=/)
... (plus others) ...
```

```
# lsblk -f
NAME      FSTYPE            LABEL           UUID                                 MOUNTPOINT
sda
&#9500;&#9472;sda1    linux_raid_member 2fe53b89:0      7f32aec1-c2b2-1276-5cf8-c984fa945b56
&#9474; &#9492;&#9472;md0   ext4              2fe53b89:root   ccb2bb10-faf0-4f33-9b05-79232317bfb0 /
&#9500;&#9472;sda2    linux_raid_member 2fe53b89:1      953dd93b-7743-3d27-371b-b09858f73957
&#9474; &#9492;&#9472;md1   swap              swap            6b2e6fb6-6d63-44c0-a340-73a81b78bdbd [SWAP]
&#9492;&#9472;sda3    linux_raid_member 2fe53b89:data-0 5511f0ec-9950-a668-9a4e-f5864fab40fb
  &#9492;&#9472;md127 btrfs             2fe53b89:data   6fb18eb7-d6f8-49ae-a8bc-8d16c193fbcd /data
sdb
&#9500;&#9472;sdb1    linux_raid_member 2fe53b89:0      7f32aec1-c2b2-1276-5cf8-c984fa945b56
&#9474; &#9492;&#9472;md0   ext4              2fe53b89:root   ccb2bb10-faf0-4f33-9b05-79232317bfb0 /
&#9500;&#9472;sdb2    linux_raid_member 2fe53b89:1      953dd93b-7743-3d27-371b-b09858f73957
&#9474; &#9492;&#9472;md1   swap              swap            6b2e6fb6-6d63-44c0-a340-73a81b78bdbd [SWAP]
&#9492;&#9472;sdb3    linux_raid_member 2fe53b89:data-0 5511f0ec-9950-a668-9a4e-f5864fab40fb
  &#9492;&#9472;md127 btrfs             2fe53b89:data   6fb18eb7-d6f8-49ae-a8bc-8d16c193fbcd /data

```

```
root@nas:~# blkid
/dev/md/data-0: LABEL="2fe53b89:data" UUID="6fb18eb7-d6f8-49ae-a8bc-8d16c193fbcd" UUID_SUB="d1c3b76c-683d-4086-b9b3-2df2d15fcbc7" TYPE="btrfs"
/dev/md0: LABEL="2fe53b89:root" UUID="ccb2bb10-faf0-4f33-9b05-79232317bfb0" TYPE="ext4"
/dev/md1: LABEL="swap" UUID="6b2e6fb6-6d63-44c0-a340-73a81b78bdbd" TYPE="swap"
/dev/sda1: UUID="7f32aec1-c2b2-1276-5cf8-c984fa945b56" UUID_SUB="effb7efd-62d6-7031-9ac7-1d7bc7c846b6" LABEL="2fe53b89:0" TYPE="linux_raid_member" PARTUUID="11ab9914-6c03-427e-b679-e14150f4c305"
/dev/sda2: UUID="953dd93b-7743-3d27-371b-b09858f73957" UUID_SUB="1d830e0a-eada-1288-5866-e324df77e173" LABEL="2fe53b89:1" TYPE="linux_raid_member" PARTUUID="d76ed9f3-64e6-4bed-9dfe-607199afd703"
/dev/sda3: UUID="5511f0ec-9950-a668-9a4e-f5864fab40fb" UUID_SUB="57bab088-6143-fa3f-3297-727c730c4388" LABEL="2fe53b89:data-0" TYPE="linux_raid_member" PARTUUID="e701e06c-999f-4f05-983e-9dc487f18fc8"
/dev/sdb1: UUID="7f32aec1-c2b2-1276-5cf8-c984fa945b56" UUID_SUB="0c863e5f-2aea-736c-31d9-5d3384c9457c" LABEL="2fe53b89:0" TYPE="linux_raid_member" PARTUUID="ae491ae6-3f16-4139-97be-6cf3cf42eca3"
/dev/sdb2: UUID="953dd93b-7743-3d27-371b-b09858f73957" UUID_SUB="c1b76bc0-6538-d2be-a6f4-0a17df7b6323" LABEL="2fe53b89:1" TYPE="linux_raid_member" PARTUUID="ddfa97de-6c5c-42c2-ac8a-b4271ae106a8"
/dev/sdb3: UUID="5511f0ec-9950-a668-9a4e-f5864fab40fb" UUID_SUB="01978edd-b383-2b45-7e42-5d34f779e5f3" LABEL="2fe53b89:data-0" TYPE="linux_raid_member" PARTUUID="5e7fe2d5-fd9d-4242-ab04-1dc8528f76d2"
/dev/md127: LABEL="2fe53b89:data" UUID="6fb18eb7-d6f8-49ae-a8bc-8d16c193fbcd" UUID_SUB="d1c3b76c-683d-4086-b9b3-2df2d15fcbc7" TYPE="btrfs"
/dev/ubi0_0: UUID="54c651e0-a819-4cc7-9b81-8b977fbb046d" TYPE="ubifs"
```

```
fdisk -l

Disk /dev/mtdblock0: 1.5 MiB, 1572864 bytes, 3072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mtdblock1: 512 KiB, 524288 bytes, 1024 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mtdblock2: 6 MiB, 6291456 bytes, 12288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mtdblock3: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mtdblock4: 116 MiB, 121634816 bytes, 237568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 80EAF84B-14A4-4E63-AD8E-26C98B92CA81

Device       Start        End    Sectors  Size Type
/dev/sda1       64    8388671    8388608    4G Linux RAID
/dev/sda2  8388672    9437247    1048576  512M Linux RAID
/dev/sda3  9437248 3907029119 3897591872  1.8T Linux RAID

Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 14D89F7A-C877-428C-B35F-5A9F9728FA94

Device       Start        End    Sectors  Size Type
/dev/sdb1       64    8388671    8388608    4G Linux RAID
/dev/sdb2  8388672    9437247    1048576  512M Linux RAID
/dev/sdb3  9437248 3907029119 3897591872  1.8T Linux RAID

Disk /dev/md0: 4 GiB, 4290772992 bytes, 8380416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/md1: 511 MiB, 535822336 bytes, 1046528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/md127: 1.8 TiB, 1995432787968 bytes, 3897329664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

```
# cat /etc/mdadm/mdadm.conf
CREATE owner=root group=disk mode=0660 auto=yes
```

---

