---
title: "Problem with my scsi harddisk"
date: 2004-11-14
forum: Installation &amp; Upgrades
---

### Post by Paco Rodriguez on 2004-11-14
I had problems with my scsi harddisk in the boot process. The kernel recognized the harddisk but not mounted the partition in the harddisk. I had to modify the file '/etc/modules.conf' and add the module kernel 'aic97xxx' (i am not sure if the module name is correct, sorry). The hotplug system load the module but before the boot process try to mount the partition in the scsi harddisk and fail because the module isn't load.

---

