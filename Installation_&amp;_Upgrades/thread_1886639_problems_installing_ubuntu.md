---
title: "problems installing ubuntu"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by Ahmed Kotb on 2011-11-25
hi,
iam got a new hp [g6 laptop]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c03000343") and i wanted to install ubuntu on it

first problem:
i tried booting into ubuntu 11.10 x64 livecd but after choosing language it stuck into a black screen.
apparently this is a common problem with 11.10 so i got an old 10.04 x86 livecd and it didn't face that problem, but it has the second problem which as far as i understand is not version related


Second (Main) problem:
The computer comes with win7 64 bit , uses UEFI to boot and GPT as a partitioning scheme

attached the image of hard drives partitions from windows

during ubuntu install the installer sees the whole hard drive as unallocated disk space ...

so what can i do so that ubuntu can see the other partitions ?

thanks in advance

---

### Post by Ahmed Kotb on 2011-11-25
this is the output of sudo fsck -lu

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc13cbdc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          409600   159584255    79587328    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3      1208201216  1241939967    16869376    7  HPFS/NTFS
/dev/sda4       159584256  1250260991   545338368    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5       159586304   683874303   262144000    7  HPFS/NTFS
/dev/sda6       683876352  1208201215   262162432    7  HPFS/NTFS
/dev/sda7      1241942016  1250260991     4159488    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 4011 MB, 4011851776 bytes
5 heads, 32 sectors/track, 48972 cylinders, total 7835648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dad4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7835647     3913792    c  W95 FAT32 (LBA)

```

---

### Post by grahammechanical on 2011-11-25
I found this link for you:

[https://help.ubuntu.com/community/UEFIBooting]("https://help.ubuntu.com/community/UEFIBooting")

Note the comment about some machines under the heading Setting Up Grub2 (U)EFI

I would say that 10.04 is not suitable for a UEFI BIOS machine. Try downloading another copy of the 11.10 iso image. Or try letting the language time out to the default language. I hope you can read the default language! Is it a CD that you are using or a USB memory stick?

The partitioner manager in 10.04 may not support GUID Partition Tables (GPT). Have you thought of that? You need to get the 11.10 live CD/USB working.

I needed to change some settings in my BIOS to get booting from a USB working correctly. In my BIOS I had legacy floppy drive enabled and that made the live boot process very slow. So slow that I though the process had stalled. Once I disabled legacy floppy I got access to USB settings in another part of the BIOS program and I could set the transfer speed to the maximum and that solved the slowness of the boot from USB.

I do not know if this applies in your case.

Regards.

---

### Post by Ahmed Kotb on 2011-11-25
> **grahammechanical said:**
> I found this link for you:

[https://help.ubuntu.com/community/UEFIBooting]("https://help.ubuntu.com/community/UEFIBooting")

Note the comment about some machines under the heading Setting Up Grub2 (U)EFI

I would say that 10.04 is not suitable for a UEFI BIOS machine. Try downloading another copy of the 11.10 iso image. Or try letting the language time out to the default language. I hope you can read the default language! Is it a CD that you are using or a USB memory stick?

The partitioner manager in 10.04 may not support GUID Partition Tables (GPT). Have you thought of that? You need to get the 11.10 live CD/USB working.

I needed to change some settings in my BIOS to get booting from a USB working correctly. In my BIOS I had legacy floppy drive enabled and that made the live boot process very slow. So slow that I though the process had stalled. Once I disabled legacy floppy I got access to USB settings in another part of the BIOS program and I could set the transfer speed to the maximum and that solved the slowness of the boot from USB.

I do not know if this applies in your case.

Regards.

i was able to boot into 11.10 but the problem still occurs , i have found that i have the problem of overlapping partitions (from the output of fdisk -lu) , iam trying to fix it but i can't found an easy solution yet..

is there any solution for that other than formatting the whole hard drive ?

---

### Post by raja.genupula on 2011-11-25
with clear explanation
[http://www.pclinuxos.com/forum/index.php?topic=70939.0](http://www.pclinuxos.com/forum/index.php?topic=70939.0)

---

### Post by Ahmed Kotb on 2011-11-25
> **raja.genupula said:**
> with clear explanation
[http://www.pclinuxos.com/forum/index.php?topic=70939.0](http://www.pclinuxos.com/forum/index.php?topic=70939.0)

i don't see how this can be useful :(
iam not an expert ..

i found this command sfdisk -uS -l /dev/sda 
and it gives the following

```

ubuntu@ubuntu:~$ sudo sfdisk -uS -l /dev/sda

Disk /dev/sda: 77825 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    409599     407552   7  HPFS/NTFS
/dev/sda2        409600 159584255  159174656   7  HPFS/NTFS
		end: (c,h,s) expected (1023,254,63) found (717,232,27)
/dev/sda3     1208201216 1241939967   33738752   7  HPFS/NTFS
/dev/sda4     159584256 1250260991 1090676736   f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (717,232,28)
		end: (c,h,s) expected (1023,254,63) found (1,37,36)
/dev/sda5     159586304 683874303  524288000   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (717,200,60)
		end: (c,h,s) expected (1023,254,63) found (585,116,43)
/dev/sda6     683876352 1208201215  524324864   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (585,85,13)
		end: (c,h,s) expected (1023,254,63) found (455,76,5)
/dev/sda7     1241942016 1250260991    8318976   b  W95 FAT32
		start: (c,h,s) expected (1023,254,63) found (507,208,22)
		end: (c,h,s) expected (1023,254,63) found (1,37,36)

```


how i can fix this partitions boundaries without screwing things up ?

---

### Post by darkod on 2011-11-25
I personally haven't used it, but people have repaired overlapping partitions with fixparts: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

