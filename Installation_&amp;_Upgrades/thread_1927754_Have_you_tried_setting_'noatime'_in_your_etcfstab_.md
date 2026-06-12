---
title: "Have you tried setting 'noatime' in your /etc/fstab for your partitions?"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-02-18
Read this on another board and was curious on how to do it and if it will work. 
I really have no idea how to do this. Could someone explain how?

> Have you tried setting 'noatime' in your /etc/fstab for your partitions? It really is a massive (double digit) performance gain. There are only a handful of pieces of software that rely on the atime (none of which you probably run). You could also try relatime which is a less strict atime. On slower disks, like a lot of laptops, you'll be shocked at the performance boost.

He stated:
 noatime explained: [http://openrent.blogspot.com/2006/11/noatime-explained.html](http://openrent.blogspot.com/2006/11/noatime-explained.html)

 This issue is as old as UNIX-- Many consider it a fundamental flaw. setting 'noatime' (or 'relatime') on anything that has a spinning disk gives big gains. The only time it's a bad idea is when writes are very, very, cheap. An example:

 His: /etc/fstab on a 5 year old laptop:

code:
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=945adb51-dc82-40f7-b89c-1f32bef8e563 /               ext4    noatime,user_xattr,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=c2de2eae-fcc2-447c-b542-ee81f833ab29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

It's literally the easiest optimization you'll ever do. Change fstab, then umount / mount or just reboot. It's any option for (pretty much any common) linux native FS, and it gives a big gain.




What are the experts here, thoughts on doing this?

---

### Post by ajgreeny on 2012-02-18
This is probably a waste of time these days as the default *atime* setting for Ubuntu is now *relatime* without it being specified in fstab.  This updates the file info only if changes are made, not every time it is read; noatime means that the file info is never changed, even when the file is changed, which is why it can cause problems in a few cases..

The difference in performance is most unlikely to be noticeable in any way, and certainly not significant, so don't bother.

---

### Post by cybrsaylr on 2012-02-18
ajgreeny,

Thanks for the feedback. A buddy posted that he felt this was a way to boost PC performance and I didn't have a clue so I just threw it out here for discussion.

---

