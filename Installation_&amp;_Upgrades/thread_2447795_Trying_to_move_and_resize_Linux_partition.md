---
title: "Trying to move and resize Linux partition"
date: 2020-07-26
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2020-07-26
16.04

Using a live CD I run GParted. I see this

/dev/sda2 312 GiB    unallocated 432.70 GiB    /dev/sda5 178.29 GiB

So as the unallocated space is at the left of the linux partition, I can't use that space to resize sda5.

What can I do?

Thanks

---

### Post by TheFu on 2020-07-26
Please post BOTH the commands and output below, using "code tags" so the columns line up as text.

[LIST]
[*]sudo fdisk -l
[*]df -hT -x squashfs -x tmpfs -x devtmpfs
[*]lsblk -e 7 -o name,size,type,fstype,mountpoint
[/LIST]

Please remove any "loop" devices from the output. Those are useless and just add cruft to the output.

Hopefully, the partition table isn't MSDOS and doesn't use extended and logical partitions. If that is the case, it may be quite a chore to do this task to the point that doing a backup, fresh install and restore of your data, settings, programs would be easier.

---

### Post by rva1945 on 2020-07-26
Thanks but I wish I could understand what you mean by code tags.
And what should I type instead of name,size,type,fstype,mountpoint
? Or are they literals?

---

### Post by deadflowr on 2020-07-26
> **rva1945 said:**
> Thanks but I wish I could understand what you mean by code tags.
And what should I type instead of name,size,type,fstype,mountpoint
? Or are they literals?

Always helpful post about code tags here:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

And just copy the commands posted  in post #2 as is and then copy and paste the output into a post, using the above mentioned code tags.

---

### Post by rva1945 on 2020-07-29
Well I finally fresh-installed 20.04 using all the HD. Thanks.

---

