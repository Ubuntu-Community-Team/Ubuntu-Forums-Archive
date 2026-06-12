---
title: "Expert's help needed as Edgy uprgrade impossible"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by ant1060 on 2006-11-07
Hi!

Could someone please help :( 

I am trying to upgrade to Edgy from Dapper but I am unable to start the process. Entering gksu "update-manager -c" allows me to click on the button so that the Edgy upgrade can start, but after a very short time it errors out with the following message :

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2) (RESTRICTED)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2) (MULTIVERSE)

This means that I am unable to continue.
Incidentally, I use the 686 system anyway on Asus A6J.  What should I do?

Thanks

---

### Post by kidders on 2006-11-07
Not sure if this will be any use, but when bzip2 returns error code 2, it means the archive is corrupt. (See man bzip2.) Perhaps deleting the affected archives and allowing the updater to re-fetch them might help? You could try switching to a different mirror too, the next time round ... just in case.

---

### Post by ant1060 on 2006-11-08
Thank you:) 
That worked and I have now uprgraded to Edgy with no problems at all (although it took 4 hours!!)
Ant

---

