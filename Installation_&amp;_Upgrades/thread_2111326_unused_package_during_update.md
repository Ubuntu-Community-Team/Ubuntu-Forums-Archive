---
title: "unused package during update"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by marchelloUA on 2013-02-01
Hi all, 

I tried to use Deluge torrent client before, but I've removed it later. Now each time I receive error after using update:

user@ubuntu:~$ sudo apt-get update 
[sudo] password for user: 

...

W: couldn't load [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: couldn't load [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: couldn't load [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


How do I remove Deluge related packages from update?

---

### Post by srekcahrai on 2013-02-01
```

sudo software-properties-gtk

```
 And remove those PPAs

---

