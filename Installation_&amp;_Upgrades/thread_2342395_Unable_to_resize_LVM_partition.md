---
title: "Unable to resize LVM partition"
date: 2016-11-06
forum: Installation &amp; Upgrades
---

### Post by cobalt2 on 2016-11-06
I'm trying to reduce my lvm in order to expand the boot partition before it. I want to expand the boot partition from 100 MiB to 286 MiB. On the vg there were 3 lvs: 

dev/lubuntu/os
dev/lubuntu/home
dev/lubuntu/swap

I resized os. Then I tried to resize the partition with gparted. I got an error message: Could not shrink dev/sdd5 as later extents are allocated. When looking at the segments, I noticed that there was fragmentation. I decided to remove os and swap in order to unite the home fragments and allocate empty space at the beginning of the lvm. Then I try again to resize the partition using Gparted and again it failed. So I used resize2fs to shrink the filesystem on home to it's minimum size. Using gparted I try to resize the partition again. I allowed it to run for 4+ hours. The top bar has a useless blue bar sliding back and forth, the bottom bar is empty and there is absolutely no sign of progress. 

[ATTACH=CONFIG]272000[/ATTACH]

So I cancelled the operation, ignoring the ominous warning from Gparted of impending filesystem damage as a result of canceling the operation. Fortunately, checking the filesystem of dev/lubuntu/home with e2fsck shows that it remained intact.
 
According to pvs I have 28.23 GiB of free space at the start of dev/sdd5. I only need 187 MiB to allocate the boot partition. How to shrink the partition without having to resort to wiping out home?

---

### Post by TheFu on 2016-11-06
Always backup the entire disk before starting anything like this. It is easy to have a SW mistake or user error wipe everything.

The file system type used matters. Not all file systems can be reduced. XFS cannot be reduced, for example.
For system-level stuff like this, I don't trust any GUIs.  Use the cli versions and I usually script it to ensure there is a record and to speed it up next time.  When trying to move freed storage from inside LVM management to outside LVM management, I'd backup everything, wipe the disk, repartition as desired, manually create any file systems, pvs, vgs, lvs and manually restore all data.  

Also, if you are resizing /boot - probably want 500MB min. There are reasons, but mainly when /boot fills up, it is usually during a kernel upgrade process and it really sucks not being able to boot because /boot was filled while updating the boot files.

So - lets assume everything is fine, but we need to start over from the beginning. Post the normal **lsv**, **vgs**, **pvs** and **lsblk** output along with some **df -h** so we know current facts. Please use *code tags* - too hard to read otherwise.

---

### Post by cobalt2 on 2016-11-06
```

lvs
LV   VG      Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home lubuntu -wi-a----- 83.46g                                                    

pvs
  PV         VG      Fmt  Attr PSize  PFree 
  /dev/sdd5  lubuntu lvm2 a--  55.80g 28.23g
  /dev/sde1  lubuntu lvm2 a--  55.89g     0 

vgs
  VG      #PV #LV #SN Attr   VSize   VFree 
  lubuntu   2   1   0 wz--n- 111.69g 28.23g

lsblk
NAME             MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1             8:1    0    15G  0 part 
&#9492;&#9472;sda2             8:2    0 283.1G  0 part 
sdb                8:16   1   983M  0 disk 
&#9492;&#9472;sdb1             8:17   1   395M  0 part 
sdc                8:32   1   3.8G  0 disk 
&#9492;&#9472;sdc1             8:33   1   3.8G  0 part 
sdd                8:48   0  55.9G  0 disk 
&#9500;&#9472;sdd1             8:49   0   100M  0 part 
&#9492;&#9472;sdd5             8:53   0  55.8G  0 part 
  &#9492;&#9472;lubuntu-home 254:0    0  83.5G  0 lvm  
sde                8:64   0  55.9G  0 disk 
&#9492;&#9472;sde1             8:65   0  55.9G  0 part 
  &#9492;&#9472;lubuntu-home 254:0    0  83.5G  0 lvm  
sr0               11:0    1   248M  0 rom  
loop0              7:0    0 210.1M  1 loop /lib/live/mount/rootfs/filesystem.squashfs

df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           633M  8.6M  625M   2% /run
/dev/shm        216M  211M  4.9M  98% /lib/live/mount/medium
/dev/loop0      211M  211M     0 100% /lib/live/mount/rootfs/filesystem.squashfs
tmpfs           1.6G     0  1.6G   0% /lib/live/mount/overlay
overlay         1.6G  136M  1.5G   9% /
devtmpfs         10M     0   10M   0% /dev
tmpfs           1.6G     0  1.6G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           1.6G     0  1.6G   0% /sys/fs/cgroup
tmpfs           1.6G   28K  1.6G   1% /tmp

```

