---
title: "Ubuntu Dapper Backport fails"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by nits_555 on 2006-09-13
Hi All,

I tried "sudo apt-get update" on my ubuntu dapper this morning and it threw the following errors:

[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2:) MD5Sum mismatch
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:) MD5Sum mismatch

The corresponding entries in the /etc/apt/sources.list are:

 # Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

Can anyone confirm if they are facing the same problem and if any workarounds?

Thanks,
Nitin.

---

### Post by msx2 on 2006-09-13
i have same problem this morning?

any suggestion to fix issue?

---

### Post by tychocity on 2006-09-13
igual para mi

---

### Post by dcollamore on 2006-09-13
I've noticed this error on a clean install of Dapper server today as well...having trouble installing packages as well.  

apt-get install -f does not list any problems, however apache2 claims to be an ~81k install and the service for it will not start.  Several other packages will not install properly (gnump3d gives a dpkg error).  I won't go into specifics on the error messages, just looking to find out if there is anything going on with the repository, and if so if there is a timeframe for a fix.  It's either that or I've gone insane.

---

### Post by msx2 on 2006-09-13
now works fine... :rolleyes:

---

