---
title: "apt-get update  not functioning with ubuntu 10.04 version"
date: 2019-04-05
forum: Installation &amp; Upgrades
---

### Post by husbuntu on 2019-04-05
hi,

I have installed Ubuntu 10.04. i tried reading many post on the forum, but i could not solve this problem. Please let me know the solution for the same

i get following errors after i give this command (sudo apt-get update)

```
dm@dm-desktop:~$ sudo apt-get -y update
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
  404  Not Found [IP: 91.189.88.161 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
  404  Not Found [IP: 91.189.88.161 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources
  404  Not Found [IP: 91.189.88.161 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
  404  Not Found [IP: 91.189.88.161 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
  404  Not Found [IP: 91.189.88.161 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
  404  Not Found [IP: 91.189.88.161 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
  404  Not Found [IP: 91.189.88.161 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
  404  Not Found [IP: 91.189.88.161 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
  404  Not Found [IP: 91.189.88.161 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
  404  Not Found [IP: 91.189.88.161 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
  404  Not Found [IP: 91.189.88.161 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources
  404  Not Found [IP: 91.189.88.161 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
  404  Not Found [IP: 91.189.88.161 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
  404  Not Found [IP: 91.189.88.161 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
  404  Not Found [IP: 91.189.88.161 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
  404  Not Found [IP: 91.189.88.162 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
  404  Not Found [IP: 91.189.88.161 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  404  Not Found [IP: 91.189.88.162 80]
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.162 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Thanx

---

### Post by deadflowr on 2019-04-05
10.04 is no longer supported and the archives have been (re)moved.
Supported releases include 14.04( for a few more weeks) 16.04 18.04 18.10 and soon 19.04.

---

### Post by husbuntu on 2019-04-05
thanx dear

---

