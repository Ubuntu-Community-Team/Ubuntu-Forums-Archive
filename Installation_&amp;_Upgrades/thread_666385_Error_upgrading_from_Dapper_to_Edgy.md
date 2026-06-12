---
title: "Error upgrading from Dapper to Edgy"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by butterman on 2008-01-13
I'm trying to upgrade a Dell Latitude notebook D820 running Dapper (from EmperorLinux) to Edgy.  Below are the error messages:

$ gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpmvbWG4/edgy.tar.gz'
authenticate '/tmp/tmpmvbWG4/edgy.tar.gz' against '/tmp/tmpmvbWG4/edgy.tar.gz.gpg'

The Update Manager gives these errors:

Failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg](http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

The Update Manager also says it's usually some sort of network problem.  I ran the update again with a wired connection and got the same errors.

---

### Post by PmDematagoda on 2008-01-13
Open Software Sources in System>Administration>Software Sources, then move to the Third-Party Software tab and uncheck all the repositories. After that is done, close the window and reload the sources list as asked. After that is complete your upgrade should work properly.

---

### Post by butterman on 2008-01-13
Thanks, that worked.  I always said I wouldn't be one of those guys that posts a question that's already been answered, but here it is:

[http://ubuntuforums.org/showthread.php?t=651365](http://ubuntuforums.org/showthread.php?t=651365)

---

