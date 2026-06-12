---
title: "Error when upgrading from 6.06 to 6.10"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by HandGrenade on 2006-12-12
Hello. I tried using the **gksu "update-manager -c"** method, and got the following error:

[I]Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found[/I]

The terminal looks like this:

[I]rsverboc@rsverboc-laptop:~$ gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmp9AF40b/edgy.tar.gz'
authenticate '/tmp/tmp9AF40b/edgy.tar.gz' against '/tmp/tmp9AF40b/edgy.tar.gz.gpg'[/I]

Does anyone have any ideas?

---

### Post by Topsiho on 2006-12-12
From my own /etc/apt/sources.list I find

#PLF
#deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

which was added by me once and which is a strange duck in this pond (it originally was not included)

My guess is that you should remove this line first (and maybe add this later when the upgrade is finished).

Good luck,

Topsiho

---

### Post by maxamillion on 2006-12-12
This is a known issue. update-manager has some unresolved issues. Use either apt-get or aptitude for upgrades for the time being. 

More info here [https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/68027](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/68027)

/me

---

