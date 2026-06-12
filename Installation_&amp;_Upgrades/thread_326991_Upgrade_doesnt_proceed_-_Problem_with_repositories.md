---
title: "Upgrade doesnt proceed - Problem with repositories?"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by hextor on 2006-12-28
Hi,

I put the "official" upgrade command and got the 6.10 is now available message. however the upgrade manager throws an error message saying it could not contact the following repositories and aborts further installation. 


 
[http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:) 404 Not Found
[http://kubuntu.org/packages/amarok-latest/dists/dapper/main/binary-i386/Packages.gz:](http://kubuntu.org/packages/amarok-latest/dists/dapper/main/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:) 404 Not Found

any tips on how to proceeed? Thanks!d

---

### Post by ajgreeny on 2006-12-28
Those repos that gave you the errors are all dapper (6.06) repos so will not be right for an upgrade to edgy (6.10). I suspect you may need to edit them out of your sources.list file, but wait for others to say so before you jump.

I've never done an upgrade to an existing install so may not be the best person to comment, but it does seem strange to use dapper repos for an edgy  upgrade.

---

