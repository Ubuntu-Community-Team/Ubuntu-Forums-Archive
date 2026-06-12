---
title: "Bad sources.list"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by reinderien on 2012-01-30
I am attempting this sources.list:
```
deb     http://mirror.csclub.uwaterloo.ca/ubuntu oneiric           main restricted universe multiverse
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu oneiric           main restricted universe multiverse
deb     http://mirror.csclub.uwaterloo.ca/ubuntu oneiric-updates   main restricted universe multiverse
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu oneiric-updates   main restricted universe multiverse
deb     http://mirror.csclub.uwaterloo.ca/ubuntu oneiric-backports main restricted universe multiverse
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu oneiric-backports main restricted universe multiverse
deb     http://mirror.csclub.uwaterloo.ca/ubuntu oneiric-security  main restricted universe multiverse
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu oneiric-security  main restricted universe multiverse

deb     http://archive.canonical.com/ubuntu oneiric           partner
deb-src http://archive.canonical.com/ubuntu oneiric           partner
deb     http://archive.canonical.com/ubuntu oneiric-updates   partner
deb-src http://archive.canonical.com/ubuntu oneiric-updates   partner
deb     http://archive.canonical.com/ubuntu oneiric-backports partner
deb-src http://archive.canonical.com/ubuntu oneiric-backports partner
deb     http://archive.canonical.com/ubuntu oneiric-security  partner
deb-src http://archive.canonical.com/ubuntu oneiric-security  partner

deb     http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

deb http://download.virtualbox.org/virtualbox/debian oneiric contrib
```

After trying this suggested method to fix my apt cache:

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

I still get:
```
W: GPG error: http://mirror.csclub.uwaterloo.ca oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Conflicting distribution: http://archive.canonical.com oneiric-updates Release (expected oneiric-updates but got oneiric)
E: GPG error: http://archive.canonical.com oneiric-backports Release: The following signatures were invalid: NODATA 1 NODATA 2

```

So either there's something else wrong with my system, or there are bad entries in that sources.list itself. Any suggestions?

Thanks...

---

### Post by reinderien on 2012-01-31
Okay, this is getting weird. I suspect it might have something to do with my network or my geographical location, because I have two brand-new machines, one xubuntu and the other ubuntu, and they both exhibit the same error messages when using apt (in xubuntu I didn't even touch sources.list).

---

### Post by reinderien on 2012-02-01
Solved. This had nothing to do with sources.list, and seemed to be an artifact of using VirtualBox in NAT mode. Switching to bridged mode made everything work.

---

