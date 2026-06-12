---
title: "Option to replace existing 13.10 installation led to removal of windows 8"
date: 2013-12-17
forum: Installation &amp; Upgrades
---

### Post by Djalmahal on 2013-12-17
Hi,

I was planning to dual boot Windows 8 and 13.10 on a friends computer. After installing 13.10 I had a working 13.10 and no windows/grub2 option upon boot. I ran boot-repair and had the options at grub2 to boot Windows and 13.10. Windows worked fine, 13.10 ended up at a purple screen and stopped. So I decided to install 13.10 again (boot-repair had downloaded new kernels which I assumed messed up the graphics).

WHILE RUNNING THE INSTALLER I CLICKED ON "REPLACING EXISTING 13.10 installation", assuming it would do exactly that, leaving the other partitions intact.

I ended up with a computer that boots 13.10 fine, I ran boot-repair to update grub2, I end up with only Ubuntu as a grub2 option. I check gparted and the installer deleted all partition except for the boot and swap.

I think that's pretty bad.

HDD setup after first install of 13.10:```
[INDENT]============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       923,647       921,600 Windows Recovery Environment (Windows)
/dev/sda2         923,648     1,456,127       532,480 EFI System partition
/dev/sda3       1,456,128     1,718,271       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,718,272   939,442,881   937,724,610 Data partition (Windows/Linux)
/dev/sda5     955,070,464   976,773,119    21,702,656 Windows Recovery Environment (Windows)
/dev/sda6     939,444,224   945,373,183     5,928,960 Swap partition (Linux)
/dev/sda7     945,373,184   955,070,463     9,697,280 Data partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    31,266,815    31,266,784   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2E3689F63689BEF9                       ntfs       System
/dev/sda2        A48B-0AB2                              vfat       
/dev/sda3        46A88C75A88C6571                       ntfs       
/dev/sda4        B0188EF6188EBABC                       ntfs       TI10657600C
/dev/sda5        CA9C9DB19C9D9891                       ntfs       Recovery
/dev/sda6        d9d43936-e86b-4e9c-ac08-1ddb6a7fecdc   swap       
/dev/sda7        00f78a87-e2ff-4516-8441-4fdc42fe0132   ext4       
/dev/sdb1        7C45-54B0                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================
[/INDENT]


```
HDD setup after second install of 13.10:```
[INDENT]
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   969,232,383   969,230,336  83 Linux
/dev/sda2         969,234,430   976,771,071     7,536,642   5 Extended
/dev/sda5         969,234,432   976,771,071     7,536,640  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    31,266,815    31,266,784   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0b636ca3-42e2-463c-b483-02b24ebb7d87   ext4       
/dev/sda5        1ad1ed4f-480f-4b9b-bab2-eefb7f5a69e7   swap       
/dev/sdb1        7C45-54B0                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
[/INDENT]

```
So, is this a bug in the installer or was I foolish to assume that "replace existing 13.10 installation" would leave the Windows 8 partition and recovery partition intact?

---

### Post by Djalmahal on 2013-12-17
Link to the HDD setup after the first install:

[http://paste.ubuntu.com/6584807/](http://paste.ubuntu.com/6584807/)

Link to the HDD after 2nd install:

[http://paste.ubuntu.com/6589163/](http://paste.ubuntu.com/6589163/)

---

### Post by oldfred on 2013-12-17
Added code tags. You can add them easily in advanced editor with # icon.

I do not know screen you get after first install? Attached is the screen I get with many installs, but I always use Something else and manually choose which partition to reinstall into.

ubiquity is the installer, which you would file bug report again.
I have seen others with the issue when choosing LVM or encrypted, but the old alternative installer always called those full drive installs.

 bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

Did you backup Windows before installing Ubuntu?
If not you may be able to get a copy of the recovery partition from your vendor for a nominal charge. Otherwise you have to purchase a full new copy of Windows. Only the vendor's version of Windows will use the product key stored in the UEFI.

---

### Post by Djalmahal on 2013-12-17
The first screenshot was what I got with the first install, I chose something else, shrank Windows 8, made a ext4 partition as / and installed 13.10.
The second install there was a new option that offered to "replace existing 13.10 installation". I clicked that and it took over the whole HDD.

And no, I was stupid enough not to back up.

---

### Post by oldfred on 2013-12-17
Ubuntu writes to entire / partition, but only a small amount of data. But it only takes one bit to corrupt an install, so it is unlikely that you can recover a working system. If you had any data you can possibly use several tools.
But STOP using system as anything overwrites more data.

You can see if you can recover old partitions with testdisk. It finds all old versions of partition table, but since you have first boot report you know sizes and partitions you had. Testdisk uses CHS not sectors but you should be able to tell.
Only if very lucky you may be able to recover recovery partition.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Some also suggest Windows tools work better for Windows, but they may charge.
 For NTFS 
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)

---

### Post by Djalmahal on 2013-12-17
I assume I should use Testdisk from a Live-USB?

---

### Post by Djalmahal on 2013-12-17
This is the output of Testdisk so far, it's still running....

---

### Post by oldfred on 2013-12-17
It may take a while with larger drives. And since you resized partitions it will find multiple versions of the same partitions. If it lets you recover partitions, you have to select the partitions that are the version that was from your first boot script. You cannot have overlapping partitions which would be some combination of old & new versions.

---

