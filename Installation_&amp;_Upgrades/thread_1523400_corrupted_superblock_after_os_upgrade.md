---
title: "corrupted superblock after os upgrade"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by rwohlhueter on 2010-07-03
While negotiating an automatic upgrade to 10.04 generic kernel 2.6.32-23 the upgrade scrpt hung forever.  Only recourse was to force quit, reboot.  Apparently recuperated after reboot.  But usb drive (non-boot) showed up unmountable, because of superblock corruption.  Some of attempts to repair are quoted below.  Any help at rescue will be appreciated, but two issues especially puzzle me. 1) the fdisk -l command says "invalid flag WILL BE CORRECTED by w(write).  Flag to what?  manpage from fdisk shows no such option.  How could this repair be implemented.  2) mke2fs -n shows alternate superblocks, but trying to use (-b #####) any of them with e2fsck doesn't help.  Is e2fsck -n -S appropriate?  Manpages give dire warnings about using -S flag.

bobw@winter-linux: ~ (2%)> sudo e2fsck /dev/sdf
sudo e2fsck /dev/sdf
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2bobw@winter-linux: ~ (2%)> sudo e2fsck /dev/sdf
sudo e2fsck /dev/sdf
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
bobw@winter-linux: ~ (2%)> sudo e2fsck /dev/sdf
sudo e2fsck /dev/sdf
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


bobw@winter-linux: ~ (3%)> sudo fdisk -l /dev/sdf
sudo fdisk -l /dev/sdf
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093595

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   85  Linux extended
bobw@winter-linux: ~ (4%)> 

[output from cfdsik | print]

Partition Table for /dev/sdf

         ---Starting----      ----Ending-----    Start     Number of
 # Flags Head Sect  Cyl   ID  Head Sect  Cyl     Sector    Sectors
-- ----- ---- ---- ----- ---- ---- ---- ----- ----------- -----------
 1  0x00    1    1     0 0x85  254   63 60800          63   976768002
 2  0x00    0    0     0 0x00    0    0     0           0           0
 3  0x00    0    0     0 0x00    0    0     0           0           0
 4  0x00    0    0     0 0x00    0    0     0           0           0





bobw@winter-linux: ~ (6%)> sudo mke2fs -n /dev/sdf
sudo mke2fs -n /dev/sdf
mke2fs 1.41.11 (14-Mar-2010)
/dev/sdf is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
30531584 inodes, 122096646 blocks
6104832 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000

bobw@winter-linux: ~ (7%)>

but the alternate superblock is apparently not read ...... ditto with -b set to any of these blocks:

bobw@winter-linux: ~ (7%)> sudo e2fsck -b 32768 /dev/sdf
sudo e2fsck -b 32768 /dev/sdf
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

bobw@winter-linux: ~ (8%)>

---

### Post by oldfred on 2010-07-03
Not sure if this will help:

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Should you not have partitions on your sdf drive?
From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

