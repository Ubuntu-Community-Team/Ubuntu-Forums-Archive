---
title: "problem updating Ubuntu packages"
date: 2015-03-30
forum: Installation &amp; Upgrades
---

### Post by -@23%^yu* on 2015-03-30
I'm using ubuntu 12.4 LTS server and when ever I try to update the packages I get this error
```
Err http://security.ubuntu.com trusty-security InRelease  
Err http://ppa.launchpad.net trusty InRelease                             
  
Err http://in.archive.ubuntu.com trusty InRelease                         
  
Err http://in.archive.ubuntu.com trusty-updates InRelease
  
Err http://in.archive.ubuntu.com trusty-backports InRelease
  
Err http://security.ubuntu.com trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://ppa.launchpad.net trusty Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err http://in.archive.ubuntu.com trusty Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com trusty-updates Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com trusty-backports Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Reading package lists... Error!
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  


W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  


W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  


W: Failed to fetch http://ppa.launchpad.net/chris-lea/node.js/ubuntu/dists/trusty/InRelease  


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'


W: Failed to fetch http://ppa.launchpad.net/chris-lea/node.js/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net'


W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'in.archive.ubuntu.com'


W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'in.archive.ubuntu.com'


W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'in.archive.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```
I use apt-get to update and upgrade. Is there any problem with Ubuntu Indian mirrors?

---

### Post by Vladlenin5000 on 2015-03-30
Try changing to another server and run the commands again.
Sometimes there are glitches in some regional mirrors.

---

### Post by grahammechanical on 2015-03-30
> [COLOR=#000000]I'm using ubuntu 12.4 LTS server[/COLOR]

Then why is apt-get trying to connect to 14.04 archives? With 12.04 the archives should be "precise" and with 14.04 they are "trusty." Also you should disable that PPA. That will get rid of a few of those error messages.

---

### Post by -@23%^yu* on 2015-03-31
> **grahammechanical said:**
> Then why is apt-get trying to connect to 14.04 archives? With 12.04 the archives should be "precise" and with 14.04 they are "trusty." Also you should disable that PPA. That will get rid of a few of those error messages.
I'm sorry about that i ment it to be 14.04 LTS. Sorry again.

---

### Post by -@23%^yu* on 2015-03-31
I figured out eh problem. I actually did not enter any dns servers in the network configuration

---

