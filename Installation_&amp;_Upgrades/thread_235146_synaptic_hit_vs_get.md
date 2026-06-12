---
title: "synaptic hit vs get"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by klick on 2006-08-12
Can someone explain to me what this is about.  I dont see it in the man page for apt-get

Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages


I assume GET means it downloaded the file, but no Idea what HIT means, I have noticed that I havent seen a single upgrade available in the past 4 days since i started noticing this, is this even a problem?

Many thanks,

---

### Post by tkiesel on 2006-08-12
I might very well be wrong, but i believe that the hit message tells you that Synaptic looked at that repository, and it hasn't been altered from the most recent list that Synaptic already has. Therefore, no need to get/download it.

You shouldn't be worried.  Updates can sometimes be few and far between on a stable Ubuntu release, but not because there is anythign wrong with the system. There are just times when no new vulnerabilities are found that affect the Ubuntu code for days or weeks at a stretch. When found, the vulnerabilities are often patched quite rapidly.

Take care,
-T

---

