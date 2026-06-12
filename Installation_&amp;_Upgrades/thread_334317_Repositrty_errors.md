---
title: "Repositrty errors"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by oscrmyer on 2007-01-08
I get a 302 error every time I run apt-get update, or run the software update tool. 

but if I do a wget i can download the file. Any idea's? Thanks!

"Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.gz)  302 Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-amd64/Packages.gz)  302 Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.gz)  302 Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-amd64/Packages.gz)  302 Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-amd64/Packages.gz)  302 Found [IP: 195.248.90.35 80]"

---

### Post by teaker1s on 2007-01-08
could it be the sources file not correctly configured, 
302 indicates temp moved file so pointing your sources to another repository may cure it

---

