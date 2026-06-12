---
title: "Install over existing partition?"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by Leivonen on 2005-11-18
Is it possible install Breezy over existing partition? I have stuff in reiserfs partition and I want to install ubuntu at same partition (I cant relocate stuff). 

Partitions: small ext3/boot, lotsaspaceGB/reiserfs and small swap. 

Reiserfs partition have stuff-directory so it doesn't "conflict" with other linux directories. I did already test this by making network install with linux and initrd.gz* files (network install works well) but it stops partition phase because there is not option for letting partition table be and installing over existing (reiserfs) partition.


*[https://wiki.ubuntu.com/Installation/FromWindows?highlight=%28windows%29](https://wiki.ubuntu.com/Installation/FromWindows?highlight=%28windows%29)

---

### Post by Leivonen on 2005-11-18
[QUOTE=Leivonen]Is it possible install Breezy over existing partition? I have stuff in reiserfs partition and I want to install ubuntu at same partition (I cant relocate stuff). 

Partitions: small ext3/boot, lotsaspaceGB/reiserfs and small swap. 

Reiserfs partition have stuff-directory so it doesn't "conflict" with other linux directories. I did already test this by making network install with linux and initrd.gz* files (network install works well) but it stops partition phase because there is no option for letting partition table be and installing over existing (reiserfs) partition.


*[https://wiki.ubuntu.com/Installation/FromWindows?highlight=%28windows%29](https://wiki.ubuntu.com/Installation/FromWindows?highlight=%28windows%29)[/QUOTE]

There is nothing to see. I didn't look partition phase too carefully because there is options for leaving partition intact. Just choose mount points for boot and root and choose not to format those chosen partitions.

---

