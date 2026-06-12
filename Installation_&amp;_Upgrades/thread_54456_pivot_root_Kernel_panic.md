---
title: "pivot_root: Kernel panic"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Rapaport on 2005-08-04
When I installed ubuntu: i received the following error after finishing the initial installation and attempting to finish by rebooting and opening ubuntu from GRUB.

```
Pivot_root: no such file or directory 
/sbin/init: 428 : cannot open dev/consoles no such file 
Kernel panic - not syncing: attempted to kill init
```





That's where I'm at. GRUB installed fine and I can still access windows XP from GRUB but no Ubuntu. Just before the error the prompt recognizes USB hard drive compatibility and then i get the above error.

---

### Post by Rapaport on 2005-08-04
UPDATE:

I repeated the installation of Ubuntu and reached the exact same point.
Specific things I did during install:

chose to mount to "/"
default options
partitioned 8.5GB U: drive in windows as FAT32
-during Ubuntu i switched drive to ext3
the first intall completes with a successful GRUB install to mbr.
then, when I reboot, GRUB appears and I choose to install the first listing for ubuntu
it ran a prompt and stopped at the same point...
the post with the three lines of error code followed "starting ubuntu..."

so it went:

```
Starting Ubuntu...
Pivot_root: no such file or directory 
/sbin/init: 428 : cannot open dev/consoles no such file 
Kernel panic - not syncing: attempted to kill init
```

---

### Post by blind0wl on 2005-08-09
It'll be in your grub boot up line....can you post what it shows in the grub listing?  Probably a bad root direction.  And what did the install proggy call your drive and partitions...as in /dev/hda1, /dev/sda etc....

---

