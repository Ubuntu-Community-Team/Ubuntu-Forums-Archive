---
title: "Mounting RAID1 on new install of 14.04 server"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by andy36 on 2014-08-09
I think I messed up the permissions on a fresh install of 14.04 server... which is odd because I'm pretty sure I just accepted all the defaults, but whatever.

**Background**: The purpose of the machine is to be  my personal "Dad tinkering" computer for when I have time to play around and goof on fun code, and to be a file/media server for my family the rest of the time. Windows put me in the habit of placing OS and software on one (expendable) partition or disk, then all the difficult/impossible-to-replace files on another (with a separate occasional backup of that disk). Such paranoia may not be necessary with Ubuntu, but I figure it can't hurt. So the plan for this system is to put the system on my SSD, and to improve on the user-file scheme by running a RAID1 with two other drives. I chose to use "server" instead of "desktop" because I want to learn how this all works... I figured that starting with the bare minimum and building it out slowly would help me learn.

** What I have done so far** (after installing and reinstalling and troubleshooting repeatedly... this latest attempt is the furthest I have gotten):
1. Installed 14.04 server from a usb stick onto sdc (my SSD), agreeing to the default for the "Use whole disk with LVM" option, no encryption option
2. [After troubleshooting] Rebooted into recovery mode and updated GRUB
3. Installed [FONT=courier new]ubuntu-desktop[/FONT] using [FONT=courier new]apt[/FONT] and the [FONT=courier new]--no-install-recommends[/FONT] switch
4. Ran apt-get update and apt-get upgrade just to make sure everything was cool, then rebooted a few times to confirm everything looked stable
5. Installed firefox with the Software Center
7. Downloaded unix nvidia geforce 750 Ti driver (my card), [some troubleshooting], installed "gcc" and "make," then the driver, rebooted and confirmed everything looked stable
8. Installed gparted and used it to create single whole-disk partitions on sda and sdb, flagged for raid
9. Installed mdadm and said "no" to some question about mail
10. Ran... ```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
```
... then ran watch to keep tabs on [FONT=fixedsys]mdstat[/FONT]. Waited many hours while it did its thing.
11. [After some troubleshooting] Edited [FONT=fixedsys]/etc/mdadm/mdadm.conf[/FONT] to add this at the end: [FONT=fixedsys]ARRAY /dev/md/crossroads:0 metadata=1.2 name=crossroads:0 UUID=4454f51f:02a3513d:518236a0:1c725c0a[/FONT]
12. Rebooted repeatedly, added, deleted, readded a partition to the RAID array md0, tried a dozen tiny variations on adding a line to fstab, tried to mount the array manually with [FONT=fixedsys]mount[/FONT]
13. Reached my wits' end and typed this post...

At this point, I am so confused by this I don't even know what information is relevant, so I'll add a few other bits of possibly-relevant information here and then hope the community can tell me what I have done incorrectly.

```
andy@crossroads:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0] sdb1[1]
      3906885440 blocks super 1.2 [2/2] [UU]
unused devices: <none> 
```

```
andy@crossroads:~$ sudo parted -l
Model: ATA HGST HDN724040AL (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4001GB  4001GB  ext4               raid


Model: ATA HGST HDN724040AL (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4001GB  4001GB  ext4               raid


Model: ATA PLEXTOR PX-256M5 (scsi)
Disk /dev/sdc: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   256GB  256GB  extended
 5      257MB   256GB  256GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/crossroads--vg-root: 239GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  239GB  239GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/crossroads--vg-swap_1: 17.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  17.1GB  17.1GB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md0: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags
```

```
andy@crossroads:/$ ls -l
total 85
drwxr-xr-x   2 root root  4096 Aug  6 20:59 bin
drwxr-xr-x   4 root root  1024 Aug  9 09:15 boot
drwxr-xr-x  18 root root  4440 Aug  9 10:49 dev
drwxr-xr-x 119 root root  4096 Aug  9 13:17 etc
drwxr-xr-x   2 root root  4096 Aug  8 23:34 export
drwxr-xr-x   3 root root  4096 Aug  6 20:48 home
lrwxrwxrwx   1 root root    33 Aug  6 20:44 initrd.img -> boot/initrd.img-3.13.0-32-generic
drwxr-xr-x  22 root root  4096 Aug  6 20:59 lib
drwxr-xr-x   2 root root  4096 Aug  6 21:11 lib64
drwx------   2 root root 16384 Aug  6 20:43 lost+found
drwxr-xr-x   4 root root  4096 Aug  9 10:40 media
drwxr-xr-x   2 root root  4096 Apr 10 18:12 mnt
drwxr-xr-x   2 root root  4096 Jul 22 18:48 opt
dr-xr-xr-x 194 root root     0 Aug  9 10:41 proc
drwx------   2 root root  4096 Aug  9 07:59 root
drwxr-xr-x  23 root root   840 Aug  9 10:42 run
drwxr-xr-x   2 root root 12288 Aug  8 23:33 sbin
drwxr-xr-x   2 root root  4096 Jul 22 18:48 srv
dr-xr-xr-x  13 root root     0 Aug  9 10:41 sys
drwxrwxrwt   6 root root  4096 Aug  9 13:17 tmp
drwxr-xr-x  11 root root  4096 Aug  6 21:56 usr
drwxr-xr-x  12 root root  4096 Aug  6 20:47 var
lrwxrwxrwx   1 root root    30 Aug  6 20:44 vmlinuz -> boot/vmlinuz-3.13.0-32-generic
```

