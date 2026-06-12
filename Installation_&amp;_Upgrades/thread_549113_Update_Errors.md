---
title: "Update Errors"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by colinpat on 2007-09-12
Hi

Can anyone tell me why I keep getting these same error messages when trying to update, screen shot attached - I hope it worked.

Also when updating get error message saying can't open hlip - HP printer program.

Any help much appreciated

Colin

---

### Post by ilsa on 2007-09-12
I am having the exact same problem as of late last night.  All packages that are listed as "Translation-en_CA" fail to download. 

 It doesn't seem to be a specific server either.  
archive.ubuntu.com
security.ubuntu.com
ca.archive.ubuntu.com
etc.

Even [www.getautomatix.com](www.getautomatix.com).

---

### Post by Ayuthia on 2007-09-12
> **colinpat said:**
> Hi

Can anyone tell me why I keep getting these same error messages when trying to update, screen shot attached - I hope it worked.

Also when updating get error message saying can't open hlip - HP printer program.

Any help much appreciated

Colin
It is saying that the six files were not in the repository.  You might try another mirror.  I looked at the first file that was missing and it looks like it is in the United Kingdom repository under [www.mirrorservice.org](www.mirrorservice.org).

---

### Post by colinpat on 2007-09-13
The update runs automatically.  How do you change the sites it is looking for to download the packages??


Also when auto updates is installing the packages I keep getting the following 

Setting up hplip (1.7.3-0 ubuntu1)
Creating/updating hplip user account
Starting HP Linux Printing & Imaging system
......fail
invoke rc.d:initscript hplip, action "start" failed
dpkg:error processing hplip (--configure):
subprocess post-installation script returned error exit status 1

This happens numerous times as the update process installs the various packages.

hplip is installed and seems to be working fine.

Any ideas most welcome

Thanks

Colin

---

