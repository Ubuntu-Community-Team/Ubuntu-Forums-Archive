---
title: "Update Failed To Fetch Problems"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by jretzer on 2007-08-22
I'm trying to update to 7.0.4  using the  Update Manager, but get the following error messages. I'm not a Linux ninja and am not sure what to do next ...

Failed to fetch [http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/Release.gpg](http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/Release.gpg) Could not resolve 'ntfs-3g.siteweetsite.info'
Failed to fetch [http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2) Could not resolve 'ntfs-3g.siteweetsite.info'
Failed to fetch [http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/main-all/i18n/Translation-en_US.bz2](http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/main-all/i18n/Translation-en_US.bz2) Could not resolve 'ntfs-3g.siteweetsite.info'
Failed to fetch [http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz) Could not resolve 'ntfs-3g.siteweetsite.info'
Failed to fetch [http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.siteweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) Could not resolve 'ntfs-3g.siteweetsite.info'

Thanks for any help.

---

### Post by ddrichardson on 2007-08-22
The site you are trying to update from is down. At least its not responding to pings.

---

### Post by jretzer on 2007-08-22
How do I get it to download from another site?

---

### Post by ddrichardson on 2007-08-22
What are you trying to get?

---

### Post by jretzer on 2007-08-22
I'm trying to use the update utility to upgrade to Feisty from Edgy

---

### Post by ddrichardson on 2007-08-22
The repo you are having problems with isn't an ubuntu one. You can still update Ubuntu - remove the bad sources from sources.lst

---

### Post by jretzer on 2007-08-22
I assume that I can do that with a text editor ... what do I replace them with ...

---

