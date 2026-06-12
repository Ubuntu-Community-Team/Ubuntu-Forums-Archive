---
title: "Error During Update"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by muka on 2007-05-20
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

Anyone please know how to resolve the above error?
It happens when Upgrade to 7.04 happens.

Btw I live downunder in Australia if it's any help.

Thanks
Muka

---

### Post by taurus on 2007-05-20
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all your repos.  Save the changes and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

