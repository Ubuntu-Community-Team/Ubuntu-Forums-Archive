---
title: "MBR destroyed - how to retrieve partitions info"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by c.monty on 2012-01-31
Hello!

I had setup successfully a LMDE installation with dual boot option.
For the LMDE installation I additionally used LUKS and LVM, means the disk layout is:
Partition 1: ~150MB, boot
Partition 2: ~ 10GB, Windows XP
Partition 3: ~ 100GB, LMDE with LUKS and LVM (rest of disk)

My problem was, that I couldn't boot Windows XP.
By accident I deleted the MBR with tool "Testdisk".

Firstly, I want to focus to restore the MBR.
Unfortunatly I don't have a backup of the MBR.

I'm quite certain that I didn't modify or delete any data (except for MBR) of the disk, and therefore I assume that all data in the 3 partitions is still there.

Do you have any idea how to recover the MBR, e.g. by analysing the hexcode.
Obviously some recovery tools, like "Testdisk" fail to identify the partitions due to usage of LUKS.

Any support is greatly appreciated.

THX

---

### Post by WthIteh on 2012-01-31
If the only corrupted part is MBR, reinstalling grub will write MBR again.
So you could boot with a live CD and then mount partitions. Then you could install grub again to write MBR again by:
```
grub-install --boot-directory=path-to-where-you-mounted-boot-partition /dev/sda
```

---

### Post by BC59 on 2012-01-31
You can repair MBR with Boot-Repair
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-01-31
I assume it is the partition table not the boot code that is the issue. I would think testdisk would see the three partitions even if it cannot see the data/structure of the third partition with LVM.

What does this show?

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt


Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

---

