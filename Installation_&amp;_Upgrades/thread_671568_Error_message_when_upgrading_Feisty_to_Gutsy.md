---
title: "Error message when upgrading Feisty to Gutsy"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Shay Andrews on 2008-01-18
I keep getting the following error message, and it tells me to check my network connection (it's fine) and retry:
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 206.112.100.146 80]
Can anyone help?

---

### Post by rsambuca on 2008-01-18
You have to disable that repository in order to upgrade.  You can do this from "System -> Administration -> Software Sources".  You will find that repository listed under Third Party repos.  Just disable it, update your your sources when prompted, and then try upgrading.

---

### Post by Shay Andrews on 2008-01-18
That worked, thanks. :)

---

