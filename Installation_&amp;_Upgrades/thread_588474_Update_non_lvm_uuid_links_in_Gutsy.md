---
title: "Update non lvm uuid links in Gutsy"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by PerH on 2007-10-23
I've recently upgraded to Gutsy a now all my non lvm2 partitions refuses to mount.
According to this post [http://ubuntuforums.org/showthread.php?t=583294](http://ubuntuforums.org/showthread.php?t=583294) in Gutsy all partitions should be referenced through /dev/mapper even though they are non lvm related.

/etc/fstab 
```

/dev/mapper/Ubuntu-Root                         /               ext3    defaults,errors=remount-ro 0       1
UUID=e638816e-a561-45f4-a19e-4d87903c43ba       /boot           ext3    defaults 0 2
UUID=88b5bd65-2d23-4f67-828f-541f90c966a9       none            swap    sw      0       0
UUID=4ac56078-25fc-4348-a07d-fa314d6d6ce9       /media/store    ext3            defaults 0 2
UUID=f9fe7d39-01e7-4778-bacd-eadb4f2332fd       /media/media    ext3            defaults 0 2
UUID=01C3EDD909D2C540                           /media/fort     ntfs-3g         defaults,locale=sv_SE.utf8,uid=1000,gid=1001,umask=007 0 2
UUID=6E2257ED549F5089                           /media/base     ntfs-3g         defaults,locale=sv_SE.utf8,uid=1000,gid=1001,umask=007 0 2

```

```

ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-10-23 18:57 01C3EDD909D2C540 -> ../../sdc5
lrwxrwxrwx 1 root root 29 2007-10-23 18:57 1da927e6-1312-4e04-85e6-e42dbe9ae30e -> ../../mapper/lvm2|Ubuntu|Home
lrwxrwxrwx 1 root root 10 2007-10-23 18:57 27A9683A0B946BC2 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-10-23 18:57 3658A36558A3229B -> ../../sdc1
lrwxrwxrwx 1 root root 10 2007-10-23 18:57 488948E14902B44B -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-10-23 18:57 4ac56078-25fc-4348-a07d-fa314d6d6ce9 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2007-10-23 18:57 6E2257ED549F5089 -> ../../sdc7
lrwxrwxrwx 1 root root 24 2007-10-23 18:57 88b5bd65-2d23-4f67-828f-541f90c966a9 -> ../../mapper/Ubuntu-Swap
lrwxrwxrwx 1 root root 24 2007-10-23 18:57 d1cd2492-6b03-4476-96a9-c764c1770eff -> ../../mapper/Ubuntu-Root
lrwxrwxrwx 1 root root 10 2007-10-23 18:57 e638816e-a561-45f4-a19e-4d87903c43ba -> ../../sdc3
lrwxrwxrwx 1 root root 10 2007-10-23 18:57 f9fe7d39-01e7-4778-bacd-eadb4f2332fd -> ../../sda3

```

How do I update my uuid links to use the new path required by lvm?

// Per Hermansson

---

