---
title: "Bulk Auto-mounting"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by CTRLurself on 2008-11-27
I'm trying to create a generic auto-booting, persistant, mass-auto-mounting bootable flash drive.

I've been working on this since I first started using Ubuntu back when 7 first came out.

Everything except for the "mass-auto-mounting" has actually been integrated into Ubuntu on it's own, and that has always been the part that eluded me.

My latest attempt is very simple, but it frequently (almost always) causes "error - volume failed to mount" type errors. I simple did *sudo gedit /etc/fstab/* then

> 

/dev/sda1 /mnt/sda1 ntfs users,defaults,umask=000 0 0
/dev/sda2 /mnt/sda2 ntfs users,defaults,umask=000 0 0
/dev/sda3 /mnt/sda3 ntfs users,defaults,umask=000 0 0
/dev/sda4 /mnt/sda4 ntfs users,defaults,umask=000 0 0
/dev/sda5 /mnt/sda5 ntfs users,defaults,umask=000 0 0
/dev/sda6 /mnt/sda6 ntfs users,defaults,umask=000 0 0

/dev/sdb1 /mnt/sdb1 ntfs users,defaults,umask=000 0 0
/dev/sdb2 /mnt/sdb2 ntfs users,defaults,umask=000 0 0
/dev/sdb3 /mnt/sdb3 ntfs users,defaults,umask=000 0 0
/dev/sdb4 /mnt/sdb4 ntfs users,defaults,umask=000 0 0
/dev/sdb5 /mnt/sdb5 ntfs users,defaults,umask=000 0 0
/dev/sdb6 /mnt/sdb6 ntfs users,defaults,umask=000 0 0

/dev/sdc1 /mnt/sdc1 ntfs users,defaults,umask=000 0 0
/dev/sdc2 /mnt/sdc2 ntfs users,defaults,umask=000 0 0
/dev/sdc3 /mnt/sdc3 ntfs users,defaults,umask=000 0 0
/dev/sdc4 /mnt/sdc4 ntfs users,defaults,umask=000 0 0
/dev/sdc5 /mnt/sdc5 ntfs users,defaults,umask=000 0 0
/dev/sdc6 /mnt/sdc6 ntfs users,defaults,umask=000 0 0

/dev/hda1 /mnt/hda1 ntfs users,defaults,umask=000 0 0
/dev/hda2 /mnt/hda2 ntfs users,defaults,umask=000 0 0
/dev/hda3 /mnt/hda3 ntfs users,defaults,umask=000 0 0
/dev/hda4 /mnt/hda4 ntfs users,defaults,umask=000 0 0
/dev/hda5 /mnt/hda5 ntfs users,defaults,umask=000 0 0
/dev/hda6 /mnt/hda6 ntfs users,defaults,umask=000 0 0

/dev/hdb1 /mnt/hdb1 ntfs users,defaults,umask=000 0 0
/dev/hdb2 /mnt/hdb2 ntfs users,defaults,umask=000 0 0
/dev/hdb3 /mnt/hdb3 ntfs users,defaults,umask=000 0 0
/dev/hdb4 /mnt/hdb4 ntfs users,defaults,umask=000 0 0
/dev/hdb5 /mnt/hdb5 ntfs users,defaults,umask=000 0 0
/dev/hdb6 /mnt/hdb6 ntfs users,defaults,umask=000 0 0

/dev/hdc1 /mnt/hdc1 ntfs users,defaults,umask=000 0 0
/dev/hdc2 /mnt/hdc2 ntfs users,defaults,umask=000 0 0
/dev/hdc3 /mnt/hdc3 ntfs users,defaults,umask=000 0 0
/dev/hdc4 /mnt/hdc4 ntfs users,defaults,umask=000 0 0
/dev/hdc5 /mnt/hdc5 ntfs users,defaults,umask=000 0 0
/dev/hdc6 /mnt/hdc6 ntfs users,defaults,umask=000 0 0


this makes the very safe assumption that practically every computer this will be used on will be using an NTFS file structure.

But like I said, this causes a lot of errors, so I'm wondering if there is a more elegant way to do this, or if I can suppress the errors. Either option will suffice, I more-or-less just need to auto-mount every functioning partition on every hard drive in the computer.

Thanks for any help.

---

### Post by taurus on 2008-11-27
One problem I see right away is if you have /dev/sdX5 & /dev/sdX6 (two logical partitions), then one of the primary partitions (/dev/sdX1, /dev/sdX2, /dev/sdX3, & /dev/sdX4) has to be an extended partition.  And since it's an extended partition, you cannot mount that partition.

---

### Post by CTRLurself on 2008-12-02
well, this is going to be a flash-drive boot that I want to be able to hand to somebody and when they boot up off of it, I want them to already have their other partitions waiting for them.

On a few different systems I've tried this on, they mounted properly (one had 2 hard drives with a primary and data partition on each), but it generated almost 30 "volume failed to mount" errors.

So I would assume (I may be wrong) that it doesn't care so much what it's mounting, it appears to care more that there are hard drives that AREN'T there.

What I'm really trying to find out is if there is a way to code the fstab file so that it will mount every hard drive it can find (much like windows or OSX do) without generating all these errors.

[edit] and the logical/primary partition ordering problem is why I have them in numerical order, so that any primary partition will be mounted before it's logical's are (which usually pops up a "Volume already mounted" error, but the partitions do in fact mount properly on the machine's i've tested this on -- however, if this may cause it to fail on other computers, any help to avoid this problem would be greatly appreciated.

---

