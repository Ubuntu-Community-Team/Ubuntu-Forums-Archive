---
title: "Gutsy break my FAT32 partition during install"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by shag13 on 2008-03-03
Dear all,

(following an advice i double post a thread here, while it concern Kubutu may be some of you may also help, sorry to have done so - the other one is here : [http://kubuntuforums.net/forums/index.php?topic=3091963.0](http://kubuntuforums.net/forums/index.php?topic=3091963.0))

Hello,

i'm desesperatly looking for some help, yesterday i decided it was time for a fresh installation of a Gutsy. I had a Win XP multiboot with another old distro, partitions were already setted up, (you will see that on fdisk output).

during installation, i choose a "manual" partitioning, everything looks fine except that Gutsy installer was not able to see my FAT32 partition, i think it was not a trouble and that i would have to had it manually in my fstab after installation.

I deleted the partition that used to be my old / and swap, recreate them and set them as / and swap mounting points. Set my old home as /home mounted. And then install Gutsy.

After installation my sda5 partition which was FAT32 was gone. Windows XP now see a drive E: which is not formatted, while it was and contain the kind of stuff that i should have backuped, and that i can not loose (just say my phd report... some kind of murphy's law...).

Looks like Gutsy installer change my FAT32 partition to "unknown"...

please help, i'm just only desesperate now... i know this kind of trouble must be handle the right way during the first time, or the risk is that i loose more and so i do not want to try approximate solutions

i post below the kind of command output that may help :

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="48D88748D88732EC" TYPE="ntfs"
/dev/sda6: UUID="B82877B8286CFA" TYPE="ntfs"
/dev/sda7: UUID="f3a684b1-ec16-44d8-b1d0-2c847a42d013" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda8: UUID="67a5db28-ee6e-4f56-a5af-e7924689ee64" TYPE="ext2"
/dev/sda9: UUID="ff87ba33-bf45-4282-3843-66b0ea2669f9" TYPE="swap"

=> no more sda5 here
 
ubuntu@ubuntu:~$ sudo fdisk -l
 
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71a271a2
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1828    14681488+   7  HPFS/NTFS
/dev/sda2            1828       12161    82999823    f  W95 Ext'd (LBA)
/dev/sda5            1829        4438    20964825    b  W95 FAT32
/dev/sda6            4439       10705    50334448+   7  HPFS/NTFS
/dev/sda7           11227       12030     6450538+  83  Linux
/dev/sda8           10706       11226     4184901   83  Linux
/dev/sda9           12031       12161     1052226   82  Linux swap / Solaris

=> it is here as a W95 FAT 32, that's fine but :
 
ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sda5 /media/sda5
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

=> looking for dmesg show this :
 
[ 1675.292000] FAT: invalid media value (0x31)
[ 1675.292000] VFS: Can't find a valid FAT filesystem on dev sda5.

=> from fdisk :
 
Command (m for help): v
34707 unallocated sectorsExpert command (m for help): e
 
Disk /dev/sda: 255 heads, 63 sectors, 12161 cylinders
 
Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 2 00 254  63 1023 254  63 1023   29366819  165999646 0f
 5 00 254  63 1023 254  63 1023   41929651  100678410 05
 6 00 254  63 1023 254  63 1023  150978871   12916260 05
 7 00 254  63 1023 254  63 1023  142609006    8369865 05
 8 00 254  63 1023 254  63 1023  163895131    2104515 05
 9 00   0   0    0   0   0    0          0          0 00
 
Expert command (m for help): p
 
Disk /dev/sda: 255 heads, 63 sectors, 12161 cylinders
 
Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 80   1   1    0 254  63 1023         63   29362977 07
 2 00 254  63 1023 254  63 1023   29366819  165999646 0f
 3 00   0   0    0   0   0    0          0          0 00
 4 00   0   0    0   0   0    0          0          0 00
 5 00 254  63 1023 254  63 1023          1   41929650 0b
 6 00 254  63 1023 254  63 1023       9513  100668897 07
 7 00 254  63 1023 254  63 1023      15183   12901077 83
 8 00 254  63 1023 254  63 1023         63    8369802 83
 9 00 254  63 1023 254  63 1023         63    2104452 82
 
=> i did not know what to do with the two previous, but it may help one of you

=> i had try gparted live distro, it tell me "unknown" as filesystem type and show an exclamation mark. I do not know how to use gparted to have more infos or repairing, may be could you help ?

=> i had find a tools that is called testdisk and that looks like being able to do something but it is desesperatly complicated to use and i do not want to do THe wrong thing that will crash the whole disk
- that is not backuped yet, for the other working partitions, i must go and buy a disk with enough space for that Sad ... damned... Sad -
here are some outputs that may help :

=> Analyse :

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1  1827 194 63   29362977
 2 E extended LBA          1827 254 63 12160 254 63  165999646
test_FAT : Boot sector doesn't have the endmark 0xAA55
 5 L FAT32                 1828   0  1  4437 254 63   41929650
 5 L FAT32                 1828   0  1  4437 254 63   41929650
   X extended              4438   0  1 10704 239 63  100678410
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 6 L HPFS - NTFS           4438 151  1 10704 239 63  100668897
   X extended             11226   0  1 12029 254 63   12916260
 7 L Linux                11226 241  1 12029 254 63   12901077
   X extended             10705   0  1 11225 254 63    8369865
 8 L Linux                10705   1  1 11225 254 63    8369802
    Next
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

=> i do not undestand why there is two entry for 5 L FAT32, not the sense of the warnings i googled with that but was not able to get the point (my english is not enough ok to understand so well)

=> if i continue with proceed i have this output that i do not undestand at all :

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  1827 254 63   29366757
D FAT32 LBA             1827 196  1  4438 254 63   41949432 [FAT32]
D HPFS - NTFS           4438 151  1 10704 254 63  100669842
D Linux                10704 241  1 11226 254 63    8386812
D Linux                11226 241  1 12029 254 63   12901077
L Linux Swap           12030   1  1 12160 254 63    2104452

=> what are the D in first column i just do not know. Last line is shwoed in green.
When using the P command to list files, looks like files are in the right places, but i can only see them, it do not propose a copy or something else.

=> continuing without doing something i had :

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63

     Partition                  Start        End    Size in sectors

 1 E extended LBA         12030   0  1 12160 254 63    2104515
 5 L Linux Swap           12030   1  1 12160 254 63    2104452

=> and then i am stuck here, i do not want to do any writing (there is a Write command and  i do not want an hazardous modifications while not being sure that is the right one...

=> using advanced menu :

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63

     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  1827 194 63   29362977
 2 E extended LBA          1827 254 63 12160 254 63  165999646
 5 L FAT32                 1828   0  1  4437 254 63   41929650
   X extended              4438   0  1 10704 239 63  100678410
 6 L HPFS - NTFS           4438 151  1 10704 239 63  100668897
   X extended             10705   0  1 11225 254 63    8369865
 8 L Linux                10705   1  1 11225 254 63    8369802
   X extended             11226   0  1 12029 254 63   12916260
 7 L Linux                11226 241  1 12029 254 63   12901077
   X extended             12030   0  1 12160 254 63    2104515
 9 L Linux Swap           12030   1  1 12160 25Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63
     Partition                  Start        End    Size in sectors
 5 L FAT32                 1828   0  1  4437 254 63   41929650

=> and going on FAT32

Boot sector
test_FAT : Boot sector doesn't have the endmark 0xAA55

Backup boot sector
test_FAT : Boot sector doesn't have the endmark 0xAA55

First sectors (Boot code and partition information) are not identical.
Second sectors (cluster information) are not identical.
Third sectors (Second part of boot code) are not identical.

A valid FAT Boot sector must be present in order to access
any data; even if the partition is not bootable.

[  Quit  ]  [Rebuild BS][  Dump  ]  [Repair FAT]

=> i do not know what to do with these commands [Rebuild BS], [Dump] and [Repair FAT]
=> i do not understand this "test_FAT : Boot sector doesn't have the endmark 0xAA55" and others output... Even after googl-ing them

that's all i can do for now Sad

hope that someone would be able to help...

ps : on Windows, the drive is still here, but looks unformated, with no space/used space, clicking on it show me a command like 'do you want to format this drive now?". I can not do that !

=>  booting from a livecd did not help, nor does GParted live, (as far i understand how to use it, but here, some gparted expert may help me. I just use it for trying to understand something, but was not able to)

it looks like while writing partition tables during installation for its / and swap partition, (that i had deleted and recreated) Gutsy had decided to rewrite the one that used to be FAT32 with some kind of "unknown"/"invalid" partition, file system or flag that i just do not know how to recover. I can not understand why it has chosen to do something in a place where it should'nt have do anything Sad

i will not be able to post more for like the next 10 hours, from now. But i will be very glad if some of the expert guys from here can post suggestions or any helpful advices, that i could then try later.

---

