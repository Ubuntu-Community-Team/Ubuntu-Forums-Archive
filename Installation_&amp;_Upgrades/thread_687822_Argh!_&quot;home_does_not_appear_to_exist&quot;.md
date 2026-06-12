---
title: "Argh! &quot;/home does not appear to exist&quot;"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Siyfion on 2008-02-04
Ok, so basically this is a fresh install of Ubuntu on two RAID 0 array's.

The "Master" disk contains two partitions:
[INDENT]1. "/" mounted ext3 partition
2. A 5GB linux swap partition
[/INDENT]

The "Slave" disk contains just the one partition, a 500GB "/home" mounted ext3 partition.

Now I have got ubuntu installed (finally), and now when it boots up and I try to log in, I get a "Your home directory is listed as '/home' but does not appear to exsist" (Or words to that effect).

This is the contents of my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/ddf1_Master1
UUID=b6964deb-c509-4a40-b172-deb2261aeddc /               ext3    defaults,errors=remount-ro 0       1
# /dev/mapper/ddf1_Slave1
UUID=6ae6278d-887b-47b6-a2b3-1138fa350c0d /home           ext3    defaults        0       2
# /dev/mapper/ddf1_Master2
UUID=8c721aa0-44c5-46cd-ba92-16d634a4b514 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Any help would be most welcome!

---

### Post by Siyfion on 2008-02-04
Ok, to add to my previous info, I just logged into a FAILSAFE term, and did a

```
sudo mount /dev/mapper/ddf1_Slave1 /home
```

And now I can log in correctly and all.. So I guess the problem lies solely on the automatic mounting of this partition...?

Ideas?

---

### Post by Odrodzona-Sarmacja on 2008-02-04
I use on my Xubuntu file browser called Thunar, but in it I can go into

edit->preferences->advanced->configure

and mark something like

[x] mount removabe media when hot-plugged
[x] mount removable media when inserted

Maybe this will help somehow.

---

### Post by Siyfion on 2008-02-05
But it's not removeable media, it's a physical harddrive on the same raid controller card as the root filesystem...!?

---

### Post by Siyfion on 2008-02-05
*bump*

---

### Post by Siyfion on 2008-02-06
*bump*

---

### Post by Siyfion on 2008-02-06
Anyone!? Please! Cuz this is really bugging me on every restart having to log in, mount my home directory, log out, log in.. etc.. :(

---

