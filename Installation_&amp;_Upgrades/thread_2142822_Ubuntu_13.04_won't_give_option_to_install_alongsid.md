---
title: "Ubuntu 13.04 won't give option to install alongside windows"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by berner5 on 2013-05-06
When I try to install ubuntu 13.04 off a live usb, I do not see the option to install alongside windows 8.  The version of windows 8 I have is one I upgraded from windows 7, so it uses bios.  I used to be able to install ubuntu 12.04 and 12.10 when I had windows 7 installed.  When I upgraded form windows 7 to 8 I had an install of 12.10.  If I remember correctly I wasn't sure exactly what to do to remove it and now I think there is probably some funky thing with my partitions that the installer doesn't like, any help would be greatly appreciated.  Thanks.

---

### Post by voipster on 2013-05-07
Have you tried installing 12.10 and going through the upgrade to 13.04?

---

### Post by berner5 on 2013-05-07
> **voipster said:**
> Have you tried installing 12.10 and going through the upgrade to 13.04?
I would, but when I've installed 12.10 in the past, I've had to install drive for both my ethernet and wireless card, so I would really like to try a different way.  I think I tried 12.04 or 12.10 too and they didn't show the option to install alongside anyway.

---

### Post by oldfred on 2013-05-07
Have you used all 4 primary partitions? Or did you create more than 4 with Windows and it converted to dynamic partitions?

Post this:
       sudo parted /dev/sda unit s print

---

### Post by berner5 on 2013-05-07
Here is the output 

Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start        End          Size         Type      File system  Flags
 1      2048s        3074047s     3072000s     primary   ntfs         boot, diag
 2      3074048s     1425720554s  1422646507s  primary   ntfs
 4      1425723329s  1437192191s  11468863s    extended               lba
 5      1425723392s  1437192191s  11468800s    logical
 3      1437192192s  1465147391s  27955200s    primary   ntfs         hidden

---

### Post by oldfred on 2013-05-07
You seem to be showing a sda5 but it has no format?

You can either delete it so it is unallocated space & then the auto install should work. Or use Something else and manually create partitions.
Click change and use as ex4, check format, and mount as / (root). You should also have swap and perhaps a /home if you want.

---

### Post by berner5 on 2013-05-07
That was it, thank you.

---

