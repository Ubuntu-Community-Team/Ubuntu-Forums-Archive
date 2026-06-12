---
title: "Change home mount point after instal"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by gmalac on 2006-10-27
Hello,
I just installed version 6.10 and it looks great on my old Gateway which has 2 disks. 
Anyway I basically clicked OK during the whole installation process (newbee here). Now I realize that there is nothing on the 2d disk. It is formatted ext3 but not used.
I'd like to move the home dir there. What should I do? I heard/read about partition and fstab or the like, but I am quite nervous about it.
Thanks you very much for any help.
Guy

---

### Post by tenn on 2006-10-27
If you post the contents of /etc/fstab some one could tell you how to edit that to make your 2nd disc the home dir.

---

### Post by lime4x4 on 2006-10-27
i'm in the same boat.. here is a copy of my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda1
UUID=83513957-bb6d-4e49-8527-d62026fda417  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=62e4bde0-9e03-4dc0-9790-64a80645f408  none            swap         sw                          0  0  
/dev/hda                                   /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/hdc                                   /media/cdrom1   udf,iso9660  user,noauto                 0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto              0  0  
/dev/sdb1                                  /media/sdb1     ext3         errors=remount-ro           0  0

---

### Post by tenn on 2006-10-27
If sdb1 is the one that you want to make your home dir just change the mount 
point to /home like bellow,

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=83513957-bb6d-4e49-8527-d62026fda417 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=62e4bde0-9e03-4dc0-9790-64a80645f408 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
/dev/sdb1 /home ext3 errors=remount-ro 0 0

This should work. Use **gksudo nautilus** in the terminal or run applications to edit the fstab file, or just do [B]gksudo gedit /etc/fstab
[/B] in the terminal.

---

### Post by gmalac on 2006-10-28
Thanks for your reply,

My fstab does not show the second disk hdb? But I can see it formated ext3 using qtparted!
Here is myfstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bb8baa58-31fe-41e3-9f5c-3c9a63c3220a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1fdf1545-c18c-4404-8e1b-f7321a03cf2e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

According to your exemple, should I add a new line at the end:

/dev/hdb1 /home ext3 errors=remount-ro 0 0

Thanks!

Guy

---

### Post by lime4x4 on 2006-10-28
do i have to copy the exsisting contents of home to the new drive first?

---

### Post by dbott67 on 2006-10-28
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

And another one that takes the tutorial from above and adds some screenshots... by our very own aysiu:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

