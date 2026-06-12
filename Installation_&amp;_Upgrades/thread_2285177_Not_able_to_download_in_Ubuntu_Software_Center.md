---
title: "Not able to download in Ubuntu Software Center"
date: 2015-07-03
forum: Installation &amp; Upgrades
---

### Post by drewchollis on 2015-07-03
Hello,
 
          In Ubuntu 12.10 whenever I try to download something in Ubuntu Software Center I get the error "Failed To Download Repository Data, Please Check Your Internet Connection" followed by: 

```
 W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found 
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found 
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found 
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found 
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found 
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by qamelian on 2015-07-03
Ubuntu 12.10 went end of life a while ago. Please refer to the URL below for information on updating/upgrading.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

