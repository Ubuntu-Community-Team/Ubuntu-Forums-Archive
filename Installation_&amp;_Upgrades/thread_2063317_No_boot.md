---
title: "No boot"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by dieselglock on 2012-09-26
I just installed 12.04 tls on a dual boot laptop. I had win7 and 10.04 lts working perfect for 2 yrs. Now when booting i get an error. I have read other posts on the subject and am extremely confused. I managed to get this from another thread but don't really understand  whats going on. 

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   488922209   244460081    7  HPFS/NTFS/exFAT
/dev/sdb2       488922271   976768064   243922897    5  Extended
/dev/sdb5       488922273   799668223   155372975+  83  Linux
/dev/sdb6       956911788   976768064     9928138+  82  Linux swap / Solaris
/dev/sdb7       799670272   956911615    78620672   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 320.1 GB, 320072933376 bytes
256 heads, 63 sectors/track, 38761 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   625142447   312571223+  ee  GPT
ubuntu@ubuntu:~$ 

sda1 is win 7
sdb1 is storage
sdb5 is 12.4lts system
sdb6 swap
sdb7 is 12.4lts home 
sdc1 is fat
sdc2 is data used in win7

Please help

---

### Post by darkod on 2012-09-26
Grub2 probably went to the wrong disk.

Boot with the cd in live mode, open terminal and try this:
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

That will write grub2 on the MBR of /dev/sdb.

Go into BIOS and make sdb first choice to boot. It should work.

By the way, why is sdc with gpt table? Not that it matters, since both OSs are on sdb. But don't use gpt unless you specifically need it, and you don't need it on disks below 2TB and if you are not using UEFI boot.

---

### Post by dieselglock on 2012-09-26
Hello,
Thanks for the fast response.

I tried that but still get this ERROR:no such device :908af3eb-0d15-492-9370-8eb860e33919
GRUB RESCUE>

The result of sudo fdisk -l is:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2f2be63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb648a4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   488922209   244460081    7  HPFS/NTFS/exFAT
/dev/sdb2       488922271   976768064   243922897    5  Extended
/dev/sdb5       488922273   799668223   155372975+  83  Linux
/dev/sdb6       956911788   976768064     9928138+  82  Linux swap / Solaris
/dev/sdb7       799670272   956911615    78620672   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 320.1 GB, 320072933376 bytes
256 heads, 63 sectors/track, 38761 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   625142447   312571223+  ee  GPT
ubuntu@ubuntu:~$ 

Thanks for any help

---

### Post by dieselglock on 2012-09-26
I got it to work using the boot repair tool thanks for the help.

---

### Post by YannBuntu on 2012-09-27
good job :)
please could you use the Thread Tools to mark it [SOLVED] ?

---

### Post by darkod on 2012-09-27
> **dieselglock said:**
> I got it to work using the boot repair tool thanks for the help.

You were probably booting from the wrong disk. Boot-repair installs grub2 to all disks so you don't have to worry where you boot from, but I always encourage people to understand what they have and how things run.

For example, tomorrow you delete this ubuntu installation, install a new one or what ever. If you try booting from the wrong disk it will still look for this old installation (since grub2 now is on all disks) and again will give you grub error.

If you know where your bootloader is, and you use this disk to boot, there should not be any issues.

---

