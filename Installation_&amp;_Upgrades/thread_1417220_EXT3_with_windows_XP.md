---
title: "EXT3 with windows XP"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by esky64 on 2010-02-27
Hi All
Hope some one can help me.
I have just built a new system and have installed windows and ubuntu 9.10 64bit.
Have installed EXT2IFS but windows keeps asking me to format the drive 
chris@chris-desktop:~$ df -k
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda2             15116868   2957076  11391888  21% /
udev                    479268       244    479024   1% /dev
none                    479268      1152    478116   1% /dev/shm
none                    479268        84    479184   1% /var/run
none                    479268         0    479268   0% /var/lock
none                    479268         0    479268   0% /lib/init/rw
/dev/sda6            445678432    238720 422800516   1% /home
chris@chris-desktop:~$ sudo fdisk -l
[sudo] password for chris:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00e600e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        3824    15358140   83  Linux
/dev/sda3            3825       60801   457667752+   5  Extended
/dev/sda5           60194       60801     4883760   82  Linux swap / Solaris
/dev/sda6            3825       60193   452783929+  83  Linux

Partition table entries are not in disk order

I think I need to unmount what gparted tells me is sda6 form format that with mkfs.ext3 -c -I128. How do I unmount the dive?
any help would be great 
Thanks 
Chris

---

### Post by wilee-nilee on 2010-02-27
Ubuntu 9.10 is Ext4 you can't read it with MS. You can use a NTFS partition to share with both OS, I use a external HD myself.

You can also access W7 from Ubuntu and move files easily.

---

### Post by esky64 on 2010-02-27
Sorry not sure if I put in first post that I format /home as ext3 then install ext2if in windows to enable it to read and write ext3

---

### Post by DrMelon on 2010-02-27
On the Ext2IFS website FAQ, under the ext3 section, it says this:
"The Ext2 file system driver of the Ext2 IFS software will refuse mounting an Ext3 file system which contains data in its journal, just like older Linux kernels which have no Ext3 support. In this way data loss and damaging the file system is avoided when the journal is subsequently replayed. So you can access only those Ext3 volumes with the Ext2 IFS software which have been cleanly dismounted beforehand. "

Obviously, your Ubuntu partition has data in the journal. You have to dismount the volume before booting Windows.

---

### Post by esky64 on 2010-02-27
> **DrMelon said:**
> On the Ext2IFS website FAQ, under the ext3 section, it says this:
"The Ext2 file system driver of the Ext2 IFS software will refuse mounting an Ext3 file system which contains data in its journal, just like older Linux kernels which have no Ext3 support. In this way data loss and damaging the file system is avoided when the journal is subsequently replayed. So you can access only those Ext3 volumes with the Ext2 IFS software which have been cleanly dismounted beforehand. "

Obviously, your Ubuntu partition has data in the journal. You have to dismount the volume before booting Windows.

Can you tell me how to cleanly dismount the volume

---

### Post by esky64 on 2010-02-27
I just used mkfs.ext3 -I 128 now ubuntu can't mount the partition /dev/sda6.
How to I get ubuntu to work with the partition

---

### Post by esky64 on 2010-02-28
> **esky64 said:**
> I just used mkfs.ext3 -I 128 now ubuntu can't mount the partition /dev/sda6.
How to I get ubuntu to work with the partition

I just reinstalled Ubuntu 9.10 64Bit
and everything works now :D

---

