---
title: "Trouble booting Ubuntu7.10 and Windows XP SP3"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by karthikCV on 2008-11-29
hi,
i installed Ubuntu 7.10 on my 80GB IDE hard disk and i have Windows XP sp3 on my 250GB SATA hard disk.
My problem is i have to manually choose the booting of OS from the BIOS Configuration by changing the hard disk priority every single time to switch between OS's .

The description at the time of loading is something close to this :

1. the Processor("AMD Athlon 64 3000+") is detected
2. DRAM 384MB and 128MB shared memory
3. it detects my IDE disk as MASTER ( Ubuntu 7.10 )
4. it detects my SATA disk as MASTER (too).(  Windows XP sp3)
5. it detects that the floppy drive is not there.
6. it asks me to enter "F1" to continue or "DEL" to setup.

As a noob i have no clue of what i should do ?
I request anyone to guide me

---

### Post by oilchangeguy on 2008-11-29
> **karthikCV said:**
> hi,
i installed Ubuntu 7.10 on my 80GB IDE hard disk and i have Windows XP sp3 on my 250GB SATA hard disk.
My problem is i have to manually choose the booting of OS from the BIOS Configuration by changing the hard disk priority every single time to switch between OS's .

The description at the time of loading is something close to this :

1. the Processor("AMD Athlon 64 3000+") is detected
2. DRAM 384MB and 128MB shared memory
3. it detects my IDE disk as MASTER ( Ubuntu 7.10 )
4. it detects my SATA disk as MASTER (too).(  Windows XP sp3)
5. it detects that the floppy drive is not there.
6. it asks me to enter "F1" to continue or "DEL" to setup.

As a noob i have no clue of what i should do ?
I request anyone to guide me

which key are you pressing? F1, or del?

---

### Post by caljohnsmith on 2008-11-29
If you don't press F1 or Del, do you boot into Ubuntu or XP? It sounds like probably you would boot into Ubuntu. If that is the case, it should be easy to boot Windows from your Grub menu. How about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
And that will help clarify your system.

---

### Post by karthikCV on 2008-11-29
i will try it out now.

i got this as the result :

karthik@ParentsGift-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ffe660c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sda2        51199155   488375999   218588422+   f  W95 Ext'd (LBA)
/dev/sda5        51199218   215046089    81923436    7  HPFS/NTFS
/dev/sda6       215046153   378893024    81923436    7  HPFS/NTFS
/dev/sda7       378893088   430092179    25599546    7  HPFS/NTFS
/dev/sda8       430092243   488375999    29141878+   7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb88fb88

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    39118274    19559106   83  Linux
/dev/hda2        39118275   150432659    55657192+   b  W95 FAT32
/dev/hda3       150432660   156296384     2931862+  82  Linux swap / Solaris

karthik@ParentsGift-desktop:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system

karthik@ParentsGift-desktop:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
0000

karthik@ParentsGift-desktop:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

karthik@ParentsGift-desktop:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
xxd: /dev/sdb: No such file or directory

karthik@ParentsGift-desktop:~$

---

