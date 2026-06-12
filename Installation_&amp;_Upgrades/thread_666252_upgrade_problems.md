---
title: "upgrade problems"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by Vitaminc23456 on 2008-01-13
i keep trying to upgrade to 7.10 from 7.04 but i keep getting this message

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-a/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-a/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found

how do i solve this problem and what does it even mean because i have checked the network connection and everything was fine

---

### Post by Crumpets and Jam on 2008-01-13
> **Vitaminc23456 said:**
> i keep trying to upgrade to 7.10 from 7.04 but i keep getting this message

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-a/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-a/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found

how do i solve this problem and what does it even mean because i have checked the network connection and everything was fine

If it is possible, I would recommend download the official .ISO file of Ubuntu 7.10, burning it to a black CD and doing a fresh install. This is how I upgraded.

If this is not possible for you, wait for some one more experienced in Linux to post.

---

### Post by Partyboi2 on 2008-01-13
Go to Software Sources (System>Admin>Software Sources)
and untick all 3rd party repo's and then try again.
If that does not work post
```
 cat /etc/apt/sources.list
```

---

