---
title: "RAID Startup Trouble"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by Seaker on 2008-06-20
After doing a clean install of Hardy, I decided to restructure the rest of my drive space to get better use out of it.  I put two fast SCSI drives into a raid0 with mdadm.  The rest of the unused space on three other drives I pooled into one volume with LVM2.  All works fine until I reboot.  On startup I get thrown into a busy box with an fsck error (see below) and my logs rapidly filling with "md: array md0 already has disks!".

```

Log of fsck -C3 -R -A -a 
Fri Jun 20 18:50:41 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Invalid argument while trying to open /dev/md0
/dev/md0: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8
```

If I issue an 'mdadm -S /dev/md0', the following shows up in the log.
```

[  161.022875] md: array md0 already has disks!
[  161.025437] md: md0 stopped.
[  161.025456] md: unbind<sdd1>
[  161.025463] md: export_rdev(sdd1)
[  161.035451] md: bind<sde1>
[  161.035565] md: bind<sdd1>
[  161.102506] md0: setting max_sectors to 128, segment boundary to 32767
[  161.102511] raid0: looking at sdd1
[  161.102514] raid0:   comparing sdd1(143371968) with sdd1(143371968)
[  161.102516] raid0:   END
[  161.102518] raid0:   ==> UNIQUE
[  161.102519] raid0: 1 zones
[  161.102521] raid0: looking at sde1
[  161.102522] raid0:   comparing sde1(143371968) with sdd1(143371968)
[  161.102525] raid0:   EQUAL
[  161.102526] raid0: FINAL 1 zones
[  161.102531] raid0: done.
[  161.102533] raid0 : md_size is 286743936 blocks.
[  161.102534] raid0 : conf->hash_spacing is 286743936 blocks.
[  161.102536] raid0 : nb_zone is 1.
[  161.102537] raid0 : Allocating 8 bytes for hash.
```

I can then 'mount /dev/md0' and I get the following after which I can let the startup continue:
```

[  211.583510] kjournald starting.  Commit interval 5 seconds
[  211.590030] EXT3 FS on md0, internal journal
[  211.590035] EXT3-fs: mounted filesystem with ordered data mode.
```

So, any ideas on what is happening and how I might fix this so that it does a normal boot with out manual intervention?

---

### Post by Seaker on 2008-06-23
Does anyone know where I can find a good discussion of what happens in Ubuntu when you boot your machine?

---

### Post by Seaker on 2008-07-08
Just a quick note to follow up and hopefully save someone some grief.  I've found that there are two issues here.  The fsck problem was solved by recreating the array and recreating the filesystem.

The second and more serious problem is the 'md: array md0 already has disks!'.  This still is happening with every reboot. It turns out that this is logged as a bug: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/188392]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/188392")

From my experience with this bug, it can cause Ubuntu 8.04 to hang (become completely unresponsive), if you let it go long enough (over 10 minutes), presumably due to the logs getting filed with 'md: array md0 already has disks!' many times per second.  Also, this error starts appearing in the kernel log just after the kernel states it has loaded symbols and it starts in mid error.  So, you really don't know what is happening that leads up to this.

I've tried every work around that I can find that has been suggested in the forums, e.g. reinstalling mdadm, rebuilding the array from scratch, etc.  But none have worked.

The only work around is to at the earliest opportunity, either in a busy box, if you are presented with one, or immediately after you log in you do the following:

  1) sudo mdadm -S /dev/md0  ( mdadm -S /dev/md0, if in a busy box)

  2) then check the log with dmesg | tail ( dmesg | /usr/bin/tail, if you are in a busybox) 

  3) if the error 'md: array md0 already has disks!' has not stopped, repeat steps 1 & 2 until it does.
       - I'm finding more and more that it takes repeating the steps 3-4 times before things settle down.

  4) once the error stops, if the array is listed in the /etc/fstab, you can issue a sudo mount /dev/md0 (mount /dev/md0, if in a busy box) and things will then work.

Unfortunately, I have not found a way to script this so that it can be done autmatically.  If you have any suggestions, they would be appreciated!

---

