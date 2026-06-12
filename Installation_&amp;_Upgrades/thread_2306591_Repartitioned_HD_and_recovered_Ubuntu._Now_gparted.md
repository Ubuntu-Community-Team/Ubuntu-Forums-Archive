---
title: "Repartitioned HD and recovered Ubuntu. Now gparted error Overlapping Partitions"
date: 2015-12-16
forum: Installation &amp; Upgrades
---

### Post by abbyhageman on 2015-12-16
I have dual boot Windows 10 and Ubuntu 15.10. Windows on primary drive.  Ubuntu, Ubuntu swap, and windows data on secondary drive in 3 partitions. I ran out of room in Ubuntu. So I wanted to resize the secondary drive partitions to make room.

I don't know a lot about ubuntu or I probably would have known a better way to backup and recover ubuntu. So I used Acronis 2014 to backup my secondary drive partitions on a external drive. Then I deleted all partitions from the secondary drive and created new ones in different sizes. Then I copied back the partition backups (one ubuntu, one swap, one windows data) to the new partitions.  I can boot into Windows 10 just fine, data on secondary is fine. I can boot into Ubuntu just fine. The problem is that when I opened gparted to check the partitions I got the error: 
     Libparted Bug Found! 
        Can't have overlapping partitions. 
                  Cancel    Ignore

I click ignore and select the secondary disk. It shows two duplicate partitions greyed out that shouldn't be there. I can't do anything with them. The other partitions are there, but squished in the middle of the two greyed out ones. I go into Windows 10 and look at the partitions and they look perfect. 

I have a hunch that something broke from the move, but I have no idea what. I don't get it. Any ideas?  Suggestions? Please talk to me like a newbie. Thank you in advance. 

P.S.  I still have the backups, and I haven't tried to boot with a live disk and reinstall, either. Just not sure what would be easiest, fastest fix.
[ATTACH=CONFIG]266203[/ATTACH][ATTACH=CONFIG]266204[/ATTACH][ATTACH=CONFIG]266205[/ATTACH]

---

### Post by oldfred on 2015-12-16
Post these:
 sudo parted /dev/sda unit s print

 sudo parted /dev/sdb unit s print
sudo fdisk -lu

---

### Post by abbyhageman on 2015-12-16
Ok here it is :}

```
abby@Abby-Laptop-Ubuntu:~$ sudo parted /dev/sda unit s print
[sudo] password for abby: 
Model: ATA Crucial_CT256MX1 (scsi)
Disk /dev/sda: 500118192s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start     End         Size        File system  Name                          Flags
 1      2048s     923647s     921600s     ntfs         Basic data partition          hidden, diag
 2      923648s   1128447s    204800s     fat32        EFI system partition          boot, esp
 3      1128448s  1161215s    32768s                   Microsoft reserved partition  msftres
 4      1161216s  500115455s  498954240s  ntfs                                       msftdata


``````
abby@Abby-Laptop-Ubuntu:~$ sudo parted /dev/sdb unit s print
Error: Can't have overlapping partitions.
Ignore/Cancel? ignore                                                     
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sdb: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End          Size         Type      File system     Flags
 1      440403968s  1953523711s  1513119744s  primary   ntfs
 2      2048s       440403968s   440401921s   extended
 5      4096s       419432447s   419428352s   logical   ext4
 6      419434496s  440403967s   20969472s    logical   linux-swap(v1)
```

```
abby@Abby-Laptop-Ubuntu:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 5A4C1F99-35B6-44A1-ACFA-6BDE3072D447

Device       Start       End   Sectors   Size Type
/dev/sda1     2048    923647    921600   450M Windows recovery environment
/dev/sda2   923648   1128447    204800   100M EFI System
/dev/sda3  1128448   1161215     32768    16M Microsoft reserved
/dev/sda4  1161216 500115455 498954240 237.9G Microsoft basic data


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9e2c082a

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sdb1       440403968 1953523711 1513119744 721.5G  7 HPFS/NTFS/exFAT
/dev/sdb2            2048  440403968  440401921   210G  5 Extended
/dev/sdb5            4096  419432447  419428352   200G 83 Linux
/dev/sdb6       419434496  440403967   20969472    10G 82 Linux swap / Solaris

Partition table entries are not in disk order.


Disk /dev/sdc: 3.7 TiB, 4000787025920 bytes, 976754645 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 268431360 bytes
Disklabel type: dos
Disk identifier: 0x2275df8b

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdc1        2048 976752639 976750592  3.7T  7 HPFS/NTFS/exFAT


Disk /dev/sdd: 2.7 TiB, 3000558944256 bytes, 732558336 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000246c6

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdd1         256 732558335 732558080  2.7T  7 HPFS/NTFS/exFAT
```

---

### Post by oldfred on 2015-12-17
I do not see overlap, but you do not have a one sector space between the end of sdb2 the extended partition and the start of sdb1. Do not know all of details of partition rules, but think there is a one sector requirement somewhere.

       First backup partition table, use your drive for sdX or sda, sdb etc. copy to another device.
sudo sfdisk -d /dev/sdX > parts.txt
sudo sfdisk -d /dev/sdb > parts_sdb.txt 

See if fixparts will rewrite partition table. Not sure it will as not normally for overlapping issues. But the one sector may be something it can change easily.

 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Otherwise we may have to manually edit the parts_sdb.txt and reinstall it.

Since you now have an UEFI hardware system and gpt partitioning on sda, you should plan on using gpt for all new or all drives totally reformatted. Windows only boots from gpt partitioned drives with UEFI. I started converting drives to gpt years ago, kept XP on MBR(msdos) but had all other new drives as gpt.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by abbyhageman on 2015-12-17
I will give this a shot. Thank you so much for taking the time to help me. :)

---

### Post by abbyhageman on 2015-12-17
Success!  Thank you so much! The error is gone! 

I ended up using the fixparts program in Windows because for some reason I couldn't get it to install in Ubuntu. 

When I ran it- it said there was some GPT info but it wasn't a GPT formatted disk, and asked me if I wanted to delete it. I typed yes. Then I didn't know exactly what else to do so I made the other two partitions primary rather than logical. Then I exited. 

I then checked the partitions on that disk in Windows and decided to shrink the last partition by a smidge. Exited. Booted into Ubuntu and no problem with gparted. Yay!  Again, thank you so much. :D
  
[ATTACH=CONFIG]266206[/ATTACH](Pic or it didn't happen)
P.S.  I will format GPT in the future, thank you for the information.

---

### Post by oldfred on 2015-12-17
Glad you were able to fix it. :)

---

