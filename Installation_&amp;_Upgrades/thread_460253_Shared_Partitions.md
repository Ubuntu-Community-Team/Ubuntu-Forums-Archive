---
title: "Shared Partitions"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by Greasyfingers on 2007-05-31
I've recently installed Ubuntu, dual booting with That Other OS. I have created a shared partition so that I can access my Windows data from Ubuntu, mounting it in a directory called /shared, with the following line in /etc/fstab:
```
/dev/hda6		/shared		vfat		auto,umask=0		0 0
```

1) All the permissions in that folder can only be changed by 'root'; how can I easily set that to 'user'?

2) Can I mount the /home directory on the same partition, so that I can see its contents from Winders, or will I need to create another one?

---

### Post by kidders on 2007-06-01
Hi there,

> **Greasyfingers said:**
> 1) All the permissions in that folder can only be changed by 'root'; how can I easily set that to 'user'?FAT filesystems can't handle ownership & access control, so there really aren't any permissions to change.

> **Greasyfingers said:**
> 2) Can I mount the /home directory on the same partition, so that I can see its contents from Winders, or will I need to create another one?Mounting a FAT filesystem at /home (I *think* that's what you're asking) would be an extremely bad idea imo. Aside from the fact that it's a particularly poorly-designed filesystem, Linux would have no way of protecting any of your personal data.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by merlinus on 2007-06-01
My advice is to format the partition as ext3, and install ntfs-config (available in Applications/Add Remove) to read and write from it.

You can also install ext2ifs so you can do the same from your windows side:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

ext3 is much more secure, and will not get fragmented anyways near as much, nor waste space, as anything that is fat.

-merlin

---

