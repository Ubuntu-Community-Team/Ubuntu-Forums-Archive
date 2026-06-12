---
title: "Apt problems amd64"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by jvictor on 2005-10-15
I have to manually do an nslookup each time to get an apt-get XXXXXX if i just try to run apt-get it stops at Connecting to in.archive.ubuntu.com ...

sudo apt-get update
Password:
57% [Connecting to in.archive.ubuntu.com (1.0.0.0)]
juby@powercube:~$ nslookup in.archive.ubuntu.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   in.archive.ubuntu.com
Address: 82.211.81.193
Name:   in.archive.ubuntu.com
Address: 82.211.81.151
Name:   in.archive.ubuntu.com
Address: 82.211.81.167
Name:   in.archive.ubuntu.com
Address: 82.211.81.182

juby@powercube:~$ sudo apt-get update
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy Release [30.9kB]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates Release [19.6kB]
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main Packages [582kB]
16% [5 Packages 56616/582kB 9%]

---