```
andy@crossroads:/media/andy$ ls -l
total 4
drwxr-xr-x 2 root root 4096 Aug  9 08:02 Space
```

**My questions**:
(1) [Urgently] How do I mount the raid device manually?
(2) [Soon after 1] How do I set up fstab so the raid mounts during boot and appears as a folder called "Space"?
(3) [Eventually] How do I ensure that users such as andy (my login), and any family members I add down the road  have permission to read/write to their files and pooled files (our media and pictures)?

Thank you all for any help you can provide. I'm happy to post more information if it helps. I am also willing to wipe everything and do it all over again if that's necessary. The raid disks are blank, and I am not attached to any of the things I've done to the system. Like I said, I want to learn how this works. But I have hit a wall and could really use some help.

Andy ... [edited for clarity]

---

### Post by andy36 on 2014-08-09
Should just mention that the way this problem currently manifests itself is with this glitch during the litany of stuff that scrolls by during the boot: "An error occurred while mounting [latest attempt at making this work]. Press S to skip or ...."

And although it keeps changing as I bang my head against the wall trying to get it to work, this is the current line of fstab that doesn't work:

```
dev/md0       /home/andy/Desktop/Space      ext4          defaults     0      0
```

I have tried this both with and without a partition on md0 also trying md0p1 in the first spot
I have tried it using the device's UUID=4454f51f:0.... in the first spot
I have tried it using md127 in the first spot (this was what the md defaulted to before I changed mdadm.conf)
I have tried it using many different folders--both owned by root and owned by andy--in the second spot
I have tried it with auto instead of ext4 in the third spot
I have tried it with usr=1000 (andy's user id) in the fourth spot

This cannot be as difficult as I am making it. But yet, here I am.

---

### Post by steeldriver on 2014-08-09
AFAIK, 'mdadm --create' just creates the array device - it doesn't actually put a filesystem on it. Have you partitioned md0? what does

```
sudo file -sL /dev/md0
```
say?

---

### Post by andy36 on 2014-08-09
It returns: ```
/dev/md0: x86 boot sector
```
And if I run the same for /dev/md0p1 it returns: ```
/dev/md0p1: Linux rev 1.0 ext4 filesystem data, UUID=70fb5442-0ad1-4a5d-a589-309ff5c29641 (extents) (large files) (huge files)
```

But I think that confirms two things for me, steeldriver, this definitely won't work if I leave md0 unallocated, and I should be trying to mount md0p1, not md0. As I wait for further answers and play around more with this, I'll only run trials with dev/md0p1 in the first spot of fstab.

Thank you for your time and help!

---

### Post by steeldriver on 2014-08-09
just fyi, that needs to be [COLOR=#0000ff]**/**[/COLOR]dev/md0p1 I think

---

### Post by andy36 on 2014-08-09
Outstanding. Adding that tiny slash (solidus) has improved my situation A LOT. Now the device mounts during boot. This line of fstab ```
/dev/md0p1       /home/andy/Desktop/Space      auto          defaults     0      0
``` but it comes through owned by root, so the "andy" acccount has no access.

What option should I set to grant a user (andy) or a group of users (future group of family members) access to the device? I'll also dig up a man page or something on this, but if anyone stops by and knows the answer offhand, would be much appreciated.

Thanks again steeldriver!

---

### Post by steeldriver on 2014-08-09
imho since it's an ext4 filesystem, it would be better to let root mount it, and then have subdirectories with whatever permissions you need for access (e.g. a 'family' subdir owned by root with group 'family' to which you can add each of the family accounts - you may want to consider setting the setgid bit as well)

---

### Post by andy36 on 2014-08-09
Rock. That does it. I can take it from here. I'll mark this as solved. Have a great weekend steeldriver.

---

