---
title: "raid10 boot problems"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by sminded on 2008-11-09
Short version:
My RAID10 array is not automatically detected at boot. I'm dropped to Busybox. If I then do mdadm --assemble, followed by CTRL-D, everything works fine, and boots fine. Btw, its not degraded.
Whats the catch, what am I missing?

I could easily modify the kernel startup scripts to do an assemble for me and everything would work just fine. But that should not be necessary.

HELP

---

### Post by Toet on 2008-11-09
Are the partitions of the type linux raid auto detection (fd)?

---

### Post by xvolks on 2009-01-23
Hi,

Maybe mdadm can't find your devices automatically.

When I had this behavior I did the following : 
[LIST]
[*]Boot from a live cd
[*]assemble raid
[*]mount raid partition, say in /mnt
[*]sudo mount -t proc proc /mnt/proc
[*]sudo mount -t sysfs sys /mnt/sys
[*]sudo mount --bind /dev /mnt/dev
[*]sudo chroot /mnt
[*]sudo vi /etc/mdadm/mdadm.conf
[*]add the line (according to your settings see [manpage]("http://man-wiki.net/index.php/5:mdadm.conf")) : *ARRAY /dev/md0 devices=/dev/sda1,/dev/sdb1*
[*]save the file
[*]sudo update-initrd -u
[*]umount all the devices
[*]reboot
[/LIST]

This operation should replace the mdadm options in the initrd so mdadm now knows what device to assemble.

Hopefully this will help someone ;)

--Xvolks

---

