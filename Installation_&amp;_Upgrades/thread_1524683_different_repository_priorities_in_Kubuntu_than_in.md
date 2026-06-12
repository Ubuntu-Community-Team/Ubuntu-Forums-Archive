---
title: "different repository priorities in Kubuntu than in Ubuntu?"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by u1106 on 2010-07-05
Why does Kubuntu have different repository priorities than Ubuntu?

In Kubuntu I have toady:

```
$ apt-cache policy linux-generic
linux-generic:
  Installed: 2.6.32.23.24
  Candidate: 2.6.32.23.24
  Version table:
 *** 2.6.32.23.24 0
        500 http://fi.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        100 /var/lib/dpkg/status
     2.6.32.22.23 0
        500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
     2.6.32.21.22 0
        500 http://fi.archive.ubuntu.com/ubuntu/ lucid/main Packages
```

Means security and updates have the same priority (500) the newer version wins.

In Ubuntu security has priority 990 and updates 900. So the older 2.6.32.22.23 from security kernel wins over the the newer kernel 2.6.32.23.24 from updates.

Can anybody explain whether this difference is intended? What would be the motivation?

I shouldn't have any package pins affecting these choices.

---