### Post by Resplendent Raven on 2012-01-31
@ oldfred
I posted this thread yesterday - [http://ubuntuforums.org/showthread.php?t=1917903](http://ubuntuforums.org/showthread.php?t=1917903)
I take it that this method is relevant to my question?

---

### Post by c.monty on 2012-02-01
> **oldfred said:**
> I assume it is the partition table not the boot code that is the issue. I would think testdisk would see the three partitions even if it cannot see the data/structure of the third partition with LVM.

What does this show?

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt


Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

oldfred is absolutely right:
I've destroyed MBR + partition table.

I assume I should restore the partition table first before I can continue.

I will update this ticket soon.

THX

---

### Post by c.monty on 2012-02-04
Hello!

This is the output of
sfdisk -d /dev/sda > PTsda.txt

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   321237, Id=83, bootable
/dev/sda2 : start= 42283080, size=    16065, Id=83
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0

In addition I have used script "boot-info-script" from [here]("http://bootinfoscript.sourceforge.net/") which provides additional information. 

Below is just an extract of the output. The complete output is attached in file "RESULTS.txt".

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       321,299       321,237  83 Linux
/dev/sda2          42,283,080    42,299,144        16,065  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        e1e11842-1892-47a3-894c-40d3a493dcfe   ext2       boot
/dev/sda2        1147f5a6-2032-49c9-b5e6-afafc1b0c007   crypto_LUKS 

```

What you can see is that only 2 partitions are identified.
This is incorrect!
1. If you consider the gap between end sector of /dev/sda1 and start sector of /dev/sda2, this is the section where NTFS partition is located.
2. If you consider the number of sectors for /dev/sda2, this would indicate a very small partition. In fact the crypto_LUKS partition is >100G.

How should I proceed from here?

THX

---

### Post by c.monty on 2012-02-04
_Update:_

I can open the LUKS partition using this command:
cryptsetup luksOpen /dev/sda2 sda2_crypt

The output of the script now provides some additional information:
```

da1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       321,299       321,237  83 Linux
/dev/sda2          42,283,080    42,299,144        16,065  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/sda2_crypt ibbTYj-WzS0-kwgj-rVMw-lBpT-12Bs-RO2adN LVM2_member 
/dev/sda1        e1e11842-1892-47a3-894c-40d3a493dcfe   ext2       boot
/dev/sda2        1147f5a6-2032-49c9-b5e6-afafc1b0c007   crypto_LUKS 

```

As you can see, there's a LVM installed in the crypted partition.
However, I cannot access the LVM.
root@sysresccd /root/Downloads % vgchange -a y
  No volume groups found
root@sysresccd /root/Downloads % vgdisplay 
  No volume groups found

The complete output of boot-info-script is attached as file "RESULTS1.txt".

---

### Post by oldfred on 2012-02-04
I do not know LVM enough to be able to help. I seems that the partition table is corrupted, but I do not know if changing it will then prevent the LVM with encryption from working. Maybe some of these links will have a clue?

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

---

### Post by darkod on 2012-02-04
You said at the beginning that even testdisk doesn't locate the partition (NTFS). I don't know how much experience you have with testdisk, but does that mean that even the deeper search can't find your missing ntfs partition?

Yes, the mbr is deleted but I was under the impression testdisk scans the whole disk and reports all found partitions.

I would try it again and make sure you do the deeper search, not just the quick serach.

As far as the LUKS partition, testdisk should always see it as LVM type but of course it can't see the data inside.

But the first step is to write a new, correct, partition table, not whether testdisk can look inside LUKS partitions.

I've seen plenty of success reports for testidks and deleted partitions here, I would give it another try with the deeper search.

---

### Post by c.monty on 2012-02-04
> **oldfred said:**
> I do not know LVM enough to be able to help. I seems that the partition table is corrupted, but I do not know if changing it will then prevent the LVM with encryption from working. Maybe some of these links will have a clue?

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)


This issue is neither about resizing the LVM on the encrypted partition (LUKS), nor about resizing the encrypted partition (LUKS) itself).

I didn't touch the partitions (as far as I know), but only the MBR including partition table.

This means I do assume that partitions are not displayed correctly except for partition /dev/sda1 which is the boot partition.
The second partition /dev/sda2 is supposed to be the NTFS partition, however it is not readable since the installation of Linux in the third partition using LUKS and LVM.

Ideally I get a partition table consisting of all three partitions, and I can mount the Linux partition.

THX

---

### Post by c.monty on 2012-02-04
> **darkod said:**
> You said at the beginning that even testdisk doesn't locate the partition (NTFS). I don't know how much experience you have with testdisk, but does that mean that even the deeper search can't find your missing ntfs partition?

Yes, the mbr is deleted but I was under the impression testdisk scans the whole disk and reports all found partitions.

I would try it again and make sure you do the deeper search, not just the quick serach.

As far as the LUKS partition, testdisk should always see it as LVM type but of course it can't see the data inside.

But the first step is to write a new, correct, partition table, not whether testdisk can look inside LUKS partitions.

I've seen plenty of success reports for testidks and deleted partitions here, I would give it another try with the deeper search.


In fact I did use all available options of Testdisk including the deep search option.
The result was not different as mentioned above: only two partitions are identified: boot partition and Linux partition.
Based on these findings the partition table was accidently written from Testdisk to the drive.

THX

---

### Post by c.monty on 2012-02-04
_Update:_ More details about LVM configuration

Hello!

I managed to get more details of the LVM configuration on the LUKS partition.

```

root@sysresccd /root % cryptsetup luksOpen /dev/sda2 sda2_crypt
Enter passphrase for /dev/sda2: 
root@sysresccd /root % vgscan --mknodes
  Reading all physical volumes.  This may take a while...
  Found volume group "vg" using metadata type lvm2
root@sysresccd /root % vgchange -a y
  device-mapper: resume ioctl failed: Invalid argument
  Unable to resume vg-swap (253:1)
  device-mapper: resume ioctl failed: Invalid argument
  Unable to resume vg-root (253:2)
  2 logical volume(s) in volume group "vg" now active

root@sysresccd /root % pvdisplay 
  --- Physical volume ---
  PV Name               /dev/mapper/sda2_crypt
  VG Name               vg
  PV Size               128.88 GiB / not usable 1.31 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              32994
  Free PE               0
  Allocated PE          32994
  PV UUID               ibbTYj-WzS0-kwgj-rVMw-lBpT-12Bs-RO2adN
   
root@sysresccd /root % vgdisplay 
  --- Volume group ---
  VG Name               vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               128.88 GiB
  PE Size               4.00 MiB
  Total PE              32994
  Alloc PE / Size       32994 / 128.88 GiB
  Free  PE / Size       0 / 0   
  VG UUID               oUe0DS-dcGH-e6lg-holh-PjGJ-CM12-nrBD0n
   
root@sysresccd /root % lvdisplay 
  /dev/mapper/vg-swap: open failed: No such file or directory
  --- Logical volume ---
  LV Name                /dev/vg/swap
  VG Name                vg
  LV UUID                V3OlNR-ZlEM-7YWK-rgiy-nvAR-KGeF-CjqJa3
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                2.54 GiB
  Current LE             650
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  /dev/mapper/vg-root: open failed: No such file or directory
  --- Logical volume ---
  LV Name                /dev/vg/root
  VG Name                vg
  LV UUID                if0NAl-AvPe-0vlV-pive-99Se-fnsJ-H1rY1q
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                126.34 GiB
  Current LE             32344
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto

```

I think it's clear now that the expected size of the partition is not displayed correctly by the partition table.

The output of "Boot Info Script" is attached as file "RESULTS3.txt".

Do you have any ideas to fix this?

THX

---

### Post by darkod on 2012-02-04
Fixparts seems capable repairing errors in partition tables.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

But with a LUKS partition containing LVM I'm not sure if it can "understand" it. You might give it a try.

---

### Post by c.monty on 2012-02-15
Hi!

Would it make sense to copy the partitions with dd to another disk and then recover the data?
I mean, based on the disk layout
```

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       321,299       321,237  83 Linux
/dev/sda2          42,283,080    42,299,144        16,065  83 Linux

```
I could execute this commands to copy every partition individually:
```

dd if /dev/sda bs=512 count=321236 skip=62 | gzip > ~/image-compress_sda1.img.gz
dd if /dev/sda bs=512 count=41961781 skip=321299 | gzip > ~/image-compress_sda2.img.gz
dd if /dev/sda bs=512 skip=42283079 | gzip > ~/image-compress_sda3.img.gz

```

Is the syntax correct, means are the numbers for options "bs", "skip", "count" correct?

THX

---

### Post by darkod on 2012-02-15
You could copy with dd but I don't see much point except having a copy in case trying to recover the disk messes it up completely.
Your problem is that somehow /dev/sda is missing the LVM partition, so copying the existing partitions seems little help.

I still didn't understand, you are only missing the LVM partition (was it /dev/sda3? ) or it should be in place of /dev/sda2 only much bigger? How many partitions did you have?

---

### Post by c.monty on 2012-02-15
> **darkod said:**
> You could copy with dd but I don't see much point except having a copy in case trying to recover the disk messes it up completely.
Your problem is that somehow /dev/sda is missing the LVM partition, so copying the existing partitions seems little help.

I still didn't understand, you are only missing the LVM partition (was it /dev/sda3? ) or it should be in place of /dev/sda2 only much bigger? How many partitions did you have?

This is the original disk layout (don't take the numbers for partition size 100%):
Partition 1: ~150MB, boot
Partition 2: ~ 10GB, Windows XP
Partition 3: ~ 130GB, LMDE with LUKS and LVM (rest of disk)

Partition 3 is the location of Linux, which is encrypted using LUKS and is build on LVM with 2 logical volumes: Swap and root.

The logical volumes information has been posted in a previous reply.

I agree that the problem now looks like to be related to the LVM.

Any idea to fix this?

THX

---

### Post by darkod on 2012-02-15
> **c.monty said:**
> This is the original disk layout (don't take the numbers for partition size 100%):
Partition 1: ~150MB, boot
Partition 2: ~ 10GB, Windows XP
Partition 3: ~ 130GB, LMDE with LUKS and LVM (rest of disk)

Partition 3 is the location of Linux, which is encrypted using LUKS and is build on LVM with 2 logical volumes: Swap and root.

The logical volumes information has been posted in a previous reply.

I agree that the problem now looks like to be related to the LVM.

Any idea to fix this?

THX

Only sda1 seems correct because 150MB is approx 320,000 sectors.
sda2 is reported as only 16,000 sectors which is only 8MB and Linux type, not ntfs (it is supposed to be XP according to you).

This is even without considering the LUKS partition and the encryption.

You also said you tried testdisk and it does not detect sda2 as 10GB ntfs and sda3.

In that case I am out of ideas. Testdisk is usually good detecting even deleted partitions, there would have been hope if it found them. But like this...

---

