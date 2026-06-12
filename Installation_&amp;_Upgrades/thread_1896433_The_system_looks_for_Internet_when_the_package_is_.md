---
title: "The system looks for Internet when the package is in the archive"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by r_anjit on 2011-12-16
I don't have an internet connection available at home but I do have it at workplace. When I copy all the packages necessary for installing a particular software in to the archive folder and run apt , It still looks to connect to the internet for downloading the packages and neglects those in the archives .

Is there any way to make it look into the archives before looking for those packages by connecting to the net. 

Thank you !

---

### Post by mikewhatever on 2011-12-16
It should look in the archives as well, that is, /var/cache/apt/archives.

---

