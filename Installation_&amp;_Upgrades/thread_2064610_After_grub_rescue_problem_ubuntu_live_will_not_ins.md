---
title: "After grub rescue problem ubuntu live will not install"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by xrobbo on 2012-09-29
Hello everybody,
I had a problem with the grub. When I turn my 12.04 ubuntu laptop ubunt won't start and the grub rescue message appear.
I've tried to solve with no success, so I decided to reinstall ubuntu from a bootable live usb key. I succeed in booting from the key but then cannot start the installation of OS on the machine. If I launch gparted, it cannot find the partitioning of the hard disk and continue sarching for it.
I'm quite desperate. Any suggestion about how to proceed would be very very welcomed.
thanks in advance

---

### Post by darkod on 2012-09-29
Boot the usb in live mode, open terminal and post the output of:
```
sudo parted -l (small L)
sudo fdisk -l
```

---

### Post by xrobbo on 2012-09-29
Hi, and thanks. The first command does not produce any output. The computer keep on processing, I have waited 10 minutes.
Here is the output of fdisk -l
```

```Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xafad6a08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    41453567    20623360    7  HPFS/NTFS/exFAT
/dev/sda3        41453568    82311167    20428800   83  Linux
/dev/sda4        82313214   625141759   271414273    5  Extended
/dev/sda5        82313216   621887487   269787136   83  Linux
/dev/sda6       621889536   625141759     1626112   82  Linux swap / Solaris

Disk /dev/sdb: 4022 MB, 4022337536 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0217934c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7856127     3928032+   e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 
```

```

---

### Post by darkod on 2012-09-29
Do you know which one is your / partition, sda3 or sda5? There are two Linux partitions on the disk, one of them might be a /home partition if you installed it like that earlier.

---

### Post by xrobbo on 2012-09-29
the operating system is on sda3, whereas sda5 contains the home.

---

### Post by darkod on 2012-09-29
OK, from live mode try reinstalling grub2 on the MBR of sda with:
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That will reinstall it on the MBR but it still might not work if the problem is different. Restart and see if it helped.

---

### Post by xrobbo on 2012-09-29
This I already tried. The problem is that when I launch the first command the laptop starts processing and never stops. I have waited for more than 30 minutes before giving up. Is that possible?
Also, the same happened when I launched gparted, and also when I tried to install ubuntu from the usb key. 
It seems to me that any time I launch a command that operates on the hard disk I get troubles.
Anyway, the most important question is: supposing I launch the command you suggest, shall I wait for how long before considering that nothing is going to happen?

---

### Post by xrobbo on 2012-09-29
Just a further note: I have a brand new dell 3350 with intel i5 on it, so slowness does not depend upon the hardware.

---

### Post by darkod on 2012-09-29
No, the results should be immediate.

Unfortunately, commands not finishing their task fast as soon as they start accessing the HDD sounds like faulty hdd to me.

I had a similar case with two faulty desktop disks I was given to see if they can work or not. They look normal on first view, fdisk will even see them and print the partitions list, but as soon as you give a command accessing the disk, the command never finishes and the disk can't be seen any more.

I might be wrong but this looks to me like hardware failure, or close to it.

---

### Post by xrobbo on 2012-09-29
This is what I feared too. Any way to check if this is really so?

---

### Post by darkod on 2012-09-29
Not sure. You might run a SMART test with smartmontools. You need to install them first. I think you should be able to do that from live mode.

Except that, the only other test I can think of is trying to use the disk. If it continues blocking as soon as any command tries to access it, I guess it's clear.

---

