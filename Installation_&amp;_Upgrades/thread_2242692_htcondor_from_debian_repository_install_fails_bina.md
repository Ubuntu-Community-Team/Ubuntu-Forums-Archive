---
title: "htcondor from debian repository install fails: binary-i386/Packages missing"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by surfer on 2014-09-03
hello

i'm trying to install [htcondor]("http://research.cs.wisc.edu/htcondor/") from their [debian repository]("http://research.cs.wisc.edu/htcondor/debian/").

( yes, i know that they offer a .deb version for ubuntu for download, but as i need to create a mirror of htcondor, i prefer to be able to install and mirror directly from a complete repository. )

the problem is that the repository with the [FONT=Courier New]sources.list[/FONT] line
```
deb http://research.cs.wisc.edu/htcondor/debian/stable/ wheezy contrib
```
does not provide any packages for the i386 architecture; only amd64 is supported. while the condor package installs prefectly.
```
$ apt-get update
```
complains
```
W: Failed to fetch http://research.cs.wisc.edu/htcondor/debian/stable/dists/wheezy/contrib/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
and therefore the grapical updater warns me about outdated packages after a few days  (at least on precise).

is there a way to tell apt to only get amd64 packages for this url? or is there another way to fix this?

---

### Post by surfer on 2014-09-03
ok, i have found a (the?) solution:
```
deb http://research.cs.wisc.edu/htcondor/debian/stable/ dists/wheezy/contrib/binary-amd64/
```
as [FONT=Courier New]sources.list[/FONT] entry does the trick.

---

