---
title: "cant write to 2nd harddrive, dont have permission?"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by Digitallysick on 2007-03-22
I just installed feisty fawn herd 5, i can mount my 2nd harddrive, and see its contents, but cant write to it

it says it is "a read only disk" 

How do i have it mount at startup with full read/write access??? thanks everyone!

Other basic questions

Im looking for software like nero, where i can drag an avi and convert it to dvd with menus and etc. Also is their an app like daemon tools?

---

### Post by taurus on 2007-03-22
What filesystem is that second harddrive?

If you want to burn an .avi to a DVD, you need to use DeVeDe (or other apps) to convert it to .iso and burn it with k3b or any other burning app in Ubunut.

---

### Post by Digitallysick on 2007-03-22
filesystem i guess its ntfs, but has no os, it was just a spare HD when i was running windows, has no os installed.

---

### Post by Pyro_Killer on 2007-03-22
just write:

sudo chown yourusername /were/it/is

 or

sudo -i
cd 777 /were/it/is

---

### Post by taurus on 2007-03-22
You can't write to ntfs without first installing ntfs-3g driver.  If you only use that spare drive in Ubuntu, why not format it to ext3.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by Digitallysick on 2007-03-22
ok i formatted the 2nd harddrive to ext3, but i cant write to it, it still says owner : root how do i make it where i can read /write ??

---

### Post by taurus on 2007-03-22
Where do you mount it now?  I assume you mount it from /etc/fstab.  What does your /etc/fstab look then?

```
cat /etc/fstab
```

---

### Post by Digitallysick on 2007-03-23
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f3e0ad46-83fd-49df-bee5-9338091aee6a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8aad1a94-725c-48b0-a5ec-2581a4ccf95d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0




to get to my second hd, i think its in /media? but i cant write to it

---

