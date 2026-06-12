---
title: "Update Manager and Repositories"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by matjaz_pirnovar on 2006-06-27
I downloaded a new update after Ubuntu notified me that there is a new update.

After successful download and installation I pressed CHECK in Update Manager and I got a window popping out saying this:

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) Bad header line
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Bad header line [IP: 85.133.25.8 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Bad header line [IP: 85.133.25.8 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Bad header line [IP: 85.133.25.8 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) Bad header line [IP: 85.133.25.8 80]"

After clicking CHECK again everything was okay, my system was OK and up-to-date.

This note happened before too.

Any ideas what that might be? I don't have any connection problems.

Thanks.

Matjaz

---

### Post by slug on 2006-07-24
Whenever I have that problem, I clear all the partial apt directories.

For instance:
If i get this error while updating my package lists *apt-get update*
clear all the files in ```
/var/lib/apt/lists/partial/*
```

If I get this error while trying to install/upgrade packages:
clear all the files in ```
/var/cache/apt/archives/partial/*
```

---

