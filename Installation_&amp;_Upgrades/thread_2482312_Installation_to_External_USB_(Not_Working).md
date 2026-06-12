---
title: "Installation to External USB (Not Working)"
date: 2022-12-28
forum: Installation &amp; Upgrades
---

### Post by jebeals on 2022-12-28
Hi everyone,

I am a new Linux user and I am trying to install Ubuntu onto an external 2 TiB USB drive from a Ventoy .iso live instance. Ideally, I'd actually like to install both Linux and Debian (and allow for room for other distros) on the USB drive and make it multi-booted, but after researching how to do this and partition it properly, I have found that I am not even able to install one LINUX OS to the external drive in the first place...

For some context, I am using UEFI booting, so I am creating a partition for the EFI booter ~400-1000MB and at least one ext4 partition that attempts to mount the root '/' on that partition. Each time I try to install Linux, both Ubuntu and Debian, I am met with:
```
The attempt to mount a file system with type vfat in SCSI1 (0,0,0), partition #1 (sda) at /boot/efi failed.
You may resume partitioning from the partitioning menu.
```
occurred when other boot/esp flags were present on other drives' devices. I took those off, seemingly bypassing this and installing the boot loader at the correct location, but then I get this error, repeatedly:

```
The attempt to mount a file system with type ext4 in SCSI5 (0,0,0), partition #2 (sdc) at / failed.
You may resume partitioning from the partitioning menu.
```

To be clear,  this is happening in both Debian and Ubuntu installation attempts when the apparent correct partitioning scheme was selected (EFI, ext4 space to mount the root, swap, etc.). It is barring me from continuing the installation.

I have used ```
sudo gdisk /dev/sdX 'o' 'w'; 'x' 'z' 
``` commands (from live ubuntu) many times as well as verifying if the disk is okay or not. Its kind of a toss up. Lots of times it says it has no problems and many other times it says the GPT Partitioning table is corrupted and strongly recommends I repair it. This "GPT Partitioning Table is corrupt but Primary is OK" also frequently occured when partitioning the drive in a tool like GParted. My strategy for reparation has been to zap it and install a new table with a new protective MBR, for the most part. 


I am afraid there is some weird disk issues going on with my USB drive.
I will list some commands showing the health/information about my drive. Some thing I have noticed but do not understand is that HPA is indeed enabled and that I always have a protective MBR with a GPT partition inside of it.

Current state of gdisk checks:
```
ubuntu@ubuntu:~$ sudo gdisk /dev/sdc GPT fdisk (gdisk) version 1.0.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): v

No problems found. 3749164989 free sectors (1.7 TiB) available in 2
segments, the largest of which is 3749162975 (1.7 TiB) in size.

Command (? for help): p
Disk /dev/sdc: 4282368000 sectors, 2.0 TiB
Model: ProductCode     
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 1B4A9CD7-11EE-41B9-BA2F-B8349F3A01C4
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 4282367966
Partitions will be aligned on 2048-sector boundaries
Total free space is 3749164989 sectors (1.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1953791   953.0 MiB   EF00  
   2         1953792       501954559   238.4 GiB   8300  
   3       501954560       533204991   14.9 GiB    8200  

```

```
[COLOR=#26A269]**ubuntu@ubuntu**[/COLOR]:[COLOR=#12488B]**~**[/COLOR]$ sudo hdparm -N /dev/sdc 
/dev/sdc: SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  max sectors   = 0/1, HPA is enabled
```

