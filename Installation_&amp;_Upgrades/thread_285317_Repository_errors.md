---
title: "Repository errors"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by wey97 on 2006-10-26
I've installed Ubuntu 6.06.1 and I have Internet connectivity but I can't get updates through synaptic package manager.

I get the following errors:
```

http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: The HTTP server sent an invalid reply header
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: The HTTP server sent an invalid reply header
http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz: The HTTP server sent an invalid reply header
http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz: The HTTP server sent an invalid reply header
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz: The HTTP server sent an invalid reply header
http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz: The HTTP server sent an invalid reply header
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz: The HTTP server sent an invalid reply header
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.7 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz: The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]

```

I tried editing sources.list with sudo gedit /etc/apt/sources.list
and removed the us. to only read [http://archive.ubuntu.com/](http://archive.ubuntu.com/)... like I read in another post with no luck.

What could cause this error?

---

### Post by wey97 on 2006-10-27
bump

---

### Post by megamania on 2006-10-27
> **wey97 said:**
> bump

ubuntu servers are very busy because the new release (6.10) has just come out and everybody is downloading/upgrading. Try waiting a few days.

---

### Post by wey97 on 2006-10-27
Ok I got the update I was looking for from the ftp archive.
[ftp://ftp.archive.ubuntu.com](ftp://ftp.archive.ubuntu.com)

Thanks

---

