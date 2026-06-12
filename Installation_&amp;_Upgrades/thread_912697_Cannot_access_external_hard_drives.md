---
title: "Cannot access external hard drives"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by Mark W on 2008-09-07
Since installing the latest Kubuntu version, I cannot access either of my external IDE hard drives. Surely both of them cant have failed at the same time. 

I read a previous thread and installed GParted and ran sudo blkid & sudo blkid, output below: (NOTE, i have 2 internal hard drives and it recognizes these 2 drives ok, all drives are 160 GB)

sudo blkid 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe197e197

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       19456    53882010    f  W95 Ext'd (LBA)
/dev/sda5           12749       19456    53881978+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b0c4b0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9585    76991481    7  HPFS/NTFS
/dev/sdb2            9586       19457    79296840    5  Extended
/dev/sdb5            9586       14265    37592068+  83  Linux
/dev/sdb6           19050       19457     3277228+  82  Linux swap / Solaris
/dev/sdb7           14266       18847    36804883+  83  Linux
/dev/sdb8           18848       19049     1622533+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbaa3baa3

   Device Boot      Start         End      Blocks   Id  System




sudo blkid 

/dev/sda1: UUID="2EA07F37A07F049D" LABEL="IDE160C" TYPE="ntfs"
/dev/sda5: UUID="DE60B07860B058CB" LABEL="IDE160D" TYPE="ntfs"
/dev/sdb1: UUID="3E04CCDC04CC9873" LABEL="SATA160XP" TYPE="ntfs"
/dev/sdb5: UUID="441c78e5-ff34-4bcd-a889-e6aef44e7a79" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb6: TYPE="swap" UUID="b3479c5a-5d3e-4af6-8dd9-d1c62873b398"
/dev/sdb7: UUID="4762d62a-073c-4b13-9449-0318e56e23a9" TYPE="ext3"
/dev/sdb8: TYPE="swap" UUID="c75a6f6b-04de-492b-8292-7329ddb91e8a"

---

### Post by Pumalite on 2008-09-07
If your extenal is sdg; maybe it needs to be formated o you may have to explore it with rescuecd;
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

