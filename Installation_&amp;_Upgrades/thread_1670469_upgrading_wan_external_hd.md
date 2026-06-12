---
title: "upgrading w/an external hd"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by BCRailrodder on 2011-01-19
Hi,

I currently upgrading from 8.04 to 10.04 & I have a couple of questions?

1)I currently have an external drive that uses NTSF and because I want to use this as a nfs server down the road, I want to change it to ext3.  This is on an OneTouch (Maxtor) and I wonder if this is going to brick the drive?

2)Where would be the best place to mount it - while it should remain plugged into the usb port, there may come a time when it is removed for what ever reason and I don't want it to bork the computer because it isn't there?

Thanks in advance,

Kent

---

### Post by slooksterpsv on 2011-01-19
1) Converting from NTFS to EXT3 will require you to have your data elsewhere before converting as it will require a reformat of the drive.
Ext3 won't be accessible (and may not be possible) without the use of 3rd party tools, namely Ext2/ext3 mounter (which I didn't have luck with mounting ext3 with it).

EDIT: It won't brick the drive, but the "One Touch" functionality that you use in Windows will be gone, cause Windows can't see the drive (if it's ext3) without additional 3rd party software.

2) You will need to unmount the drive from the OS before you can disconnect it. E.g. in Nautilus (file manager) on the left it usually lists the mounted drives, be sure all windows, applications, etc. that are using data from the drive are closed, then click on the eject button. As long as you dismount it, it won't bork the data. Also ext3 is a lot more stable than NTFS in my opinion, so data loss is rare, at least that I've seen.

I hope I didn't miss anything.

---

### Post by BCRailrodder on 2011-01-19
> **slooksterpsv said:**
> 1) Converting from NTFS to EXT3 will require you to have your data elsewhere before converting as it will require a reformat of the drive.

All ready done ..

> Ext3 won't be accessible (and may not be possible) without the use of 3rd party tools, namely Ext2/ext3 mounter (which I didn't have luck with mounting ext3 with it).

Thanks, I'll check into what's available

> EDIT: It won't brick the drive, but the "One Touch" functionality that you use in Windows will be gone, cause Windows can't see the drive (if it's ext3) without additional 3rd party software.

Not a problem - haven't dual booted in ages :)


> 2) You will need to unmount the drive from the OS before you can disconnect it. E.g. in Nautilus (file manager) on the left it usually lists the mounted drives, be sure all windows, applications, etc. that are using data from the drive are closed, then click on the eject button. As long as you dismount it, it won't bork the data. Also ext3 is a lot more stable than NTFS in my opinion, so data loss is rare, at least that I've seen.

Normal SOP then..

> I hope I didn't miss anything.

I take it that it would still mount in /media/ then as always?  Assuming that I don't try to mount it somewhere else in the filesystem permanently of course.

---

### Post by slooksterpsv on 2011-01-19
> **BCRailrodder said:**
> ...

I take it that it would still mount in /media/ then as always?  Assuming that I don't try to mount it somewhere else in the filesystem permanently of course.

Right, you can use pysdm and add it to your fstab, even have it mount to a different location maybe /seconddrive - or what not. Either way still need to unmount before disconnecting.

---