---

### Post by TheFu on 2016-11-06
Really wanted to see the **df -h** stuff on the booted system, not a live-CD boot.  You'll probably want to do all the work using a live-CD boot, so that is smart, just not what is needed now.  If the system won't boot, we'll need a mapping of the file systems to mounts.  That could be in the /etc/fstab, but might not be if UUIDs are used there.

Also, please post **sudo parted -l** output. Sorry, I should have asked for that above. If you like, remove the info for drives that are not involved ... but if they have anything to do with Linux or booting, we need to see them.

BTW, last time I lost 80% of my data (about a decade ago) was because I'd merged 2 disks into a single LV.  Just sayin'.  I didn't have backup religion back then, so it was entirely my fault.

---

### Post by cobalt2 on 2016-11-06
I dont have access to the fstab right now, so I recreated it:
```

fstab

<filesystem>      <mount>
dev/lubuntu/swap
dev/lubuntu/os    /
dev/lubuntu/home  /home
LABEL=boot        /boot

parted -l

Model: Memorex TRAVELDRIVE 005B (scsi)
Disk /dev/sdb: 1031MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  415MB  414MB  primary  ext4         boot


Model:   (scsi)
Disk /dev/sdc: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4010MB  4009MB  primary  fat32        boot


Model: ATA OCZ-REVODRIVE3 (scsi)
Disk /dev/sdd: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ext4         boot
 2      107MB   60.0GB  59.9GB  extended
 5      107MB   60.0GB  59.9GB  logical                lvm


Model: ATA OCZ-REVODRIVE3 (scsi)
Disk /dev/sde: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  60.0GB  60.0GB  primary               lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/lubuntu-home: 89.6GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  89.6GB  89.6GB  ext4
```

I'm using a flash drive for booting. I want to add a boot partition to my SSD as a backup. I have already backed up my home partition ofcourse.

---

### Post by cobalt2 on 2016-11-08
Any ideas? If not I'm going to just delete the lvm and rebuild.

---

### Post by ian-weisser on 2016-11-08
Why did you originally choose an LVM filesystem?
Why does that reason no longer apply?

100MB indeed seems too small to safely hold three kernels and initrds.

You can use LVM tools to shrink the LVM partition, then parted/gparted to grow /boot. However, it requires care and attention to detail so the released space is properly adjacent to /boot.

---

### Post by TheFu on 2016-11-08
> **cobalt2 said:**
> Any ideas? If not I'm going to just delete the lvm and rebuild.

My answer (previously provided):
>  When trying to move freed storage from inside LVM management to outside LVM management, I'd backup everything, wipe the disk, repartition as desired, manually create any file systems, pvs, vgs, lvs and manually restore all data. 

As long as the directories "appear" to be in the same location, it will be fine. Only the boot config and /etc/fstab need know about LVM or any encryption being used.  I've never felt bad wasting 500MB too much for /boot. Not once.  Of course, I remember the days of 40MB HDDs too and the idea that 64GB of SSD fits into something the size of my pinky finger nail is just amazing AND provides 180MBps throughput!

```
$ df -h
Filesystem                                                               Size  Used Avail Use% Mounted on
/dev/sda1                                                                472M  110M  338M  25% /boot

```  Been burned a few times by not having enough room there. I'm very happy seeing extra space there.  

Just to be clear, there might be easier ways to accomplish this - I just don't know any.

---

