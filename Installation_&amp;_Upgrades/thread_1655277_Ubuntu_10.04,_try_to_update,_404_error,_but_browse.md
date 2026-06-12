---
title: "Ubuntu 10.04, try to update, 404 error, but browser finds archive fine"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by kyleddm on 2010-12-29
Hi everyone,
 
I am trying to update My ubuntu 10.04 machine. I am trying to get the latest 10.04 updates and then go to 10.10. When I try to update, either by using synaptic, update manager, or terminal (apt-get) I receive a 404 error on some of the repositories. When I go to that same exact link through my browser, it finds the package no problem.
 
Also, when I try to update to 10.10, an error occurrs saying the server is overloaded, but i think this has something to do with the above error.
 
I am connected through a windows XP machine running internet connection sharing. I also have the ip addresses to my DNS servers stored directly on the ubuntu machine, (which is why I can see the internet).
 
Does anyone know why I can see the packages through the browser, but not through any software manager?
 
Thanks

---

### Post by sikander3786 on 2010-12-29
So you are not behind a proxy?

Please post the _complete_ output of this command.

```
sudo apt-get update
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by kyleddm on 2010-12-30
Here is what it said for the 10.04 update:
 
```
 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz 404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

```
 
for update to 10.10:
 
```
 
Could not find release notes
The server may be overloaded. 

```
 
Oh and to answer your question, no I am not behind a proxy, I am simply using a windows computer as a NAT router (via internet connection sharing).  If you can't see an issue, it is entirely possible that internet connection sharing is somehow impeeded on my network, although I do not see how I am able to go to the packages via the same exact link through a browser, but updating will not work, although, I just tried to post to this forum using that computer and it kept telling me that my message was of 0 length, so maybe it is possible that part of my connection is impeeded in the network.

---

