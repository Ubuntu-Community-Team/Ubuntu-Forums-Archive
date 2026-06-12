---
title: "Ubuntu 11.10 amd64 &amp; Offline repositories problem"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by b.tavakkoli on 2011-10-26
Hi,

I had install ubuntu 11.10 amd64 desktop cd on my PC.
Also i get Full Repositories of ubuntu 11.10 with debmirror.

i edit my /etc/apt/sources.list file and comment all lines and add below line to this file :

```
deb file:///media/hdd5/OneiricRepos/Oneiric64/OneiricRepos64/ oneiric main multiverse universe restricted
```and run "apt-get update" and i get some errors like this :

> W: Failed to fetch file:/media/hdd5/OneiricRepos/Oneiric64/OneiricRepos64/dists/oneiric/main/binary-i386/Packages  File not foundWell, if i put these files (binary-i386/Packages) in my amd64 repositories the "apt-get update" will run whitout any problem, but when i want to install packages like ubuntu-restricted-extras it want to install some i386 packages that there isn't! While same package for amd64 is available on that directory that apt wants to use

I want to use my ubuntu 11.10 amd64 with my offline ubuntu 11.10 amd64 repositories that are more than 40GB and i don't want to get more than 40GB for i386 repositories again!

Please help :)

Update :

my /etc/apt/sources.list content : [http://pastebin.com/V8ZnWQkR](http://pastebin.com/V8ZnWQkR)
my "apt-get update" result : [http://pastebin.com/279DVv2A](http://pastebin.com/279DVv2A)

---

