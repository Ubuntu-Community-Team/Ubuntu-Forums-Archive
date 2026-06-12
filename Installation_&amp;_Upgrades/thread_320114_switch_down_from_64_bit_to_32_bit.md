---
title: "switch down from 64 bit to 32 bit?"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2006-12-16
Is there any painless way of switching from a Kubuntu 64 installation to a 32 bit install of same?
The text installer confuses the hell out of me as regards selecting partitions to (re)use for the installation and I also have no CDs left to burn an ISO onto. I have some blank DVDs, but don't think they'll work for burning a 32-bit CD ISO.
Some kind of apt-get command similar to the one used to upgrade from 6.06 to 6.10 would be very handy, but I guess I'm dreaming :)

---

### Post by meng on 2006-12-16
How have you partitioned this puppy in the first place? If you have a separate /home partition, then just reinstall over the / partition and preserve the /home partition. Yes, that means you will need to understand which partition is doing what, but that's a good thing to know anyway. The most important thing to know when using the text installer is that you choose correctly between "reformat this partition" and "keep existing data". Two very different choices and outcomes!!!! Any other mistakes you make during installation (e.g. incorrect mountpoints) can be reversed.

---

### Post by pickarooney on 2006-12-16
I reckon I got the partitioning right after much sweating and reworking the last time. Fstab is like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=23cd75dd-8522-4cc8-8026-43d34facd54f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=38771644-df5d-4863-95ef-4abcf0a9c696 /boot           ext3    defaults        0       2
# /dev/sda4
UUID=6aca9cac-5354-4183-bf88-68e9e62bed9a /home           ext3    defaults        0       2
# /dev/hdb5
UUID=faf11a4c-4365-4982-98c9-fcf80bc73ca5 /media/backup   ext3    defaults        0       2
# /dev/hda6
UUID=f3466d96-c519-11d7-9a37-a027fa319c88 /media/oldhome  ext3    defaults        0       2
# /dev/hda7
UUID=bb8c5418-a024-4cc0-a287-4b1b083042af /media/oldsystem ext3    defaults        0       2
# /dev/hdb1
UUID=f084d777-e5ba-49df-b71b-729b2c0d2475 /media/supersize ext3    defaults        0       2
# /dev/sda5
UUID=7db0edf9-d00d-4b15-a5c3-c738a9091488 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

So at some stage I should pick "manually install" and "keep existing data"? Sounds straightforward enough. 
Just need to find a CD now.

---

### Post by meng on 2006-12-16
Manually edit partition table, and for each device in the fstab (/dev/sda1, /dev/sda4, etc.) choose the corresponding mountpoint (/boot, /home, etc.), and also choose the "keep existing data".
/dev/sda3 can be reformatted so you replace 64-bit with 32-bit.

---

