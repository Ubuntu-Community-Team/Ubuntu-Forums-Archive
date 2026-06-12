---
title: "Ubuntu installer won't see my partitions"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by forza.stiinta on 2011-09-10
My HDD has 3 partitions. On the 1st there a windows 7 installation, on one Ubuntu 11.4 and the 3rd is NTFS with data.

My ubuntu installation has crashed and won't boot, so I want to reinstall it.

The issue is that the installer sees my hard drive as having no partiion, just 160gb of unallocated space. 

What can I do? I want to replace the old Ubuntu with a fresh installation, and I really need my data and Windows7 to remain untouched. 

The only option I am presented is full format of the hdd...

---

### Post by YesWeCan on 2011-09-10
Sometimes this is caused by old raid super blocks on your disk. From live CD try this:

[COLOR="DarkSlateBlue"]sudo apt-get install dmraid
sudo dmraid -E -r /dev/sdX[/COLOR]
where X is the drive letter of your disk.

If that doesn't work, please post the output of
[COLOR="DarkSlateBlue"]sudo sfdisk -luS[/COLOR]

---

### Post by srs5694 on 2011-09-12
This is usually caused by subtle damage to the partition table or, as YesWeCan says, old RAID metadata. My [FixParts program](http://www.rodsbooks.com/fixparts/) fixes most of the partition table issues that can cause this problem, but not the leftover RAID data problem. For diagnostic purposes, I recommend:

```

sudo fdisk -lu

```This has an advantage over the "sfdisk -luS" that YesWeCan suggests because it reports the disk's size, which is critical because one of the causes of the symptom you report is a partition that's too big for the disk. Without the disk size information, you can't tell if any partition is too big. (sfdisk reports the disk size in cylinder, head, and sector units, but that's imprecise. On most disks, partitions may be a bit bigger than the CHS units specified and still be small enough to fit on the disk.)

See [this page of mine]("http://www.rodsbooks.com/missing-parts/index.html") for more on this topic, including an alternative way to fix it with sfdisk.

---

### Post by forza.stiinta on 2011-09-14
Thanks for your answers.

Attached is a screenshot.

You can see that linux systems sees my partitions, gparted no, and also the output of fdisk -lu

I am not, or have never used raid. Also, I could not run FixParts... I got the rpm, unpacked it, but it dies on "make".

---

### Post by fdrake on 2011-09-14
before building from source run this commands:

```

sudo aptitude install gcc make build-essential 

```
then follow by building from source. if you still have problem post here the erros msgs.

also can you please copy and paste the output for "sudo fdisk -lu" in a post it's easier to see it on text then on an image.

---

### Post by forza.stiinta on 2011-09-14
All 3 packages are installed, but I get this error:
```
ubuntu@ubuntu:~/Desktop/gptfdisk-0.8.0$ make
g++ -Wall -D_FILE_OFFSET_BITS=64 -D USE_UTF16   -c -o guid.o guid.cc
In file included from guid.cc:22:0:
guid.h:29:23: fatal error: uuid/uuid.h: No such file or directory
compilation terminated.
make: *** [guid.o] Error 1
ubuntu@ubuntu:~/Desktop/gptfdisk-0.8.0$ 

```

Here's the output of fdisk -lu

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34aa5865

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52300079    26150008+   7  HPFS/NTFS
/dev/sda2        52300202   312575759   130137779    f  W95 Ext'd (LBA)
/dev/sda5   *    52300204   257100479   102400138    7  HPFS/NTFS
/dev/sda6       305930240   312580095     3324928   82  Linux swap / Solaris
/dev/sda7       301801472   305926143     2062336   82  Linux swap / Solaris
/dev/sda8       257101824   297670655    20284416   83  Linux
/dev/sda9       297672704   301797375     2062336   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by fdrake on 2011-09-14
do this and try again:
```

sudo aptitude install uuid-dev libossp-uuid-dev

```


also have you tried to fix the problem with
fsck?

```

sudo ntfsfix /dev/sda1 /dev/sda3 
sudo fsck -y /dev/sda6 /dev/sda7 /dev/sda8 /dev/sda9

```

---

### Post by srs5694 on 2011-09-14
> **forza.stiinta said:**
> ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34aa5865

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52300079    26150008+   7  HPFS/NTFS
/dev/sda2        52300202   [COLOR=Red]312575759[/COLOR]   130137779    f  W95 Ext'd (LBA)
/dev/sda5   *    52300204   257100479   102400138    7  HPFS/NTFS
/dev/sda6       305930240   [COLOR=Red]312580095[/COLOR]     3324928   82  Linux swap / Solaris
/dev/sda7       301801472   305926143     2062336   82  Linux swap / Solaris
/dev/sda8       257101824   297670655    20284416   83  Linux
/dev/sda9       297672704   301797375     2062336   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I've highlighted the cause of the problem in red -- your /dev/sda5, which is a logical partition and thus must be entirely contained within your extended partition -- ends after the end of the extended partition. FixParts should be able to fix this problem -- but of course, you should be sure to view the partition table as FixParts sees it (using "p") to verify that it's including all your partitions (except for the extended partition, which it drops and then re-creates when you save your changes). Only after you're sure that FixParts is seeing everything correctly should you type "w" to save your changes.

