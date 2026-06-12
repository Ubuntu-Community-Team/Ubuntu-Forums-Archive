---
title: "Server 10.04 software RAID1 issue."
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by Linux_noob616 on 2010-10-20
I'm building a Linux server for a client of mine with RAID1 and i can't seem to install ubuntu 10.04 server

All goes perfect without a hitch, and everything installs great.

When it first boots i don't get a grub grub screen (to my knowledge) and a bunch of errors "could not load /dev/disk/random string of numbers"

I'm about to try and install 10.10 when it finishes it's download and will report back.

Please post if you have any idea whats wrong. I would rather use 10.04 for it's long support.

EDIT: the errors are as followed..
```
 mount: mounting /dev/disk/by-uuid/(long string of numbers) on /root
failed: invalid arguement
mount: mounting dev on /root/dev failed: no such file of directory
mount: mounting sys on /root/sys failed: no such file of directory
mount: mounting proc on /root/proc failed: no such file of directory
Target filesyetem doesn't have /sbin/init.
no init found. try passing init= bootarg.


Busybox v1.13.3 (ubuntu 1:1.1.13.3-1ubuntu11) built-in shell (asj)
enter 'help' for a list of built-in commands.

(initamfs)
```

---

### Post by Linux_noob616 on 2010-10-20
edit..

Anyone...? I know none of you are my personal tech support.. But i am running out of time..

EDIT: 10.10 refuses to let me set a partition to bootable.. so thats out.

---

### Post by Linux_noob616 on 2010-10-20
okay fixed it! well for 10.10

How i did it was i booted into a live CD with Ubuntu 9.04 and deleted the partitions. then i rebooted into a 10.10 live CD and installed the Disk Utility program, and created partitions and set the ones i was going to use as ext4 as bootable.

Then i set them all for RAID auto config. rebooted into the 10.10 server CD and all installed without failure

---

