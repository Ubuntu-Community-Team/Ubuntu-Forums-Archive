---
title: "auto-mount fixed HD on startup"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by ak-47 on 2008-03-24
Hi,

trying to work something out and I haven't found the answer yet - first time that's happened

I have a HD in my desktop that I'd like to be auto-mounted when the machine starts up.  Currently it's found, but until I login and manually mount it via the "file manager" it's not available.

I tried following a how-to related to ntfs drives where it advised editing the /etc/fstab file but it didn't work.

This HD has be formatted to ext3.

here is my /etc/fstab file, where the last line is what I added....


#######################################
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8ddc29fb-070b-4cb1-9a76-7ce2623f008e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4366c0ca-d3e3-49e6-9043-78d28360a73f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb        /media/biggie   ext3    defaults        0       0
#######################################

thanks for any help

---

### Post by newtonfn on 2008-03-24
I must be wrong, but the line you added is missing the partition number.

Should be something like

```

/dev/sdb1 /media/biggie ext3 defaults 0 0

```

Before rebooting (or mounting the partition) remember to create the biggie directory.

---

### Post by ak-47 on 2008-03-24
newtonfn: right on, that was the exact problem - many thanks

---

