---
title: "I want to dual boot"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by Kaninepete on 2010-02-02
I tried to install Jaunty on my new laptop because I still had the live CD laying around after my desktop died. I want to dual boot with windows 7, which came preloaded on my HP pavillion.
     The installation process on the live CD only gave me the option to overwrite all of the windows stuff, and have only ubuntu. Do I need to make room for the new partion first? I don't remember doing that before.
     
      Also, on the live CD, I didn't have sound. Will I be able to fix that easily?

---

### Post by oldfred on 2010-02-02
How many partitions has the system used?  They often have a hidden recovery or two and may have used all 4 primary partitions.

It is much better to use win7 tools to shrink the windows partition and reboot several times into windows to make sure it works ok after the resize. Many blame grub/ubuntu for windows issues with a resize.

from liveCd this will tell number of partitions:
sudo fdisk -l  (el not 1 or I)

---

### Post by Kaninepete on 2010-02-02
I can see from the windows partition editor thing that it has four.

SYSTEM 199MB
(C: ) 450.13GB
RECOVERY(D: ) 15.33GB
HP_TOOLS 103MB

None of them strike me as being useless. I don't know what HP_TOOLS actually does, but I'm afraid to delete it. 
What do you suggest?

---

### Post by oldfred on 2010-02-02
You cannot delete system or C: without having to totally reinstall windows. That leaves recovery. What does your recovery have? It often is a way to write a repair CD and possibly to reimage your hard drive to the way it was the day you purchased it. If it lets you write that to a DVD I would do that and write the repair CD. (you should have done this as this is the only way to recover from a hard drive failure). If it only works from the partition and you do not want to delete it, you have to add another drive.

---

### Post by OrangeCrate on 2010-02-02
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Goldcoin on 2010-02-02
Use Window's disk software (that is already built in) to partition the disk, leaving at least 10GB for Ubuntu.

---

### Post by Kaninepete on 2010-02-02
I made the recovery DVDs.
I would rather not delete the recovery partition because I don't know if it is equivalent to them or not.

Can I just shrink windows as goldcoin says, or is there a problem with having more than 4 partitions?
I'm hardly using any of my 500GB, so that would be my prefered method.

---

### Post by kansasnoob on 2010-02-02
I would boot the Ubuntu Live CD choosing to try without changes and then run the command from terminal:

```
sudo fdisk -l
```

BTW that's a lower case L.

If you have only one drive it's probably sda so run:

```
sudo parted /dev/sda print
``` 

**EXAMPLE**:

```
lance@lance-desktop:~$ **sudo fdisk -l**
[sudo] password for lance: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            3764       19457   126062055    5  Extended
/dev/sda3            2678        3763     8723295   83  Linux
/dev/sda5            3764        4799     8321638+  83  Linux
/dev/sda6            4800        9284    36025731   83  Linux
/dev/sda7            9285       10301     8169021   83  Linux
/dev/sda8           10302       12215    15374173+  83  Linux
/dev/sda9           14880       15032     1228941   82  Linux swap / Solaris
/dev/sda10          15033       17103    16635276   83  Linux
/dev/sda11          17104       17870     6160896   83  Linux
/dev/sda12          17871       19457    12747546   83  Linux
/dev/sda13          12216       13046     6674976   83  Linux
/dev/sda14          13047       14879    14723541   83  Linux

Partition table entries are not in disk order
lance@lance-desktop:~$ **sudo parted /dev/sda print**
Model: ATA WDC WD1600AAJB-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  22.0GB  22.0GB  primary   ntfs            boot
 3      22.0GB  31.0GB  8933MB  primary   ext3
 2      31.0GB  160GB   129GB   extended
 5      31.0GB  39.5GB  8521MB  logical   ext3
 6      39.5GB  76.4GB  36.9GB  logical   ext3
 7      76.4GB  84.7GB  8365MB  logical   ext3
 8      84.7GB  100GB   15.7GB  logical   ext3
13      100GB   107GB   6835MB  logical   ext3
14      107GB   122GB   15.1GB  logical   ext3
 9      122GB   124GB   1258MB  logical   linux-swap(v1)
10      124GB   141GB   17.0GB  logical   ext3
11      141GB   147GB   6309MB  logical   ext3
12      147GB   160GB   13.1GB  logical   ext3

lance@lance-desktop:~$ 

```

You can see that the latter command is very "human readable :P

If you have 4 primary partitions you'll need to copy and then delete some partition to an external source, then create an extended partition and copy it back as a logical partition, and then create the partitions for Ubuntu.

**Do not move any Windows partition needed for booting Windows!**

---

