---
title: "upgrade failed while installing"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by harys on 2006-06-05
hi i had this error message while proceeding with the upgrade from breezy to dapper drake. i ran the command gksudo update-manager -d from the terminal. the error occured after running the process for at least five minutes

"a problem occured durin the update. this is usually some sort of network problem, please check your network connection ans retry.
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found"

i checked my network connection and all is ok.

thanks for your help. harys

---

### Post by llamakc on 2006-06-05
Comment out those lines in /etc/apt/sources.list and try again. They are not the official repositories for Dapper.

---

### Post by harys on 2006-06-06
thanks, it worked as you said!!!
harys

---

