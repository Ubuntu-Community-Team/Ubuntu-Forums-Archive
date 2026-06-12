---
title: "Swap space has gone away"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by mikeytag on 2006-06-13
Hi everyone,
For some reason my swap partition will not mount anymore. On boot it fails and when I run this command "sudo mount /dev/sda5" I get the following error

mount: mount point none does not exist

Very weird. Am I supposed to make a file or folder called none somewhere? I am pretty confused here. Here is my /etc/fstab file. I have an external hard drive as well as another SATA drives that houses my Windows installation for VMWare goodness :) However, I don't think those should affect the swap space at all. 


```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Windows Drive
/dev/sdb1       /media/Windows  ntfs    noauto  0       0
#Backup Drives
/dev/sdc1       /media/Linux\040Backup  ext3    defaults        0       0
/dev/sdc2       /media/Windows\040Backup        ntfs    noauto  0       0

```

---

### Post by aysiu on 2006-06-13
That's weird. My swap line looks just like yours: ```
/dev/hda6       none            swap    sw              0       0
``` But I don't get that error about *none* not existing.

---

### Post by mikeytag on 2006-06-13
Hmmmm. I thought my fstab was ok, I find it very odd that Ubuntu is complaining about none not existing.

Here is some more info, I try to run mkswap and swapon as follows and here is my output.

```

michael@michael:/$ mkswap /dev/sda5
Setting up swapspace version 1, size = 3109117 kB
no label, UUID=a964974c-b831-4785-85ef-c38fd7d8a582
michael@michael:/$ swapon
usage: swapon [-hV]
       swapon -a [-e] [-v]
       swapon [-v] [-p priority] special|LABEL=volume_name ...
       swapon [-s]

```

---

### Post by aysiu on 2006-06-13
Maybe [this](http://lists.debian.org/debian-user/2004/06/msg01203.html) might help.

---

### Post by mikeytag on 2006-06-13
No matter what I seem to do. Top is always reporting the following:

```

Mem:   2073988k total,   618084k used,  1455904k free,    11980k buffers
Swap:        0k total,        0k used,        0k free,   251452k cached

```

---

### Post by mikeytag on 2006-06-13
[QUOTE=aysiu]Maybe [this](http://lists.debian.org/debian-user/2004/06/msg01203.html) might help.[/QUOTE]

Thanks aysiu,
I tried that but ended up with this error:

```

michael@michael:/$ mkswap /dev/sda5
Setting up swapspace version 1, size = 3109117 kB
no label, UUID=7977e070-ef3f-4bd9-ab8b-daca42b80f05
michael@michael:/$ swapon -a
swapon: /dev/sda5: Operation not permitted

```

---

### Post by aysiu on 2006-06-13
Maybe you need to do ```
sudo swapon -a
```?

---

### Post by mikeytag on 2006-06-13
[QUOTE=aysiu]Maybe [this](http://lists.debian.org/debian-user/2004/06/msg01203.html) might help.[/QUOTE]
Aysiu,
Forgive my earlier post. Operation not permitted means it needs to be run as root. Running 'sudo swapon -a' did the trick.
Thanks,
Mike

---

### Post by aysiu on 2006-06-13
Awesome. Don't know why the problems cropped up in the first place, but I'm glad it's solved now.

---

