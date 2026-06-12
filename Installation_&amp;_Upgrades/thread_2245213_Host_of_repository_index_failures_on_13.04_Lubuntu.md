---
title: "Host of repository index failures on 13.04 Lubuntu install"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by michael-b-drennan on 2014-09-21
Having lost one of two memory cards on this old Acer 2.93 GHz I figured it was time to install something leaner and newer than the 10.04 that came installed on it.  The Lubuntu install went seamlessly, until I went to upgrade some of the packages.  I had downloaded the mirror last year, but only got around to installing it the other week.  A few repositories however have gone missing - 

```
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources)  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources)  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources)  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.
```

So where would I go besides IP: 91.189.91.14 80 for these updates?  I tried changing from the Main Server to the Server for United States in Software and Upgrades, then thought to change the repository software settings as found on sites regarding 404 errors.  But limited software sources were liisted: Canonical Partners, and Independent, both with source code as well; on and the main restricted sources for ringtail on CD-ROM.  But  I installed off a USB..  What am I missing here, besides a few repositories?

---

### Post by deadflowr on 2014-09-21
13.04 has reached end of life and as such the repos are now gone.
You'll best be served by trying to upgrade to a supported release
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by michael-b-drennan on 2014-09-26
Thanks DeadFlowr!  Pardon the delay of my response.  This page on updates to Saucy indicates all updates should be applied to Raring Ringtail beforehand.  Since I cannot access updates in the first place will it matter, and how?

---

### Post by deadflowr on 2014-09-26
Thinking it through more, I would suggest foregoing a network upgrade, and instead simply download a fresh copy of 14.04.
The next step would be figuring out what you would want to backup.

Backing up is a rather personal endeavor, and sometimes can be a pain, but in the long run it'll be far cleaner than trying to update from a dead release to a dead release to a supported release. IMO.

Keep posting if you need help with backing up, as others will chime in on what they think works best for you.

---

