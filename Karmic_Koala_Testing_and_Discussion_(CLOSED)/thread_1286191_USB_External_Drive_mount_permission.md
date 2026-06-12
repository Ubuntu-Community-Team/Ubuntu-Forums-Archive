---
title: "USB External Drive mount permission"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keptile on 2009-10-08
Hi everyone,

I recently upgraded from jaunty to karmic and everything went smooth. The only problem is that my external drive (NTFS) is no longer automounted at startup. If I mount it from Nautilus, it is mounted without read/write permissions to anyone except the current user. I guess this is due to the transition from HAL to DeviceKit. Anyone has a similar issue?

Thanks.

---

### Post by emarkay on 2009-10-08
I have an Iomega 500Gig USB HDU and it works fine. I have read and write permissions. FWIW, I have the latest updates as of an hour ago.

---

### Post by jet87 on 2009-10-08
keptile,
I have the same issue as you after installing Karmic this past Saturday.  I did a full install and not an upgrade.  I've not looked into to issue too much due to time, but it is an annoyance when Rhythmbox needs to rescan my library because a drive wasn't mounted.

---

### Post by keptile on 2009-10-08
I have the latest updates. Automount seems to work but still USB drives have permissions to the current user only, regardless of the filesystem.

I noticed that only folders have 700 permissions, not the files. When I change the permissions of the mount folder with sudo chmod 777 <mountfolder>, I changes back to 700.

---

### Post by keptile on 2009-10-08
There is a bug filed for this behavior:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/390040/](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/390040/)

So, devkit default is to mount with 0700 and Ubuntu defaulted to mounting external disks with user-only privileges to protect private data.

But there is no functionality to fine-tune it in Gnome.

---

