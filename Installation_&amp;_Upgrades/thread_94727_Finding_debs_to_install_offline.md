---
title: "Finding debs to install offline"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by Mr. Swiveller on 2005-11-24
Hi there!

I am relatively new to Linux, having recently migrated from Win 9X. The version of Ubuntu I am using is Breezy.

I am currently trying to locate the appropriate DEBs for Wine and the Kernel Source (required by OSS install). I can't use apt-get or other automated utilities since my only access to the internet is from Windows boxes. Does anyone know whether there is a site I can go to for downloading the 'official' deb-files made for Breezy installs?

Any help is greatly appreciated.

Cheers,

Swiveller.

---

### Post by StefanoCole on 2005-11-25
Go to [http://www.archive.ubuntu.com]("http://www.archive.ubuntu.com") then go to dists/breezy/universe/binary-i386; download the file Packages.gz.
This file contains a list of all the binary packages available in the universe repository. Unzip it with Winzip and open it (add a .txt extention to the exctracted file). Search the package you need. When you find it there is info about where it is located, go to the specified URL and download it. Note: take into account for possible package dependencies. 
You can do the same for the other repos (main, multiverse, ecc.), always looking in the corresponding Packages.gz file. It is a not smooth process but it works.

Hope this helps, Stefano

---

### Post by Mr. Swiveller on 2005-11-25
Thanks!

Swiveller

---

