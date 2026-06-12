---
title: "/home not taking after move to new partition"
date: 2007-04-21
forum: Kentucky Team - US
---

### Post by JarG0n on 2007-04-21
I followed the Psychocats page on moving my /home folder to a new partition.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Afterwards, my /home partition exists as it should on /dev/sda3, however when I restarted, it seems to have created a new profile for my account.  All my desktop settings are gone; Firefox Bookmarks, etc.  Seems Ubuntu is not finding the settings it should be using from the moved directory.  When I go to my home folder, it has everything in it that I saw before the move.  So, it appears nothing is missing, it's just not being used.  Does anyone know why this would happen?

System Monitor shows /dev/sda1 and /dev/sda3, and their allocated disk space usage, according to the partitions I setup.  

Here's my fstab.  I put in exactly what the guide told me to.  I think the only deviation from the guide, is that I used the bootable gparted Live CD (which is quite nice to have!), not the Ubuntu Installer CD.  Both use gparted, albeit probably different versions perhaps.  I wouldn't think this has anything to do with it, since the partitions are there and ostensibly functioning normally.

Any help would be much appreciated.  I miss my Firefox bookmarks.  

```
 
GNU nano 1.3.12             File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=c599929d-b1e4-4438-8c2a-89bd5686a006 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=5251d8da-9efe-415e-aa4a-a796b01eb68f none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda3       /home           ext3    nodev,nosuid    0       2

```

---

