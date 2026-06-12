---
title: "Reinstall Ubuntu on Dual boot( Xp)"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by chandru155 on 2010-01-07
I have dual boot of xp and ubuntu 9.10.
For Ubuntu i created 3 partitions, namely, /,swap and for boot
Now i am going to reinstall Ubuntu again. What should i do on Manual partition.
Shall i delete all the three ubuntu partitions and create it again?
Or what should i do to reinstall ubuntu with dual boot?
reply soon.
I am going to format my system withing 10 minutes

---

### Post by audiomick on 2010-01-07
With that setup, if you want a fresh install re-format them all.

Most recommendations I have seen suggest the following:
a partition of around 10 - 15GB for the system mounted at /
a swap partition as big as your RAM, if you want hibernate to work.
If hibernate is not an issue, about 1GB swap

The rest of your space mounted at /home. This allows you to re-mount home at a future re-instal, thereby retaining your data and settings.

There is no need for most people for a separate /boot partition.

---

### Post by chandru155 on 2010-01-07
Ok. sorry thats not boot. that was Home

On Manual partition, should i tick format button for root(/) and home?
I dont want anything.
If i give format for both root and home, will i get dual boot again?

---

### Post by audiomick on 2010-01-07
Ok, you already have a separate /home partition. So, choose the mount point for /home, the same file system that it already had, but not to format it. Then the system will come back with all your data where it was, and the desktop the way you had it, and things like your evolution setup intact.

You need to use the same (identical) user name and password that you had on the old install.

Re-format the / partition.

If your swap is big enough, you just re-mount it as swap.

---

### Post by chandru155 on 2010-01-07
I dont want anything except xp ubuntu dual boot at last..
So shall i give format for home partition also?

I heard that, on last page, name READY TO INSTALL
((which will show like this

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
 partition #9 of SCSI1 (0,0,0) (sda) as ext4
 partition #10 of SCSI1 (0,0,0) (sda) as swap
 partition #11 of SCSI1 (0,0,0) (sda) as ext4
)
Should i uncheck install bootloader? or shall i proceed further without any change in that option?

---

