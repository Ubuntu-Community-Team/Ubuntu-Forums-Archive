---
title: "Could not download all repository indexes"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by yanivby on 2011-01-02
Hi,

I'm using Ubuntu 8.10 (unable to upgrade to 10.10 just yet)
About a week or two ago, Update Manager started complaining. 
After choosing "check for updates" I'm getting the following error:

**Could not download all repository indexes**

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://il.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I'm getting similar errors when using apt-get. I tried to use a repository of a different country (fi instead of il), but still got 404 response, so this doesn't seem to be a local server problem.
I would find it odd that 8.10 would be removed from the repositories, but if not - what has happened? I'm not even sure if the problem is on my end or not. I can't find anyone else complaining so (unless I'm missing out) the problem is probably local, but I don't really know where to start looking.

Thanks in advance!

---

### Post by Quackers on 2011-01-02
I'm not 100% sure, but I think support for 8.10 may have ceased in April 2010.

---

### Post by yanivby on 2011-01-04
Thanks Quackers.
Does anybody have an authoritative answer, or can point me out to a link with information about this and what I can do (beside upgrade)?

Thanks!

---

### Post by plucky on 2011-01-04
> **yanivby said:**
> Thanks Quackers.
Does anybody have an authoritative answer, or can point me out to a link with information about this and what I can do (beside upgrade)?

Thanks!

See [Here](https://help.ubuntu.com/community/UpgradeNotes)

Intrepid Ibex (8.10) reached EOL in April 2010.

Good Luck

---

### Post by gmargo on 2011-01-04
8.10 Intrepid has been end-of-lifed, but the files live on in a different location.  You can still install packages, but you won't be getting any new  security updates.

Edit your **/etc/apt/sources.list** file and change all instances of "**[http://il.archive.ubuntu.com/](http://il.archive.ubuntu.com/)**" and "**[http://security.ubuntu.com/](http://security.ubuntu.com/)**" to "**[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)**".  Then update/upgrade as usual.

---

### Post by yanivby on 2011-01-05
@gmargo, @plucky - thank you both!

---

