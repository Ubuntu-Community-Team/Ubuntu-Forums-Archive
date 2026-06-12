---
title: "mirror raid element won't mount"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by captain_vaginismus on 2007-01-23
before, I had a dapper system with several different arrays split over two 250 gig sata drives, when updating (using a fresh install) I had trouble redoing my arrays, so I partitioned one, and kept the other intact, remembering before that I had no problem mounting one drive of the array.

So I have one mirror of the array still, partion type: Linux raid autodetect
but when I go to mount it I get, 
root@i8u:/home/mastur# mount /dev/sda5 /mnt/****
mount: unknown filesystem type 'linux_raid_member'

does anybody know what this meens? thanks.

---

### Post by moogman on 2007-03-20
Hi there,

I had a problem where I previously had a RAID of two HDDs. I then re-installed Ubuntu, and grub was at the start of one partition. For some strange reason, it wasn't correctly formatted. i.e. mount still thought it was a RAID partition, but it should have been a bootable ext3 partition.

**Warning!** This will nuke your partition if you follow it, it may even nuke your cat ;-)

I think mdadm got in the way in the Ubuntu live CD or something. My solution was:
- I wanted /dev/sda1 back as my /boot/ partition.
- To deactivate the raid, use
```
mdadm --stop /dev/sda1
```

- Format /dev/sda1 with:
```
mke2fs /dev/sda1 -j
```

- Reinstall grub with:
```
grub-install
```

- Re-configure the kernel, to re-generate the initrd and that with:
```
dpkg-reconfigure linux-image-2.6.17.11
```

I would like to point out (if it's not already obvious), that this totally wiped any old reference to RAID. It wasn't clear to me what you want to do so maybe you could explain better for my dumb self ;-)

At the very least, try this command:

```
mdadm --query /dev/sda5
```

It should give you some information.

---

### Post by mbarraus on 2007-09-04
Dear Captain

I received this error message on a mirrored drive on which I have the boot partition.

Linux software raid doesn't support the boot partition being on a mirrored drive because it has a problem with the path to the boot partition. For this reason only one of the mirrored drives will boot. You can however access the data on the mirrored drive which won't boot by removing the raid partition. I have done this using The Expert Partitioner built into SLES10 without it wiping the data on the mirrored drive. I was then able to mount the drive and access the data. I have documented this at [http://www.solvedit.com.au/content/view/81/42/](http://www.solvedit.com.au/content/view/81/42/).

Regards
Michael Barr
[www.solvedit.com.au](www.solvedit.com.au)

---

### Post by iwm on 2008-01-12
Try to give this command:
mount -t ext3 /dev/sda5 /mnt/****

bye 
iWM

---

