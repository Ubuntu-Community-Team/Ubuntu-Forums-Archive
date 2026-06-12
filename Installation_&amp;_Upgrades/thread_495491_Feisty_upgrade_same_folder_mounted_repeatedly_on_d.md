---
title: "Feisty upgrade same folder mounted repeatedly on desktop"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by shadarack on 2007-07-08
Okay...I'm not sure what went wrong, I upgraded to Feisty from Edgy using the upgrade kernel tool provided. It took a while, but that's okay. What's not okay is for some reason it mounted the same drive repeatedly on my desktop! My desktop is full of mounted disk icons all named 41G volume. There are so many of them, they have pushed my normal desktop icons off the screen!

In case it matters, I am using XCFE for my desktop manager, which I installed after installing regular Ubuntu with the GNOME desktop manager. 

To save time, it's not Fstab. Fstab posted at bottom of this help request.

Please, someone help me get all these extra mount icons off my desktop and keep them from coming back. I can't seem to un-mount them and they're not in fstab. Where did they come from? How do I get rid of them?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=86bd8347-9102-4366-976a-44398e314c85 / ext2 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=7cb2644b-d2bb-42d6-8ecb-1720807ca137 /home ext3 defaults 0 2
# /dev/hdc1 -- converted during upgrade to edgy
UUID=5A441F47441F2573 /media/xp ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdc5 -- converted during upgrade to edgy
UUID=10D8-132E /media/old vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hdc6 -- converted during upgrade to edgy
/dev/hdc6 /media/emule ext3 defaults 0 2
# /dev/hdd5 -- converted during upgrade to edgy
/dev/hdd5 /media/movies vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hdd6 /home/shadarack/Desktop/Torrents ext3 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=e4c301a3-2142-4f4d-9cf7-e0d42f62b233 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by shadarack on 2007-07-12
Well, I think I solved the issue. The problem was that feisty was trying to mount a non-existant partition. Not it's fault, I had the partition listed on Fstab. Not my fault either, the partition was supposed to be there - something had damaged my partition table on hdd so that hdd5 was no longer there.

Fortunately testdisk is the 8th wonder of the world and everything is all good now, all I had to do was correct my partition table so it read like it should and all those cloned mount-points went away.

I think Feisty was trying to automatically mount the missing partition to my media folder, which caused it to show on my desktop. Still not sure why it showed 58 times...

Sooooo, if this happens to you, check your partition manager and make sure every partition that is listed on fstab is actually there, and if it's not, testdisk for teh win.

---

