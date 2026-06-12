---
title: "Update Manager cannot find updates"
date: 2014-12-20
forum: Installation &amp; Upgrades
---

### Post by william.c.garate on 2014-12-20
I'm running Ubuntu 12.10.
I want to use the Update Manager to find and install updates -- namely to 13.04. Following the instructions here: [https://help.ubuntu.com/community/RaringUpgrades#Ubuntu_Desktops_12.10_to_13.04_.28Recommended.29](https://help.ubuntu.com/community/RaringUpgrades#Ubuntu_Desktops_12.10_to_13.04_.28Recommended.29)

But! When I run ```
update-manager -d
``` it fails to download repository information, telling me to "check your internet connection."

[quote]
W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

[quote]

Well, my internet connection works. What gives, man?

---

### Post by TheFu on 2014-12-20
12,10 and 13.04 support ended months ago.
You need to move to 14.04.

Best to know when support ends and move to the supported release of your choice BEFORE that time.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) - It sounds like you need to only run LTS releases, like me.

---

### Post by grahammechanical on 2014-12-20
You are in the land of End of Life upgrades. The repositories of 12.10 and 13.04 are closed as are the repositories of 13.10. A new install of 14.04 would be best but if you want some fun or perhaps frustration then this link will tell you how.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards.

---

### Post by william.c.garate on 2014-12-20
I'm trying to update to 14.04 guys! But it won't let me update incrementally!

---

### Post by sammiev on 2014-12-20
Possible backup all your data and try a fresh install of 14.04

---

