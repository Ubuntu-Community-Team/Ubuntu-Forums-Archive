---
title: "problem upgrading to ubuntu 7.04 from 6.10"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by ajlinzey on 2008-09-21
I'm trying to upgrade from 6.10 to 7.04. 
I'm getting Error during update A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
.
.(many similar entries deleated
.
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz) 404 Not Found

According to [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)
I need to change where apt sources.list points to to [http://old-releases.com](http://old-releases.com). The relavent line in /etc/apt/sources.list  is deb [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) edgy-updates main restricted universe multiverse
I'm not at all sure this is right. 
-Andy

---

### Post by Partyboi2 on 2008-09-22
Try changing it so it looks like this:

```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
```

---

### Post by ajlinzey on 2008-09-22
I tried that and it seemed to download some stuff but the suff it it's not finding is all not on [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/)... the full URL is in the original post
Where would the security stuff for old distributions be? and how do I get the update manager to look there?
-Andy

---

### Post by ajlinzey on 2008-09-23
My bad I had neglected to comment out the previous entry for the security entries.
New I get to a point where it tells me:
[I]While scanning your repository information no mirror entry for the upgrade was found.This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'edgy' to 'feisty' entries.
If you select 'no' the update will cancel. 
I selected yes
Then I get:
After scanning your 'sources.list' no valid entry for 'edgy' was found.

Should default entries for 'feisty' be added? If you select 'No' the update will cancel.

Again I selected yes
and got :
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
with the following problems
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Now It seems that my sources.list has reverted I've tried to attach it.
-Andy

---

### Post by oilchangeguy on 2008-09-23
7.04 is almost a year and a half old. and i don't think it's available for download anymore. if your computer will run 8.04, back up your data, and do a fresh install. because you can't upgrade from 6.10 to 8.04.

---

### Post by Lantesh on 2008-09-24
> **oilchangeguy said:**
> 7.04 is almost a year and a half old. and i don't think it's available for download anymore. if your computer will run 8.04, back up your data, and do a fresh install. because you can't upgrade from 6.10 to 8.04.

I've got to agree with oilchangeguy.  You are really wasting your time trying to upgrade from Edgy to Feisty considering how out of date Feisty is.  Back up your data if you don't already keep it on another partition, and do a clean install of Hardy.

---

