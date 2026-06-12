---
title: "Get .iso from network PC"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by renevanh on 2005-03-13
I downloaded the Ubuntu .iso, and burned it to a cd.
Something did go wrong, so I searched the internet, and learned how to get the .iso file from a server, using the wget command in the commandline.

I guess this should be possible for a network station, but I can't figure out how.

Can somebody help me?

wget (http://)10.0.0.1/F:\Linux Distro's\warty-release-install-i386.iso won't work...
(Maybe the space in the folder name on F:\?)

The idea is to umount the cdrom, mount the iso as the cdrom, and get the installation going.

I did it before, but I repartitionated the harddisks, so I lost the .iso, and I don't like to wait another hour to download it again...

In advanced thanks,

René

---

### Post by sas on 2005-03-13
afaik that won't work unless 10.0.0.1 is running a web server and the .iso is on the site somewhere. You might want to try reading about [samba](http://www.ubuntuguide.org/#sambaserver) or nfs

---

