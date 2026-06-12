---
title: "Read Only File System on Cloned Disk from Damaged HDD"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by AJThind on 2014-04-28
I have had a Ubuntu 9.04 installed on a P4 computer since 2009

recently in the last year I've been getting message to error check the drive I ran fsck on boot and everything worked .

in the last 2 months I got "read only file system " after about 2-4 minutes of login to USER when I try and create a new file and it won't let me create or delete anything.

So I ran Hirens boot disk and found that smart was reporting my HDD to be failing with bad sectors.

I used HD Clone 4 to copy the 40gb drive onto a brand new 40 gb drive orig was Maxtor new is seagate

upon first root as seagate as master it did error check and offered to repair files that were in bad spots etc I said yes to all and it booted fine 

Hoever after 2-4 minutes same thing read only file sytem.

I've tried everything unmount remount etc fsck from terminal today I tried to use original 9.04 live cd to boot and gparted seems to say unallocated drive everything says seagate is healthy gparted only seems to be looking for ext2 drive is ext3 

I'll post Fstab, then demsg then stuff I've tried in terminal please help 

*****Fstab output
proc /proc proc defaults 0 0
UUID=9ecc2ad8-4ada-4bd3-8343-f5efe3cab07d / ext3 relatime,errors=remount-ro 0 1
UUID=35f842e0-c8a3-471f-ba7c-9512555d9e28 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0


***********demsg log

GB/37.2 GiB)
[    1.203966] sd 0:0:0:0: [sda] Write Protect is off
[    1.203972] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.204027] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.204289]  sda: sda1 sda2 <
[    1.223334] sd 0:0:1:0: [sdb] Attached SCSI removable disk
[    1.242739]  sda5 >
[    1.242840] sda: p5 size 2971962 exceeds device capacity, limited to end of disk
[    1.243223] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.320321] ata2.01: ATAPI: Optiarc DVD RW AD-7190A, 1.01, max UDMA/66
[    1.320370] ata2.01: limited to UDMA/33 due to 40-wire cable
[    1.352227] ata2.01: configured for UDMA/33

************stuff I tried in Terminal **********


ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
ubuntu904: clean, 499983/2354688 files, 8464549/9408057 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
ubuntu904: clean, 499983/2354688 files, 8464549/9408057 blocks
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ sudo fsck /dev/hda
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No such file or directory while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
ubuntu904: clean, 499983/2354688 files, 8464549/9408057 blocks
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45088888

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4685    37632231   83  Linux
/dev/sda2            4686        4870     1486012+   5  Extended
/dev/sda5            4686        4870     1485981   82  Linux swap / Solaris
root@ubuntu:/home/ubuntu# fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
ubuntu904: clean, 499983/2354688 files, 8464549/9408057 blocks
root@ubuntu:/home/ubuntu# fsck /dev/sda2
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
root@ubuntu:/home/ubuntu# fsck /dev/sda
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:/home/ubuntu# sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x45088888

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75264524    37632231   83  Linux
/dev/sda2        75264525    78236549     1486012+   5  Extended
/dev/sda5        75264588    78236549     1485981   82  Linux swap / Solaris
root@ubuntu:/home/ubuntu# fsck -yCM /dev/dm-0
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No such file or directory while trying to open /dev/dm-0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:/home/ubuntu# sudo mount -o remount,rw '/media/SGTL MSCN'
mount: can't find /media/SGTL MSCN in /etc/fstab or /etc/mtab
root@ubuntu:/home/ubuntu# sudo mount -o remount,rw '/sda1
> sudo mount -o remount,rw '/sda1/home
mount: can't find /sda1
sudo mount -o remount,rw /sda1/home in /etc/fstab or /etc/mtab
root@ubuntu:/home/ubuntu# sudo mount -o remount,rw '/sda1            
sudo mount -o remount,rw '/sda1
mount: can't find /sda1
sudo mount -o remount,rw /sda1 in /etc/fstab or /etc/mtab
root@ubuntu:/home/ubuntu# fsck /dev/sda
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:/home/ubuntu# fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
ubuntu904: clean, 499983/2354688 files, 8464549/9408057 blocks
root@ubuntu:/home/ubuntu# fsck -a /dev/sda1
fsck 1.41.4 (27-Jan-2009)
ubuntu904: clean, 499983/2354688 files, 8464549/9408057 blocks
root@ubuntu:/home/ubuntu# fsck -a /dev/sda2
fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
root@ubuntu:/home/ubuntu# fsck -p /dev/sda2
fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
root@ubuntu:/home/ubuntu# fsck -p /dev/sda5
fsck 1.41.4 (27-Jan-2009)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5
root@ubuntu:/home/ubuntu# sudo badblocks -sv /dev/sda
Checking blocks 0 to 39082679
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.


[SIZE=3][B]
**************new hd was slightly smaller than old hdd what if I try this?[/B][/SIZE]

format new hdd
install a new vigin 9.04 from live cd/dvd onto it 
boot into live cd and copy all files and folders onto new drive saying "no " to any overwrite options

**Then would system be normal?**

I say this because I have a_ custom coded game server software_ that auto runs before gui on failing hdd ubunto 9.04 and on new seagate cloned from it.

so that if I'm in another town and system reboots due to power failure etc server is running upon power restore.

I don't know how the linux fluent guy who did this for me, made it auto run or where the run script is, I do know it's nothing to do with startup folder in gui, I watched him do it he put files into a new folder in etc and somewhere a startup script not I don't know where.  he did it all in terminal and very fast 

if it wasn't for that I'd just move to latest or newer ubuntu pref lts .  He told me if I updated the instaled ybuntu to 10 when it came out that I'd lose the game server auto running on boot as all his work would be overwritten or erased.

please help me either by getting rid of read only file system Or by locating the startup script(s) for custom game server (just found it etc rc2.d lol and exacutable in etc init.d ) not sure but I thinks thats the stuff or in those dir

---

### Post by sudodus on 2014-04-30
Welcome to the Ubuntu Forums :-)

For a cloning operation you need a target drive that is the same size or bigger. Otherwise you can get problems.

So I suggest that you get a bigger drive, and then use ***ddrescue*** to clone the content of the original drive to the target drive. The info page is very good. Read it carefully and use one of the examples (with modifications for your particular system).

Install ddrescue into a live system (on a CD/DVD/USB drive)

```
sudo apt-get install ddrescue
```

```
info ddrescue
```

Example 1 will probably help you get started.


*Edit*: If there is no reply, you can bump the thread once every day (so after 24 hours, write 'bump' in a reply)

---

