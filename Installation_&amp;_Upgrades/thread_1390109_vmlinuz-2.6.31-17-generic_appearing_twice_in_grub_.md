---
title: "vmlinuz-2.6.31-17-generic appearing twice in grub menu, why?"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by Blackie_Chan on 2010-01-25
When I restart my machine, in the grub menu, there's always 2 entries for vmlinuz-2.6.31-17-generic. It looks something like:

vmlinuz-2.6.31-17-generic
vmlinuz-2.6.31-17-generic (recovery)
vmlinuz-2.6.31-17-generic
vmlinuz-2.6.31-17-generic (recovery)

Can you tell me how to remove the duplicate entry? 

Thanks

blackie_chan@ubuntu:~/Downloads$ sudo update-grub
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```
blackie_chan@ubuntu:~/Downloads$ cd /boot/
blackie_chan@ubuntu:/boot$ ls
```
abi-2.6.31-17-generic         memtest86+.bin
config-2.6.31-17-generic      System.map-2.6.31-17-generic
grub                          vmcoreinfo-2.6.31-17-generic
initrd.img-2.6.31-17-generic  vmlinuz-2.6.31-17-generic
```

---

### Post by Leppie on 2010-01-25
could you post the output of the following commands:
```
sudo fdisk -l
sudo blkid
```

---

### Post by Blackie_Chan on 2010-01-25
> **Leppie said:**
> could you post the output of the following commands:
```
sudo fdisk -l
sudo blkid
```

blackie_chan@ubuntu:~$ sudo fdisk -l
```

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4086cea9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6260    50179072    7  HPFS/NTFS
/dev/sda3            6261       19314   104856255   83  Linux
/dev/sda4           19315       30515    89972032+  83  Linux

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8aeb8aeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1305    10482381   83  Linux
/dev/sdb2            8063       14589    52428127+  83  Linux
/dev/sdb3            1306        8062    54275602+   b  W95 FAT32

Partition table entries are not in disk order

```
blackie_chan@ubuntu:~$ sudo blkid
```
/dev/sda1: UUID="942AAD512AAD30E2" LABEL="System Reserved" TYPE="ntfs"
/dev/sda2: UUID="3878B11378B0D13C" TYPE="ntfs"
/dev/sda3: LABEL="DATA" UUID="e605b1e4-1da0-4246-a971-2c6b10e7425c" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: LABEL="BACKUP" UUID="5b56ee5e-4778-4ee7-885b-6c2fcb966ee6" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb3: LABEL="" UUID="38EE-9CEA" TYPE="vfat"
/dev/sdb1: UUID="c26d0cc1-b6cc-4bc3-83b0-03384ba6085b" TYPE="ext4"
/dev/sdb2: LABEL="HOME" UUID="8fdb002c-d87f-4f6d-8c4b-a20ba23249d2" TYPE="ext3"

```

---

### Post by Leppie on 2010-01-25
> **Blackie_Chan said:**
> ```
/dev/sda1: UUID="942AAD512AAD30E2" LABEL="System Reserved" TYPE="ntfs"
/dev/sda2: UUID="3878B11378B0D13C" TYPE="ntfs"
[COLOR=Red]**/dev/sda3: LABEL="DATA" UUID="e605b1e4-1da0-4246-a971-2c6b10e7425c" SEC_TYPE="ext2" TYPE="ext3"**[/COLOR]
/dev/sda4: LABEL="BACKUP" UUID="5b56ee5e-4778-4ee7-885b-6c2fcb966ee6" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb3: LABEL="" UUID="38EE-9CEA" TYPE="vfat"
/dev/sdb1: UUID="c26d0cc1-b6cc-4bc3-83b0-03384ba6085b" TYPE="ext4"
/dev/sdb2: LABEL="HOME" UUID="8fdb002c-d87f-4f6d-8c4b-a20ba23249d2" TYPE="ext3"

```
could it be that grub is picking up your backup?

---

### Post by Blackie_Chan on 2010-01-25
The root(/) partition is installed only on /dev/sdb1 partition, the other ext3 partitions are used for storing data. None of the other partitions have a /boot directory.

---

### Post by Leppie on 2010-01-25
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by Blackie_Chan on 2010-01-25
> **Leppie said:**
> could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

Thanks alot Leppie, 

I found the problem after running the script above. In /etc/grub.d, I had 10_linux and 10_linux.bak. Removing the backup file fixed my problem.

---

### Post by Leppie on 2010-01-25
> **Blackie_Chan said:**
> Thanks alot Leppie, 

I found the problem after running the script above. In /etc/grub.d, I had 10_linux and 10_linux.bak. Removing the backup file fixed my problem.
glad you found the error.
you could've kept the backup copy of your 10_linux by making it a non-executable:
```
sudo chmod -x /etc/grub.d/10_linux.bak
```

---

