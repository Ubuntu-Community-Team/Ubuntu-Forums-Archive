---
title: "error processing package libc-bin / no space left on device"
date: 2017-08-11
forum: Installation &amp; Upgrades
---

### Post by kurt-o-sys on 2017-08-11
I'm trying to upgrade my system, but it complains that there's no space left on the device. This seemingly obvious messages doesn't seem to be very easily solved: there are still quite some space and inodes...
What can be the reason of this error? (Full output, see  [https://paste.ubuntu.com/25293735/](https://paste.ubuntu.com/25293735/))
Thx!

---

### Post by TheFu on 2017-08-12
You are out of inodes on / partition.  Don't know why or how that row is all zeros, but it is.

---

### Post by sccman on 2017-08-12
Maybe you have a un-reasonably large file that Ubuntu created in a bug.

Type in:
```
du -a /var | sort -n -r | head -n 10
```
And show us the output. That will give us the top 10 largest files on your computer.

---

### Post by TheFu on 2017-08-12
> **sccman said:**
> Maybe you have a un-reasonably large file that Ubuntu created in a bug.

Type in:
```
du -a /var | sort -n -r | head -n 10
```
And show us the output. That will give us the top 10 largest files on your computer.

It only searches in /var, not the entire computer.  
I would use **find** with a *-size +1G* option to search for large files on a computer, but there are 100 different ways to accomplish the same task.

But the root cause is still that there are ZERO inodes listed or available on / according to the linked output. THAT is the problem.

---

### Post by kurt-o-sys on 2017-08-12
right... but it shows all zero's, that's weird, right? One would expect that at least there are some Inodes? Well, let me see how to solve that problem. Thx.

---

### Post by kurt-o-sys on 2017-08-12
Well... it seems on btrfs, it's normal it shows 0 on the inodes and it's nothing to worry about: [http://www.nrtm.org/index.php/2012/03/13/the-joys-of-btrfs-and-opensuse-or-no-space-left-on-device/comment-page-1/](http://www.nrtm.org/index.php/2012/03/13/the-joys-of-btrfs-and-opensuse-or-no-space-left-on-device/comment-page-1/)

```
$ btrfs filesystem df /
Data, single: total=24.65GiB, used=14.36GiB
System, single: total=4.00MiB, used=16.00KiB
Metadata, single: total=776.00MiB, used=555.08MiB
GlobalReserve, single: total=192.00MiB, used=10.39MiB
kurt-personal@kurt-yagram / $ btrfs filesystem usage /
WARNING: cannot read detailed chunk info, RAID5/6 numbers will be incorrect, run as root
Overall:
    Device size:          25.41GiB
    Device allocated:          25.41GiB
    Device unallocated:             0.00B
    Device missing:          25.41GiB
    Used:              14.90GiB
    Free (estimated):          10.29GiB    (min: 10.29GiB)
    Data ratio:                  1.00
    Metadata ratio:              1.00
    Global reserve:         192.00MiB    (used: 10.39MiB)
$ 
```

But the device seems to be full somehow... Not sure yet what's going on.

---

### Post by TheFu on 2017-08-12
Whoa.  btrfs - I've never touched that. Don't feel it is safe enough for my data. Maybe in a few more years, though I read that redhat is dropping support earlier this week.  [http://www.linux-magazine.com/Online/News/Red-Hat-to-Drop-Support-for-Btrfs](http://www.linux-magazine.com/Online/News/Red-Hat-to-Drop-Support-for-Btrfs)
> However, despite being under development for more than 10 years, Red Hat discovered through feedback that Btrfs was not considered stable enough by its customers.
Of course, other major vendors are still using and committed to btrfs - SUSE and Facebook are examples in the link.

---

### Post by kurt-o-sys on 2017-08-12
If anyone has the same issues: this may help:
[https://bbs.archlinux.org/viewtopic.php?id=193400](https://bbs.archlinux.org/viewtopic.php?id=193400)
[https://unix.stackexchange.com/questions/174446/btrfs-error-error-during-balancing-no-space-left-on-device](https://unix.stackexchange.com/questions/174446/btrfs-error-error-during-balancing-no-space-left-on-device)
[http://marc.merlins.org/perso/btrfs/post_2014-05-04_Fixing-Btrfs-Filesystem-Full-Problems.html](http://marc.merlins.org/perso/btrfs/post_2014-05-04_Fixing-Btrfs-Filesystem-Full-Problems.html)

---

### Post by TheFu on 2017-08-12
So ... SOLVED?  Please mark the thread "**SOLVED**".

Also, it would be VERY helpful if you could clearly say this is a BTRFS related issue and what you did to solve it to help others in this community.  

This helps  a few ways - people with a similar issue will see it is corrected and people trying to help, won't have to read the entire thread to figure out there's nothing more to be done.  Help us out, please.

---

