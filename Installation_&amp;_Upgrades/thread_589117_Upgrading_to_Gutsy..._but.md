---
title: "Upgrading to Gutsy... but"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by ur0b0r0 on 2007-10-23
i was so exited when i saw in the update manager the new distribution, i wanted to upgrade but on the first step it shows me an error of the software sources, so i tried to correct it in the sources.list but it says permission denied, even as root ¬¬. (root:/etc/apt/sources.list )
idk what to do, thats what the upgrade says before continuing:

Failed to fetch [http://javadesktop.org/lg3d/debian/dists/dists/stable/binary-i386/Packages.gz](http://javadesktop.org/lg3d/debian/dists/dists/stable/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://javadesktop.org/lg3d/debian/dists/dists/contrib/binary-i386/Packages.gz](http://javadesktop.org/lg3d/debian/dists/dists/contrib/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

---

### Post by prshah on 2007-10-23
Are you currently running 7.04? You can only upgrade from 7.04. Also the update manager specifically mentions that you have to complete all updates in 7.04 before updating. Did this help?

Cheers,
PRS

---

### Post by rsambuca on 2007-10-23
You need to remove those non-standard repositories from your sources list.  You can do it by entering```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Frak on 2007-10-23
Goto System -> Administration -> Software Sources  and remove all unnoficial repos.

---

