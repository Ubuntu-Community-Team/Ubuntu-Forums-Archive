---
title: "Update problem for a beginner with 8.10"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by dmfagan9 on 2011-08-30
Hi All-

So I have an old Ubuntu (8.10 but i am not sure if its 32 or 64- if someone could let me know how I can figure this out it would be great!)

I routinely get update messages that do not go through. it says 'could not apply changes! fix brokn packages first!'

It also says upgrade to 9.04 is avaliable! (Of course there are higher ones as well- but this is what comes up)

When I go to update packages I receive this

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://id.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

any help would be much much appreciated!

Dylan

---

### Post by mörgæs on 2011-08-30
It is a waste of time to struggle with an outdated version of Ubuntu. Go for a fresh install of one of the supported releases.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by dmfagan9 on 2011-08-30
Thanks OK- what about backing up all of my files? I do not have an external HD currently. I have heard about problems with big system transfers?

---

### Post by dmfagan9 on 2011-08-30
Sorry- also do you recommend the 10.04 LTS? It looks like it has the longest 'life'? Thanks

---

### Post by dino99 on 2011-08-30
here is how to install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Lucid is a good choice, Maverick, Natty too ;)

---

### Post by mörgæs on 2011-08-30
It is hard to give a recommendation that fits everyone. Try a few in a live boot and pick the one you like best. If you don't want to bother with frequent reinstalls, 10.04 is a good choice.

Personally I am more fond of Xubuntu than Ubuntu, also on fast computers, but this is mostly a matter of taste.


A few USB sticks are good to have around, both for backup and installation.

---

### Post by coffeecat on 2011-08-30
> **dmfagan9 said:**
> Thanks OK- what about backing up all of my files? I do not have an external HD currently. I have heard about problems with big system transfers?

How did you intend to backup your files without an external drive? Do not think of backing up your data to another partition on the drive you are going to re-install to - something may go wrong. You really need to get an external hard drive - or three! Your personal data is worth more than the cost of the physical media on which it is stored.

---

