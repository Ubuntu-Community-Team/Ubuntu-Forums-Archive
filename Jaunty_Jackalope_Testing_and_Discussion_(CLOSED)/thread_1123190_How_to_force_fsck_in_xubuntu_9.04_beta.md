---
title: "How to force fsck in xubuntu 9.04 beta?"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by reprobus on 2009-04-11
Sudo touch /forcefsck doesn't seem to work in xubuntu 9.04 beta or either it is doing it so fast that I don't see it doing it. Is it broken or is there a new way to do it now or what?

---

### Post by racmar on 2009-04-12
what does the following show?
```
cat /var/log/fsck/checkfs
```

---

### Post by reprobus on 2009-04-12
dustin@laptop:~$ cat /var/log/fsck/checkfs
Log of fsck -C3 -R -A -a 
Sat Apr 11 23:55:48 2009

fsck 1.41.4 (27-Jan-2009)

Sat Apr 11 23:55:48 2009
----------------
dustin@laptop:~$

Hrmm, I guess it did it. But it never showed me that it was doing it like it does on 8.10. Dunno if thats a bug or if it should be that way??

---

### Post by racmar on 2009-04-12
are you using ext3 or ext4 for your partition you want to fsck?  also, if this is your rootfs, you can do:
```
cat /var/log/fsck/checkroot
```

I just tried forcefsck on my ext3 root partition, and it ran @ startup like it should.

---

### Post by reprobus on 2009-04-12
I use ext3. Heres the output of the command you just gave me.

dustin@laptop:~$ cat /var/log/fsck/checkroot
Log of fsck -C3 -a -t ext3 /dev/sda1 
Fri Apr  3 18:49:32 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda1: clean, 127872/4685824 files, 1035861/18729774 blocks

Fri Apr  3 18:49:33 2009
----------------
dustin@laptop:~$

---

### Post by racmar on 2009-04-12
It looks like your rootfs hasn't been fscked since April 3rd.  what do you have in /etc/fstab?

```
cat /etc/fstab
```

fstab has info on what order and which drives should be auto fscked on startup.

---

### Post by reprobus on 2009-04-12
My fstab is empty.

---

### Post by racmar on 2009-04-12
I didn't know it was possible to have an empty fstab.  Strange.  At this point, I am out of ideas.  Here is what I have...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=157ab916-d67c-4139-93c3-6441340793bf /               ext3    errors=remount-ro 0       1
# /dev/sda5
UUID=4698f74a-702f-4233-ac5f-27b08b8aca0c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

to get the UUIDs, just issue

```
blkid
```

If you want, you might try creating a /etc/fstab file with something similar to the above.

---

