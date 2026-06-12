---
title: "error VFAT folder as file"
date: 2005-02-01
forum: Installation &amp; Upgrades
---

### Post by zeus on 2005-02-01
I just installed Ubuntu replaceing my old FC2. I have this kinda problem, that i haven't been resolved.

I have 3 fat32 win partition on my box. I can access to it but all folders threated as file . 

My fstab 
```

proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hdb2       /mnt/win1       vfat    user,umask=0,auto,exec,rw        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5	/mnt/win2	vfat	user,umask=0,auto,exec,rw	0	0
/dev/hda6	/mnt/win3	vfat	user,umask=0,auto,exec,rw	0

```

any ideas? All my files are stored in the fat partition...

---

### Post by poofyhairguy on 2005-02-01
[QUOTE=zeus]I just installed Ubuntu replaceing my old FC2. I have this kinda problem, that i haven't been resolved.

I have 3 fat32 win partition on my box. I can access to it but all folders threated as file . 

My fstab 
```

proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hdb2       /mnt/win1       vfat    user,umask=0,auto,exec,rw        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5	/mnt/win2	vfat	user,umask=0,auto,exec,rw	0	0
/dev/hda6	/mnt/win3	vfat	user,umask=0,auto,exec,rw	0

```

any ideas? All my files are stored in the fat partition...[/QUOTE]


You have to much crap on this lines;

[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

 /dev/hda1       /media/windows    vfat    umask=000       0       0

---

### Post by Buffalo Soldier on 2005-02-01
try changing to this
```

/dev/hdb2	/media/win1	vfat	umask=000	0	0
/dev/hda5	/media/win2	vfat	umask=000	0	0
/dev/hda6	/media/win3	vfat	umask=000	0	0

```

---

### Post by zeus on 2005-02-01
Yes it works...guys..

I don't know if UBUNTU store mounted files in /media ... thanks..

There are new things in Linux every single day :)

---

