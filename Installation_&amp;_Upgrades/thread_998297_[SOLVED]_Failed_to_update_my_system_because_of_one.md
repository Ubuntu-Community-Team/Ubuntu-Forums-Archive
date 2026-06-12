---
title: "[SOLVED] Failed to update my system because of one of the rep. Please help"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by gsmbk on 2008-11-30
Hey guys,

I've been facing this problem for quite some time, and I didn't post it here before trying everything I could !!

I'm using Ubuntu 8.04

When using "Update Manager", after checking all the repositories, it gives this error message...

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.My first guess is, it happened because I changed the "Download Server" from the "Software Sources", and get it back to the main server. 

This is my the content of my sources.list ; without all the hashes lines...

```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy universe

deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-security universe

deb http://archive.ubuntu.com/ubuntu/ hardy-security main

deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
```After having the error message, it tells...
> The package informaion was last updated 68 days agoIt really annoy me not to know how fix it...

Any ideas ? Any suggestion ? :)

TIA.

---

### Post by Pumalite on 2008-11-30
Try:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by gsmbk on 2008-11-30
> **Pumalite said:**
> Try:
sudo apt-get update
sudo apt-get dist-upgrade

When using the first line...
```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
```


using the 2ed line...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Pumalite on 2008-11-30
System>Administration>Software Sources>Download From>Choose 'Best Server'

---

### Post by gsmbk on 2008-11-30
Thanks :)

I solved the problem.

After reading the sources.list file carefully, I noticed that there was a replica in the data.
I tried to re-arrange everything in a neat way...

After modifying the sources.list file as below, the problem is no more :)

```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe

deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse universe

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted multiverse universe

deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted multiverse universe
```Thanks again for your effort :)

---

