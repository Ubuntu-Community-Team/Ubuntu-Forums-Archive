---
title: "[SOLVED] Access Partition"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by sufyan on 2008-07-28
I intalled vista followed by a fresh install of hardy. The dual boot works, I made three partitions; 1 for vista, 1 for hardy and I kept one for documents and videos so that I can access it from any operating system (NTFS).

I can access it from vista but am having problems with hardy. 

Suggestions please.

---

### Post by Nikitas350 on 2008-07-28
What problems do you have?

---

### Post by sufyan on 2008-07-28
It does not mount.

---

### Post by Nikitas350 on 2008-07-28
Run sudo blkid in terminal and post the output here. Also post the fstab here (/etc/fstab).

---

### Post by cdtech on 2008-07-28
You could add to your /etc/fstab file:

```
sudo gedit /etc/fstab
```

add:

```
UUID=1D8FD5F25AC0301F /media/Vista     ntfs    defaults,umask=007,gid=46 0       0
```

You can find your block id using, simply "blkid"

**P.S.**
Be sure you create the directory under /media to mount the NTFS partition (vista)

---

### Post by sufyan on 2008-07-28
/dev/sda1: UUID="7CFCE2E8FCE29BA0" TYPE="ntfs" 
/dev/sda2: UUID="a674adeb-c452-43a6-a597-380619f244df" TYPE="ext2" 
/dev/sda3: UUID="6AC0EDBFC0ED919D" TYPE="ntfs" 

and /ets/fstab is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a674adeb-c452-43a6-a597-380619f244df /               ext2    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by RuleMaker on 2008-07-28
The thing you should do is:
1) find that neutral partition in blkid and copy it's UUID
2) edit your fstab, add a line like this:
UUID=<UUID that you copied in first step> /media/Neutral ntfs-3g auto,users,uid=1000

(this will automatically mout that drive on system startup)

---

### Post by sufyan on 2008-07-28
It is working now. Thank you:guitar:

---

