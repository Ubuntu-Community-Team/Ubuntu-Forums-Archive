---
title: "jeos and vmware shared folders / vmhgfs"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by pkn on 2007-12-07
I have installed JeOS on VMware Workstation 5.5.5.

Works fine, except the VMware shared folders. I have not installed vmware-tools as the modules vmnet and vmhgfs are already included in jeos.

However I cannot mount the shared folder.  /etc/fstab includes
```
.host:/ /mnt/hgfs vmhgfs defaults,ttl=5 0 0
``` 

andreas@jeos:/etc$ mount /mnt/hgfs/
mount: wrong fs type, bad option, bad superblock on .host:/

Anyone got hgfs running with jeos?

regards,
Andreas

---

