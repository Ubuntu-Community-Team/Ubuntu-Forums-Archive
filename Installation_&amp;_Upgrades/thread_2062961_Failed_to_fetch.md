---
title: "Failed to fetch"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by kf7nnz on 2012-09-26
I'm getting the following message (actually many messages very similar) trying to run the update manager after first being warned only a partial upgrade could be performed.

```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/icedtea-7-jre-jamvm_7u7-2.3.2-1ubuntu0.12.04.1_amd64.deb 404  Not Found [IP: 91.189.92.184 80]
```

I checked a portion of this link, 

[http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/](http://security.ubuntu.com/ubuntu/pool/universe/o/openjdk-7/)

and, sure enough, the package specified does not exist in that folder. I opened a terminal and ran 
```
apt-get check
```
and
```
apt-get upgrade --fix-missing
```
which seemed to succeed but then I still have the same problem. What gives?

---

