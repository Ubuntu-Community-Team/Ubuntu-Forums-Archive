---
title: "Ubuntu doesnt load graphically"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rosenth on 2009-10-03
i dont see ubuntu splash screen while loading "karmic koala",
here are some lines whene ubuntu loads:
```

skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.5
Starting up...

```
then:
```

skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.5
 * stopping NTP server ntpd
 * starting NTP server ntpd
fsck from util-linux-ng 2.16
fsck from util-linux-ng 2.16
fsck from util-linux-ng 2.16
fsck.ext3: Bad magic number in super-block while trying to  ...
.
.
mountall: fsck /mnt/disk [906] terminated with status 8
mountall: General fsck error
...
CONTROL-D will terminate this shell and re-try.
...
* stopping NTP server ntpd
...

```

i had installed "Hardy" after "koala". i noticed i should update partitions UUID, and i did update.
both ubuntus use same "/home" partition

---

### Post by rosenth on 2009-10-03
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e77d19ad-62be-47b4-a453-f3ce7c46a1eb /               ext3    relatime,errors=remount-ro  0       1
# /dev/sda10
UUID=55277259-2d3c-4dca-a30b-2dcff5afb57e /home           ext3    relatime        0       2
# /dev/sda4
UUID=c77d9f3c-4f29-4d93-b7ce-f3c5891155b2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5	/mnt/disk	ext3	default 0 2

```

---

### Post by FrancoNero on 2009-10-03
yes! another topic with the exact same problems. I cant believe this is taking so long for a bugfix to come out. seems to me there are hundres of people out there (including me) who've never seen the new, supposedly nice-looking, boot process because all we get is these text notifications....

---

### Post by Skadge on 2009-10-08
Here the corresponding bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/444928](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/444928)

Don't hesistate to subscribe.

---

### Post by ljrmorgan on 2009-10-08
> **Skadge said:**
> Here the corresponding bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/444928](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/444928)

Don't hesistate to subscribe.

From post #6: "We have addressed these console printing issues and will be checking in the changes soon."

Hopefully that'll fix it then :-)

---

