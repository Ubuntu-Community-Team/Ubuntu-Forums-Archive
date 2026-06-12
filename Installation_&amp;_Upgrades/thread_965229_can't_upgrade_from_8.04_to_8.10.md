---
title: "can't upgrade from 8.04 to 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by djcrash1981 on 2008-10-31
First of all thanks for taking the time to read my problem.

For what I've read is not a good time to make the upgrade (to buggy) but I gave a try to see with what I'll deal in a future.

I changed my sources so I can download the upgrade, it starts doing all the previous steps before starts download the packages and when it does the space check for /boot it fails telling me that it needs 214 free MB and I need to free still 12Mb.

The first time I've installed my PC was like 2 years ago, since then I've been upgrading it without a trouble, till now. Does anyone knows a workaround to this???? Back in the days when i installed i used the default configuration for an LVM system so it created this disk layout:
S.ficheros	Tamaño	Usado	Disp	Uso%	Montado en
/dev/mapper/Ubuntu-root	36G	34G	2.4G	94%	/
varrun	502M	268K	502M	1%	/var/run
varlock	502M	0	502M	0%	/var/lock
udev	502M	52K	502M	1%	/dev
devshm	502M	164K	502M	1%	/dev/shm
lrm	502M	40M	463M	8%	/lib/modules/2.6.24-21-386/volatile
/dev/sda1	228M	24M	193M	11%	/boot
gvfs-fuse-daemon	36G	34G	2.4G	94%	/home/m827078/.gvfs

I can't reinstall my PC because it's my work pc and i have several production servers sync with my public key.

I hope someone can point me to the right direction.

Thanks a lot, and sorry for my English.



----------------
Listening to: [Aborted - A Murmur In Decrepit Wits](http://www.foxytunes.com/artist/aborted/track/a+murmur+in+decrepit+wits)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by lavinog on 2008-10-31
use synaptic and uninstall some of the older kernels
search for **linux-** look in name instead of description
unininstall all but the latest version. That should free up some space.

If it doesn't, you need to grow the boot partition.
Use the live cd and use gparted to resize your current partions to grow the boot partition to 500M or more

---

