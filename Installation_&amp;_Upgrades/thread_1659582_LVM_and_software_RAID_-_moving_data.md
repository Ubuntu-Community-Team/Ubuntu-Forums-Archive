---
title: "LVM and software RAID - moving data"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by bigstoo on 2011-01-04
I have a Linux installation that currently uses a 40GB hard disk.
It is partitioned as follows:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14        4865    38973690   8e  Linux LVM

```

The disk has recently started to make a lot of noise, so I'd like to replace it before I lose data.

I have a pair of identical 160GB blank hard disks that I would like to use as a software raid1 array (The existing 30-odd GB root partition would be resized to fill the new disks).

Could anyone explain how I could get the data on to the new hardware without losing anything?

Thanks in advance

---

### Post by psusi on 2011-01-04
sudo cp -ax /source /destination

---

### Post by bigstoo on 2011-01-04
So that would copy the contents of the file system from one disk to another?

What about the MBR?

---

### Post by psusi on 2011-01-04
cp -a will copy all files, and preserve their permissions.  The -x makes it only copy files on that mount point/disk, rather than descending into directories that are mounted from another disk.

You obviously need to partition, format, and mount the destination.  If you want to make the destination bootable, you will need to install grub on it.

It looks like right now you have your root on a standalone partition, and the rest of the disk is managed by LVM.  With LVM you can simply add a new disk as a new pv, then have pvmove migrate your logical volumes off of the old pv on the fly.  I would suggest doing that for your lvm volume(s), then create a new logical volume to hold your root, rather than using a stand alone partition for that, then use cp -ax to migrate everything in the old root to the new root.  That way in the future, if you do this again, you can simply pvmove everything.

---

### Post by bigstoo on 2011-01-04
Sorry, I didn't make it clear from the partition table above.
/boot is in it's own partition. The rest of the root file system is in an LVM.

The situation I'm at now, is that I have cloned the 40GB disk to one of the 160GB disks. (I wanted the data off the dodgy disk ASAP)
Obviously, though, the 160GB has the partition table off the old disk, so only 40GB is being used.

Is it possible to resize the LVM partition so it takes up the remaining 120GB or so of the drive, without losing the data off it.

Once that's done, and I have a working single drive, is it easy enough to add the other disk as a mirror in the LVM?

---

### Post by psusi on 2011-01-04
Yes, see pvresize and lvresize.

For mirroring, you want to use mdadm to initialize the other disk as a raid1 mirror with only a single disk.  Then pvcreate and vgextend the array, then pvmove your logical volumes off of the single disk, then when you have the system working with the new single disk raid 1 array, you can pvremove and then add the second disk to the raid array.  Then you will have lvm on top of raid1.

---

### Post by bigstoo on 2011-01-05
Here's what I've done...

Firstly, I created 2 partitions on the empty new hard disk:
```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      104391   83  Linux
/dev/sdb2              14       19457   156183930   83  Linux raid autodetect

```

I then created a raid1 array with a single disk:
```
mdadm --create --verbose /dev/md0 --level=raid1 --force --raid-devices=1 /dev/sdb2
```

Then (floundering a little) I created a new LVM physical volume on the /dev/md0 device. (I used a GUI here, so I'm not 100% sure what commands are used)

Next, I moved the Logical Volume onto the new Physical Volume:
```
pvmove /dev/sda2 /dev/md0
```

Once it's all moved, I removed the original PV from the volume group:
```
pvremove -ff /dev/sda2
```

Do things look right so far?
What's the next step?
- Install grub onto /dev/sdb
- Edit fstab so that /boot mounts to /dev/sdb1

---

### Post by bigstoo on 2011-01-05
Ok. I think I've done it.

Here's my partition tables:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14       19457   156183930   fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      104391   83  Linux
/dev/sdb2              14       19457   156183930   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976758784    7  HPFS/NTFS

Disk /dev/md0: 159.9 GB, 159932219392 bytes
2 heads, 4 sectors/track, 39045952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

```

Output of pvscan
```
  PV /dev/md0   VG VolGroup00   lvm2 [148.94 GB / 0    free]
  Total: 1 [148.94 GB] / in use: 1 [148.94 GB] / in no VG: 0 [0   ]
```

I had to increase the number of disks in the array, using:
```
 mdadm --grow /dev/md0 --raid-disks=2

```

