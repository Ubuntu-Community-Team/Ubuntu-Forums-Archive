---
title: "Low space in /boot and upgrade aborting."
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by takeawaydave on 2008-11-02
Trying to upgrade but the following is a problem:

```

The upgrade aborts now. The upgrade needs a total of 88.1M free space on disk '/boot'. 
Please free at least an additional 33.6M of disk space on '/boot'. 
Empty your Deleted Items folder and remove temporary packages of former installations using 'sudo apt-get clean'.
```

The problem is as though:

```
david@siwa:/boot$ df -h .
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              67M   11M   52M  17% /boot

```

Only 67M and I need 88M.

Please advice to what I can so.

Thanks,

David

---

### Post by cariboo on 2008-11-02
You could use gparted to resize your boot partition. You have to do this using the LiveCD as you can't resize a mounted partition.

Once you are running the desktop of the LiveCD go to System-->Administration-->Partition Editor and use the Resize/Move Button to resize your /boot partition.

Jim

---

### Post by takeawaydave on 2008-11-02
Won't there be a problem though since my root partition physically taking up the disk blocks after the boot partition?

---

