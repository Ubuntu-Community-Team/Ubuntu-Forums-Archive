---
title: "problem when upgrading to 6.10"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by cptjaben on 2006-10-26
When I attempt to update from dapper to edgy by typing gksu "update-manager -c" and then click on upgrade distro from the menu I get this message about halfway through:

Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://debian.tagancha.org/debian/dists/dapper/main/binary-i386/Packages.gz](http://debian.tagancha.org/debian/dists/dapper/main/binary-i386/Packages.gz) 400 Bad Request
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/mainci/source/Sources.gz](http://wine.budgetdedicated.com/apt/dists/dapper/mainci/source/Sources.gz) 404 Not Found
Failed to fetch [http://debian.tagancha.org/debian/dists/dapper/restricted/binary-i386/Packages.gz](http://debian.tagancha.org/debian/dists/dapper/restricted/binary-i386/Packages.gz) 400 Bad Request
Failed to fetch [http://debian.tagancha.org/debian/dists/dapper/main/source/Sources.gz](http://debian.tagancha.org/debian/dists/dapper/main/source/Sources.gz) 400 Bad Request
Failed to fetch [http://debian.tagancha.org/debian/dists/dapper/restricted/source/Sources.gz](http://debian.tagancha.org/debian/dists/dapper/restricted/source/Sources.gz) 400 Bad Request

does anyone know how this could be fixed or more importantly how i can successfully update to 6.10?

---

### Post by Fyda on 2006-10-26
That's strange. Third-party (non-official) repositories are supposed to be disabled automatically by update-manager in this scenario (mine did).

What happens if you manually comment them out, do *sudo apt-get update*, and try again?

---

### Post by cptjaben on 2006-10-26
how do I manually comment them out?

---

### Post by Gaute65 on 2006-10-26
With # in front of then

---

### Post by cptjaben on 2006-10-26
Thanks for the help, It looks as though it's working now.

---

