---
title: "Automount :: external USB"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by anywebloco on 2008-10-10
Hello - 

For some reason I'm unable to automount an external USB at boot time.

The device is /dev/sdb1 and I've formatted it as ext3. The devicenotifier plasmoid picks it up and you can mount it within the GUI (it mounts at /media/disk).

The (relevant) output of ls /dev/disk/by-uuid -alh is:
> lrwxrwxrwx 1 root root  10 2008-10-10 12:23 30910c65-e857-453e-9050-83680a7767e6 -> ../../sdb1


The (relevant) line in /etc/fstab is:
> # /dev/sdb1
UUID=30910c65-e857-453e-9050-83680a7767e6 /media/backup ext3    rw,auto,user,sync       0       0

Can anyone see what I'm missing here? Any reason why this drive shouldn't mount at boot time?

It booted fine in Hardy, the permissions for /media/backup are username:username, and I've tried variations like replacing UUID with /dev/sdb1

really - this is doing my head in so I'd really appreciate it if anyone's got this sorted in Intrepid!

Thanks,

awl

---

### Post by anywebloco on 2008-10-14
anyone?

---

