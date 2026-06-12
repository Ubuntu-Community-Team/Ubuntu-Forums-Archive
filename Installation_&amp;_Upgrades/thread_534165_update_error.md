---
title: "update error"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by adearaujo on 2007-08-24
```
http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Connection failed [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Connection failed [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: Connection failed [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-amd64/Packages.gz: Connection failed
http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz: Connection failed [IP: 91.189.89.6 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz: Connection failed
http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz: Connection failed [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz: Connection failed [IP: 91.189.88.31 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz: Connection failed [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz: Connection failed [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz: Connection failed [IP: 91.189.88.31 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz: Connection failed [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz: Connection failed [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: Connection failed [IP: 91.189.88.31 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz: Connection failed [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-amd64/Packages.gz: Connection failed [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.gz: Connection failed [IP: 91.189.88.31 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-amd64/Packages.gz: Connection failed [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-amd64/Packages.gz: Connection failed [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz: Connection failed [IP: 91.189.88.31 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz: Connection failed [IP: 91.189.89.6 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz: Connection failed [IP: 91.189.89.8 80]
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz: Connection failed [IP: 91.189.88.31 80]

```


Anybody have any idea why this is happening? I just recently installed dapper 6.06 on laptop acer 4400. During install, I got an error saying it could not update security updates. I have installed ubuntu many times before and never seen that before. I also get same errors when I do a sudo apt-get update or try to install anything through repositories. Any ideas why? I can get online just fine, including I am submitting this post using the computer having this problem.

---

### Post by Pumalite on 2007-08-24
The Repo's might be down. Wait a little bit and try again.

---

### Post by adearaujo on 2007-08-25
Oh I see, That thought did come to my mind. It has been happening for 2 days, I tried yesterday as well and was getting the same thing. Still getting same errors 2 hours later:
```
alexandre@brazuca:~$ sudo apt-get update
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 91.189.89.8 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 91.189.88.31 80]
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/multiverse Sources
Ign http://archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/multiverse Packages
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/multiverse Sources
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Err http://security.ubuntu.com dapper-security/multiverse Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports/main Sources
Ign http://archive.ubuntu.com dapper-backports/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/universe Sources
Ign http://archive.ubuntu.com dapper-backports/multiverse Sources
Err http://archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 91.189.89.8 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  Connection failed [IP: 91.189.89.8 80]
Err http://archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  Connection failed [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 91.189.89.8 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 91.189.89.8 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 91.189.89.8 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper-backports/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com dapper-backports/restricted Sources
  Connection failed [IP: 91.189.89.8 80]
Err http://archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Sources
  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-amd64/Packages.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-amd64/Packages.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz Connection failed [IP: 91.189.89.8 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-amd64/Packages.gz  Connection failed [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz  Connection failed [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-amd64/Packages.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.gz  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-amd64/Packages.gz  Connection failed [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-amd64/Packages.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  Connection failed [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  Connection failed [IP: 91.189.89.6 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

