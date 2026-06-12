---
title: "dual boot grub windows hard drive help"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by epotn on 2008-09-01
i installed ubuntu on my left over drive space and grub automatically detected my windows partition, but it did it twice:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

so when i log into windows my second hard drive is not showing up im pretty sure the problem is right here if anyone could help
thanks
-Epotn

*to specify i have 2 HD's one is for winxp/ubuntu and the other is for music, movies, etc..

---

### Post by caljohnsmith on 2008-09-01
You shouldn't need that second entry in your menu.lst if that HDD is just "movies, music, etc". And also, having that entry in your menu.lst will not affect whether Windows can see that HDD. Does Ubuntu see that HDD? Also, what file system does that HDD use--NTFS, FAT32, ext3, etc?

---

### Post by epotn on 2008-09-01
ubuntu sees it its a ntfs

---

### Post by JC Cheloven on 2008-09-01
The second windows entry seems to be nothing but garbage. Just 'comment' all the lines of that entry and see if your problem is fixed. If it is, you can definitively delete these lines at a later time.

Just in case: to 'comment' these lines, open the file in an editor
```
gksudo gedit /boot/grub/menu.lst
```
and put a # at the beginning of each line. Save, exit and reboot.

---

### Post by manishtech on 2008-09-02
> **epotn said:**
> i installed ubuntu on my left over drive space and grub automatically detected my windows partition, but it did it twice:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

so when i log into windows my second hard drive is not showing up im pretty sure the problem is right here if anyone could help
thanks
-Epotn

*to specify i have 2 HD's one is for winxp/ubuntu and the other is for music, movies, etc..
As you can see that the second entry mentions the root as (hd1,0), then it maps the two  hard disks. I means that they are swapped for this entry. Effectively it becomes (hd0,0). So its just a redundant entry. Remove it as mentioned above/

---

