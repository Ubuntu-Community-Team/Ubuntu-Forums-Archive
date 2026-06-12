---
title: "Update Manager Doesn't update system"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by Sonicrulz12 on 2011-06-23
Hi, I upgraded from 10.10 to 11.04 and when i try to check for updates in the update manager it says:W:Failed to fetch [http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ppa/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ppa/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ppa/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/ppa/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Sonicrulz12 on 2011-06-23
Can anybody help please I always like to be up-to-date

---

### Post by Ezlivin on 2011-06-23
Looks like that directory does not exist anymore if you follow the link from your code in Firefox.

```
http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/
```There are options for lucid/ and maverick/ only. Seems the author has removed the natty/ directory.

---

### Post by avtolle on 2011-06-23
The expired sources need to be removed from your /etc/apt/sources.list file (or, at the very least, commented out). You might look for other ppas with your desired "up to date" apps, and if found, add them. Good luck.

---

