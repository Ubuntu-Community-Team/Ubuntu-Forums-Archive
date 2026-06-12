---
title: "What partition table does the ubuntu 12.04 installer make?"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by The Phone on 2013-06-23
What partition table does the Ubuntu 12.04 live CD installer make? Or can you choose that?


  Or should I use Gparted when I make the partitions for best compatibility (ms-dos)?


  Regards


  The Phone

---

### Post by dino99 on 2013-06-23
by default, the ubuntu installer, aka ubiquity, offer an automatic partitioning : / (root) & swap
but you also can select "something else" choice, aka the manual way, to set the partitions as you need/want (usually users prefer a separate /home partition for security, instead of the default home folder)

[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by The Phone on 2013-06-23
> **dino99 said:**
> by default, the ubuntu installer, aka ubiquity, offer an automatic partitioning : / (root) & swap
but you also can select "something else" choice, aka the manual way, to set the partitions as you need/want (usually users prefer a separate /home partition for security, instead of the default home folder)

[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

So if I do it manually with gparted I can make this partition scheme without problem?


8 gb swap partition

/ (root) 30 gb ext4

---

### Post by grahammechanical on 2013-06-23
It is natural for a Linux distribution to be installed on a Linux/open source file system. I do not think it is possible to install Ubuntu on some of the Microsoft file systems. I say "some" because I have a live Ubuntu USB stick and this is what the Disks utility says about its file system.

FAT (32) Partition Type W95 FAT 32 (LBA) (Bootable).

I doubt very much if a Microsoft OS would install on anything other than a Microsoft file system. I wonder if Windows 8 would install on FAT 32?

In what way would you need compatibility?  Ubuntu can do this:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

I do not think that Microsoft returns the compliment by giving read/write abilities to Linux/open source file systems.

Regards.

P.S. in response to your second post. From the posts I have seen on this forum I would say that you must use Windows utilities to create space on the hard disk for Ubuntu and its partitions. Afterward you must defrag Windows at least twice and make sure that you can boot into Windows before starting to install Ubuntu. I do not think that it is wise to use Gparted to resize Windows partitions.

---

### Post by The Phone on 2013-06-23
> **grahammechanical said:**
> It is natural for a Linux distribution to be installed on a Linux/open source file system. I do not think it is possible to install Ubuntu on some of the Microsoft file systems. I say "some" because I have a live Ubuntu USB stick and this is what the Disks utility says about its file system.

FAT (32) Partition Type W95 FAT 32 (LBA) (Bootable).

I doubt very much if a Microsoft OS would install on anything other than a Microsoft file system. I wonder if Windows 8 would install on FAT 32?

In what way would you need compatibility?  Ubuntu can do this:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

I do not think that Microsoft returns the compliment by giving read/write abilities to Linux/open source file systems.

Regards.

I have no plan on having windows filesystem anywhere on my disk. I just don't know what partition table the ubuntu installer uses.

```
However, in practice, only certain LBA-48 enabled operating systems, including Linux, FreeBSD and Windows 7[SUP][[16]]("http://en.wikipedia.org/wiki/Master_boot_record#cite_note-Smith_2011_gdisk-18")[/SUP]  that use 64-bit sector addresses internally actually support this. Any  operating system using 32-bit sector addresses internally would cause  addresses to wrap around and thereby result in serious data corruption.
```  

So if you take a windows 7 formatted disk in a xp machine serious corruption will accrue. I just wondering if the ubuntu installer uses ms-dos partition table or what. There is several versions of it. 

My other question was if it's okey with just a / ext4 (root) partition and a swap partition. Everywhere I read people makes a partition for the /home, but that isn't necessary, right?

BTW: You can have a ms-dos partition table without having a windows filesystem.

Regards ;)

---

### Post by oldfred on 2013-06-23
How large is hard drive? Some have issues with very large / (root) partitions.

If never installing Windows you can use the newer gpt partition table. Linux can use gpt with both BIOS and UEFI, Windows only boots from gpt partitioned drives with UEFI.
 I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.


 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

I prefer smaller / (root) of 25GB and either separate /home or /mnt/data partitions for data. I multi-boot so I want the shared data partition as /home should not be shared.

      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]@The Phone;
The term "msdos" in ubuntu partitioning scheme does not equal MicroSoft Disk Operating System. Coming from a Windows world that might be a source of confusion to you.
[/COLOR][INDENT=2][COLOR=#000000]
hope that helps

[/COLOR][/INDENT]

---

