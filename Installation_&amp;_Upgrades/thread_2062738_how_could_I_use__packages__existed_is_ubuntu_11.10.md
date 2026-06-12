---
title: "how could I use  packages  existed is ubuntu 11.10   in 12.04"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by forsubhi on 2012-09-25
W: Failed to fetch [http://ppa.launchpad.net/openbravo-isv/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/openbravo-isv/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/openbravo-isv/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/openbravo-isv/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/openbravo-isv/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/openbravo-isv/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found


I think that this packages is existed in ubuntu 11.10 , how could I use it with 12.04 ?

---

### Post by drmrgd on 2012-09-25
Looks like the author does not have a more current repository than Oneiric, unfortunately.  Without knowing what the package is, does, and requires, it's really hard to say if using the Oneiric repository would work, as the newer Precise libraries might not be compatible and could end up wreaking havoc on you system.  

It does look like the packages were updated within the last month, however.  I would contact the Openbravo ERP team from the link in their Launchpad page to see if there's a way to run it in 12.04.  Here's a link, in case you don't have it:

[https://launchpad.net/~openbravo-isv](https://launchpad.net/~openbravo-isv)

---

