---
title: "upgrading from 6.06 to 6.10"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by Hightide on 2007-12-27
HI all
I am upgrading using update manager from 6.06 to 6.10 using the command line

gksu "update-manager -c" 

i get this (dee below) and it stalls. can you help?


Failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg](http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg) Could not resolve ‘wine.lowvoice.nl’
Failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz) Could not resolve ‘wine.lowvoice.nl’

regards

hightide

---

### Post by taurus on 2007-12-27
You need to edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out all the 3rd party repos by placing a # in front of them.

Save it and then try to upgrade your machine now.

---

### Post by Hightide on 2007-12-27
Hi Taurus

brilliant. i owe you a drink.

regards
Hightide

---

