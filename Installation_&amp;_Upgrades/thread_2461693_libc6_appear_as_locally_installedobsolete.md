---
title: "libc6 appear as locally installed/obsolete"
date: 2021-05-05
forum: Installation &amp; Upgrades
---

### Post by enboig on 2021-05-05
I was checking with synaptic for locally installed packages, and I discovered there libc6 (among other packages which should be from ubuntu repo).
I think this could be from some added and removed PPA, but now I would lile to return most of them to ubuntu repo; how could I do that? I could force one by one package version, but there are quite a lot.

Thanks

---

### Post by Xian on 2021-05-05
Can you first verify the source of this package? 

Issue the command shown below and scroll down to "APT-Sources". 
This will tell your from what repo the package originated.

 It's likely the libc6 package showing as local/obsolete is just a prior version no longer found in ubuntu's repos. 
If this is the case it can be safely removed. 

```
apt show libc6
```
Sample output will show as this:
```
apt show libc6
.
.
.
Original-Vcs-Browser: https://salsa.debian.org/glibc-team/glibc
Original-Vcs-Git: https://salsa.debian.org/glibc-team/glibc.git
Download-Size: 2,690 kB
APT-Manual-Installed: no
APT-Sources: http://us.archive.ubuntu.com/ubuntu hirsute/main amd64 Packages
```

---