Installing uuid-dev, as fdrake suggests, should enable you to compile GPT fdisk; however, you'll probably find it easier to install [a binary package](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.0/fixparts-binaries/) (select the RPM or Debian package for whatever distribution you're using); or you can download and boot [Parted Magic,](http://partedmagic.com) recent versions of which include FixParts.

---

### Post by Ankhwatcher on 2011-09-14
I am having the same sorts of problems. Here is what I'm seeing on the computer.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd49287ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771071   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/dm-0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1              63   976768064   488384001   83  Linux
Partition 1 does not start on physical sector boundary.

Disk /dev/dm-1: 500.1 GB, 500105217024 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976768002 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 98816 bytes
Disk identifier: 0x27dd27dc

Disk /dev/dm-1 doesn't contain a valid partition table
```

Thanks,
-ANkh

---

### Post by fdrake on 2011-09-14
> 
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd49287ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771071   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/dm-0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1              63   976768064   488384001   83  Linux
Partition 1 does not start on physical sector boundary.

Disk /dev/dm-1: 500.1 GB, 500105217024 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976768002 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 98816 bytes
Disk identifier: 0x27dd27dc

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/sdc: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3224498923  [COLOR="Red"]**3657370039**[/COLOR]   216435558+   7  HPFS/NTFS
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(210558, 221, 10)
Partition 1 has different physical/logical endings:
     phys=(784, 0, 13) logical=(238825, 64, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ? [COLOR="Red"]**_ 3272020941 _**[/COLOR] 5225480974   976730017   16  Hidden FAT16
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(906, 235, 61) logical=(213662, 17, 20)
Partition 2 has different physical/logical endings:
     phys=(262, 116, 59) logical=(341222, 117, 13)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?           0           0           0   6f  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(0, 0, 1)
Partition 3 has different physical/logical endings:
     phys=(10, 114, 13) logical=(800994292, 156, 16)
Partition 3 does not end on cylinder boundary.
/dev/sdc4        [COLOR="Red"]**_50200576_**[/COLOR]   974536369   462167897    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(3278, 20, 45)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(63636, 236, 34)
Partition 4 does not end on cylinder boundary.


it looks like you have overlapping partitions too. you can try:
```

sudo umount /dev/sdc1
sudo ntfsfix /dev/sdc1

```
unfortunatelly it looks like you have problem with fat16 and ntfs partitions (windows filesystems). do not know if fixparts handles both these kind of file-systems. you can try also to fix these with some win booting tools.

---

### Post by Ankhwatcher on 2011-09-14
@fdrake that's just my crazy messed up (but working!) live usb-stick.

My installs have failed through Wubi.exe (only show's the C: drive) and from the a CD and from the usb stick.

Thanks,
-ANkh

---

### Post by srs5694 on 2011-09-14
> **Ankhwatcher said:**
> I am having the same sorts of problems. Here is what I'm seeing on the computer.

Please start your own thread. It gets very confusing to try to solve two peoples' problems in a single thread, even if they seem (or are!) similar. The result of two peoples' problems in one thread is often less help for both parties.

> **fdrake]it looks like you have overlapping partitions too. you can try:
 	Code:
 	sudo umount /dev/sdc1
sudo ntfsfix /dev/sdc1 
[/quote]

I recommend strongly against using any filesystem maintenance tool on any partition that's known to overlap with another one. The result can be damage to the other partition's data. As a general rule, it's best to do low-level backups of both filesystems before attempting repairs. With that done, you can adjust the partitions and *then* do filesystem repairs. That said, the details of what's appropriate depend on the specific nature of the problem. I can't seem to find the original message to which you're replying, so I don't know who posted it or what the context was.

Also, be aware that ntfsfix is *not* a full-featured NTFS repair utility said:**
> unfortunatelly it looks like you have problem with fat16 and ntfs  partitions (windows filesystems). do not know if fixparts handles both  these kind of file-systems. you can try also to fix these with some win  booting tools.

FixParts doesn't deal with filesystems at all; it's a partition maintenance tool exclusively. If you don't understand the distinction, it's this: Partitions are simple disk allocation maps -- the partition table breaks the disk into one, two, three, or more parts (partitions), each of which consumes a contiguous chunk of sectors on the disk. Partition definitions include some additional metadata, such as a partition type code, but they're very simple definitions. Filesystems, on the other hand, generally reside inside partitions. Filesystems include much more complex data structures that enable you to read, write, and otherwise manipulate files.

Tools like GParted manipulate partition tables and filesystems together, which blurs the distinction in many peoples' minds, but it's possible to operate on one without the other. Tools like fdisk, gdisk, and FixParts manage partitions without filesystems; and tools like mkfs, fsck, and resize2fs manage filesystems without touching partition definitions. Advanced filesystem and partition repair procedures often involve manipulating one type of data structure independently of the other, so such tools are very useful.

---

### Post by Ankhwatcher on 2011-09-14
> **srs5694 said:**
> Please start your own thread. It gets very confusing to try to solve two peoples' problems in a single thread, even if they seem (or are!) similar. The result of two peoples' problems in one thread is often less help for both parties.

[I did]("http://ubuntuforums.org/showthread.php?t=1843567"), but nobody responded to it.:(

Please ignore /dev/sdc, it has nothing to do with this problem.

---

