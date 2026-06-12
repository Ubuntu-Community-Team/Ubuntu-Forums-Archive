---
title: "Trying to upgrade to 7.10 from feisty fawn..."
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by v604mustangjoe on 2008-03-21
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edge/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edge/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edge/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edge/main-all/binary-i386/Packages.gz) 404 Not Found


i get this error, how do i fixe it. 

I have feisty fawn and i am attempting to upgrade to 7.10 with the update manager.

---

### Post by Pumalite on 2008-03-21
First remove all third parties from your /etc/apt/sources.list. Then try :
sudo apt-get update
Then try to upgrade again.

---

### Post by v604mustangjoe on 2008-03-21
how do i remove third parties from my sources list?

there is the sources list save file, is that where i get the default list. Also how do i unlock the permissions?

---