And now I get
```
Personalities : [raid1] 
md0 : active raid1 sda2[2] sdb2[0]
      156183808 blocks [2/1] [U_]
      [>....................]  recovery =  2.0% (3238144/156183808) finish=127.6min speed=19975K/sec

```

So it looks like it's working.

One question, though:
My /boot partition is sitting on /dev/sda1 and obviously isn't in a raid array. Is that a problem? Can /boot even BE in a software raid array?

---

### Post by psusi on 2011-01-05
Yes, /boot can be in a raid array, or even can be an lvm logical volume, if you are using grub2 ( the default since Ubuntu 9.10 ).

---

### Post by bigstoo on 2011-01-10
Ok. I've messed things up.

Bolstered by my newfound knowledge, I decided I would start again, but this time do it a little neater, and also create a raid array for /boot, too.
My plan was to have 2 raid arrays:
/dev/md0 -> /dev/sda1 and /dev/sdb1
/dev/md1 -> /dev/sda2 and /dev/sdb2

So, I put the old, 40GB hard disk back in the machine, along with one of the new 160GB hard disk.

I thought I would get the root filesystem moved to a new raid array first, then worry about the /boot partition later, so I simply copied the /boot partition and installed grub to the new drive.

Next I created and activated a raid array, /dev/md1, on the new drive. I extended the existing volume group to the new drive, then moved the logical volumes to this new disk and then removed the old 40GB from the VG. Everything looked right in pvscan, vgscan and lvscan. I figured I now had the data that was on the old disk, on the new disk.

However, when I reboot (after removing the 40GB drive) I get Volume Group not found. I can't see the exact error message, as it scrolls up too fast. It then, obviously, fails to mount the root filesystem.

If I boot to the Ubuntu 10.10 server cd, and choose "rescue a system", it lists bot /dev/md1 and /dev/VolGroup00/LogVol00 as available filesystems. If I select /dev/VolGroup00/LogVol00, it mounts fine, and I can access the files ok, so there doesn't appear to be anything wrong with the LVM or Raid.

My guess is that it's something simple like fstab. Help!

---

### Post by psusi on 2011-01-10
What do you mean it scrolls up too fast?  And this is after the grub menu right?  The exact error message is pretty vital.

---

### Post by bigstoo on 2011-01-10
Yep. Grub works fine, it finds the linux kernel and initrd from the /boot partition.
Then the text on the screen starts scrolling like a normal linux boot.
Is there any way to pause it as it's scrolling up?
All I can see is the last so many lines, where it lists a kernel panic, and lots of mount points that it can't find.

Having read elsewhere, I suspect it might be because /dev/md1 isn't being created at boot.

I'll keep digging... I may find myself coming out the other side.

---

### Post by bigstoo on 2011-01-11
In a vain attempt to see what was going on during boot before it panicked, I videoed the startup and then watched it back frame by frame.

It still scrolls past pretty quick, but I can't really see any errors other than the "No Logical Volumes" found. dmraid appears to be working, so I'm guessing the problem is with LVM.

Am I right in thinking I can put "break=premount" as a kernel argument to halt the boot as it gets to mounting the filesystems?

---

### Post by psusi on 2011-01-11
Are you mixing up software raid with fake raid?  dmraid is for fake raid.  You need to use one, or the other, not both.

---

### Post by bigstoo on 2011-01-11
No, I'm definitely using software raid (mdadm).
I just saw the dmraid message during bootup and thought it might be relevant.

I'm in the process now of *vgextend*ing and *pvmove*ing the logical volume back to the original drive.

I suspect the problem has something to do with UUID of volumes.

Last time I did it, I cloned the drive (and presumably kept its UUID) and it worked.
This time I tried moving the VG to a different PV and booting from that. I presume there must be some ID mismatch somewhere (I can only think initrd?).

Fingers crossed, I can get it booting again.

---

### Post by psusi on 2011-01-11
What dmraid message?  What do you get if you run sudo dmraid -n?

---

### Post by bigstoo on 2011-01-12
The message is
```
device-mapper: dm-raid45: initialized v0.2507k
Scanning and configuring dmraid supported devices
Scanning logical volumes
```

I can't run sudo dmraid -n as I don't get to a command prompt. It kernel panics before mounting anything.

Don't worry too much about it. I'm going to reinstall the system.

---

