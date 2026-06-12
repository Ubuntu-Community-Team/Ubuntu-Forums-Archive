---
title: "Issue with /home after kernel upgrade"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by MarkNZ on 2007-05-28
Hi There,

I'm running Feisty on a Dell Latitude D505 and everything has been working great until I updated the kernel through update manager this morning.

I've moved /home to it's own partition some time ago using [these instructions]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"), and it's been working fine until the kernel upgrade today. Ubuntu doesn't seem to recognise that /home is mounted to another partition, even though the entry is still in /etc/fstab .

My /etc/fstab is below:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6 /home ext3 nodev,nosuid 0 2
# /dev/hda3
UUID=f74ca020-c668-4657-a71c-860a2b29a5c7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7e54cd1f-0dd3-42ad-88df-34f36859f389 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
```

The new /home partition is definitely /dev/sda6 and the filesystem is also definitely ext3, so that looks fine to me. Any idea where I am going wrong?

Also, I noticed there are a few other files in /etc such as fstab.edgy, fstab~ and a few others which I'm assuming are past versions, is it possible that Ubuntu is reading one of these files?

Thanks in advance.

Mark

---

### Post by NZ-Wanderer on 2007-05-28
Are you by chance using SATA drives at all???

Might pay to check this thread

[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

a lot of people are checking in and reporting problems with the latest kernel which everyone downloaded today.
One of which is regarding drives changing or not being reconigised correctly.

---

### Post by MarkNZ on 2007-05-28
Hi NZ-Wanderer, thanks for your reply.

No, not using SATA, just good old IDE.

Cheers.

---

