---
title: "Failed to fetch... during 7.04 upgrade"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by russose on 2007-03-31
Hi Guys,

I tried to upgrade to 7.04 using update-manager -d and it goes until the download part withoput problems... it downloaded almost 1GB fine but at the end, it give me the following error:

Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/universe/x/xpdf/xpdf-utils_3.01-9ubuntu3_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/x/xpdf/xpdf-utils_3.01-9ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/universe/x/xpdf/xpdf-common_3.01-9ubuntu3_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/x/xpdf/xpdf-common_3.01-9ubuntu3_all.deb) 404 Not Found

The first time, it gaves me 4 such errors but I uninstalled xpdf and now, there are still these 2 errors and It resume the upgrade. the title of the error windows says in French that the updates packages couldn't be downloaded... it workes fine for all other packages.

Thanks for the help,
Salvatore

---

### Post by zvacet on 2007-03-31
In software repositories,or something like that (I don´t know exact name ,ause i don´t have english version) you will see that you can choose between main and local server.Try with main.

---

### Post by russose on 2007-04-01
Hi,

Thanks for the reply. I made a apt-get check and I changed the sources of my packages and then it worked ;)

Thanks;
Salvatore

---

