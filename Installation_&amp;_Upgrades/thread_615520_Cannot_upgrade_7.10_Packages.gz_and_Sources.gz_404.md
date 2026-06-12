---
title: "Cannot upgrade 7.10: Packages.gz and Sources.gz 404 Not Found"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by walkiria_nixe on 2007-11-17
Hi,

I am trying to upgrade to Ubuntu 7.10 but I get the following error while upgrading:

"A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found"

Upgrade aborts at this point. Any ideas on how I can proceed?

Thanks.

---

### Post by por100pre1 on 2007-11-18
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

```
gksudo gedit /etc/apt/sources.list
```

Be sure to replace **medibuntu.sos-sts.com** with **medibuntu.org**

---

### Post by zvacet on 2007-11-18
You can take** por100pre1** advice and get what you want,but recommended procedure is to do upgrade only with official Ubuntu repos.So,it will be better to delete lines in your post and save and close.

```
sudo aptitude update
```

and after that you can do the upgrade,When you are finish just add to your source list like this

[http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories")

---

### Post by por100pre1 on 2007-11-19
> **zvacet said:**
> You can take** por100pre1** advice and get what you want,but recommended procedure is to do upgrade only with official Ubuntu repos.So,it will be better to delete lines in your post and save and close.

```
sudo aptitude update
```

and after that you can do the upgrade,When you are finish just add to your source list like this

[http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories")

Actually, yes, the best way is to remove that repository when upgrading. In any case, the Medibuntu repository is no longer in [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) , so updating the line will be necessary.

---

