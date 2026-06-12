---
title: "fprint updates"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by peterson43 on 2011-08-08
I was getting some error messages recently when trying to run update manager. I finally figured out that some of the errors were caused by having the update manager look for obsolete packages. For instance, I got the error messages

> 
Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  404  Not Found

I fixed this problem by clicking on 'settings' in Update Manager, then clicking on the 'other software' tab and un-checking the appropriate line. (I think this could have also been fixed by manually editing the file in /etc/apt/sources.list)

Anyway, I wanted to know what updates I would no longer be searching for, and a little searching revealed that I had added these sources in order to get the fprint package (for fingerprint readers). I do use my fingerprint reader, so I want to make sure that I keep fprint properly updated. Does anyone know how to make sure that I do keep fprint updated. Do I need to tell Update Manager to look in a new location for the fprint updates?

---