more hdparm info:
```
ubuntu@ubuntu:~$ sudo hdparm /dev/sdc

/dev/sdc:
 multcount     =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 266565/255/63, sectors = 4282368000, start = 0
ubuntu@ubuntu:~$ sudo hdparm -I /dev/sdc

/dev/sdc:

ATA device, with non-removable media
Standards:
    Likely used: 1
Configuration:
    Logical        max    current
    cylinders    0    0
    heads        0    0
    sectors/track    0    0
    --
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:           0 MBytes
    device size with M = 1000*1000:           0 MBytes 
    cache/buffer size  = unknown
Capabilities:
    IORDY not likely
    Cannot perform double-word IO
    R/W multiple sector transfer: not supported
    DMA: not supported
    PIO: pio0
 
```
lastly, fdisk output:
```
ubuntu@ubuntu:~$ sudo fdisk /dev/sdc

Welcome to fdisk (util-linux 2.37.2).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): p
Disk /dev/sdc: 1.99 TiB, 2192572416000 bytes, 4282368000 sectors
Disk model: ProductCode     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1B4A9CD7-11EE-41B9-BA2F-B8349F3A01C4

Device         Start       End   Sectors   Size Type
/dev/sdc1       2048   1953791   1951744   953M EFI System
/dev/sdc2    1953792 501954559 500000768 238.4G Linux filesystem
/dev/sdc3  501954560 533204991  31250432  14.9G Linux swap

Command (m for help): v
No errors detected.
Header version: 1.0
Using 3 out of 128 partitions.
A total of 3749164989 free sectors is available in 2 segments (the largest is 1.7 TiB).

```

Lastly, there is a warning on my ext4 partition (/dev/sdc2) in GParted:
```

<i>Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          c4243b6b-9612-4bfd-a859-c2b3d765997c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent 64bit flex_bg sparse_super large_file huge_file dir_nlink extra_isize metadata_csum
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              15630336
Block count:              62500096
Reserved block count:     3125004
Overhead clusters:        1258681
Free blocks:              61241408
Free inodes:              15630325
First block:              0
Block size:               4096
Fragment size:            4096
Group descriptor size:    64
Reserved GDT blocks:      1024
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Tue Dec 27 22:03:35 2022
Last mount time:          n/a
Last write time:          Tue Dec 27 22:06:16 2022
Mount count:              0
Maximum mount count:      -1
Last checked:             Tue Dec 27 22:05:04 2022
Check interval:           0 (<none>)
Lifetime writes:          5283 kB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     32
Desired extra isize:      32
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      d678bd42-1ca4-426e-a1c8-e385914d1b73
Journal backup:           inode blocks
FS Error count:           1
First error time:         Tue Dec 27 22:06:16 2022
First error function:     ext4_find_extent
First error line #:       925
First error inode #:      8
First error err:          EFSCORRUPTED
Last error time:          Tue Dec 27 22:06:16 2022
Last error function:      ext4_find_extent
Last error line #:        925
Last error inode #:       8
Last error err:           EFSCORRUPTED
Checksum type:            crc32c
Checksum:                 0x039e9b34</i>

<i>dumpe2fs 1.46.5 (30-Dec-2021)
dumpe2fs: Corrupt extent header while reading journal super block</i>

<i>Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+.</i>

```

I don't totally believe my disk is corrupt, but there is some weird stuff going on that I just can't figure out. The last warning message seems to indicate the superblock header in the ext4 journal is corrupt, which could be because of some other corruption/misalignment in the disk? I'm not really sure...
Any help much appreciated! Thanks in advance!!

-Jason

---

### Post by oldfred on 2022-12-28
Does HDD have separate power supply.
I found my USB to SATA adapter with just USB power worked great with my SSD, but would not even power up my old HDD.
I have used many flash drives for multiple installs. Usually one full install and many ISO. I do not use ventoy as I started using grub2's loopmount to directly boot ISO.

Ubuntu's Ubiquity installer has a very old bug, that is still current. It only wants to install grub's UEFI boot files to first drive's ESP - efi system partition. 
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. 
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

With multiple installs, I prefer to keep /home inside / (root), but then have a large data partition that I can mount in all the installs. As long as user is 1000, ownership & permissions are not an issue. My installs are mostly Ubuntu or flavors of Ubuntu so not an issue. 

If issues on partitions, have you tried fsck?
To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

