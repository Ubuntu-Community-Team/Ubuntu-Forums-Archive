---
title: "Software RAID1 upgrade 10.10 to 11.04"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2011-05-05
I purchase a new computer and had 10.10 installed with a Raid1 - 2x1T hds. I did the upgrade to 11.04 (wee hours of the am) without thinking about the disk mirroring.  The upgrade worked to a point.  When I started working on the bells & whistles from "Things to add after upgrade", I didn't get past the upgrade command.It would appear that another process had locked
/var/cache/debconf/config.dat when you tried to upgrade your system.
However fuser did not indicate anything.   These were the errors.

E: man-db: subprocess installed post-installation script returned error exit status 1
E: libapache2-mod-php5: subprocess installed post-installation script returned error exit status 1
E: mdadm: subprocess installed post-installation script returned error exit status 1
E: php5-cli: subprocess installed post-installation script returned error exit status 1
E: php5-pgsql: dependency problems - leaving unconfigured
E: php5-sqlite: dependency problems - leaving unconfigured
E: samba-common: subprocess installed post-installation script returned error exit status 1
E: samba-common-bin: dependency problems - leaving unconfigured
E: smbclient: dependency problems - leaving unconfigured


Question:  Is this the result of RAID1, i.e. should I have disconnected one hd, updated the other, then mirrored the first?

See Bug 777541

---

