---
title: "[SOLVED] Help restore GRUB"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by underground on 2008-06-17
Please help me restore the grub.
I followed the instructions here [http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

but after the command chroot /mnt  /bin/bash i should type grub-install /dev/sdX
But then comes an error saying that:
```
root@ubuntu:/# grub-install /dev/sdb7
bash: grub-install: command not found
```

What should i do???
I mounted my disk with ubuntu installed through the live cd but the /boot direcory is empty.

Please i need help because i get an Grub error 15.

---

### Post by underground on 2008-06-17
I think i made it...
I entered grub and the did the following
```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,6)

grub> setup (hd1,6)

Error 12: Invalid device requested

grub> root (hd1,6)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,6)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> 

```

I will restart and will say if it works.

---

### Post by meierfra. on 2008-06-17
Post the output of 

```
sudo fdisk -l
```
(l is a lowercase L)

---

### Post by underground on 2008-06-18
I restarted and i keep getting the error 15 but now it goes automatically to grub shell.
So i type find /boot/grub/stage1
It says that it in (hd0,6).
then i type root (hd0,6) and setup (hd0).
It says that everything completed without errors but after reboot i still go to grub shell.

This is the output of fsdisk
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13081308

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             263        5104    38893365    f  W95 Ext'd (LBA)
/dev/sda2   *        5105       33721   229866021    7  HPFS/NTFS
/dev/sda3           33722       38912    41696707+   7  HPFS/NTFS
/dev/sda5             263        2220    15727603+   7  HPFS/NTFS
/dev/sda6            2221        5104    23165698+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65f765f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6526    52420063+   7  HPFS/NTFS
/dev/sdb2            6527       48588   337863015    f  W95 Ext'd (LBA)
/dev/sdb5            6527       32713   210347046    7  HPFS/NTFS
/dev/sdb6           32714       42113    75505468+   7  HPFS/NTFS
/dev/sdb7           42114       44603    20000893+  83  Linux
/dev/sdb8           44604       48339    30009388+  83  Linux
/dev/sdb9           48340       48588     2000061   82  Linux swap / Solar

```

Now i am writing through live cd.

---

### Post by meierfra. on 2008-06-18
I still don't see what is going on. So I need more information.

Post the output of all these commands:

At the grub screen at boot up type

```
find /boot/grub/stage2

find /boot/grub/menu.lst
```

Boot from the live cd, open a terminal and type

```

mkdir Ubuntu
sudo mount /dev/sdb7 Ubuntu
cd Ubuntu/boot
ls -l
ls -l grub
cat grub/menu.lst
```

---

### Post by underground on 2008-06-18
Thank you very much for helping me but i decided to install again ubuntu as i need the pc for homework..

Now everything works fine.

---

