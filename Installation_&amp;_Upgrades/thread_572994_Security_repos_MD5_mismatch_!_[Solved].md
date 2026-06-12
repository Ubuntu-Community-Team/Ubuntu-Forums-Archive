---
title: "Security repos MD5 mismatch ! [Solved]"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by Roque on 2007-10-11
Hi,

Since about a month I am getting this message when I issue
sudo apt-get update

[B]Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  MD5Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2)  MD5Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.bz2)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.bz2)  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/B]

I cannot upgrade under these conditions. How can I fix this?

---

### Post by Sef on 2007-10-11
Applications > Accessories > Terminal

then use this command:

```
 cat /etc/apt/sources.list
```

(that will show you your repositor

---

### Post by Roque on 2007-10-11
It seems your message has been trimmed.
The offending repos in my sources.list are the ones that come with Ubuntu, so the problem should be elsewhere:

```
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
```

---

### Post by zvacet on 2007-10-11
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by Roque on 2007-10-11
Isn't aptitude a frontend of apt? I was told not to mix both.

Anyways, now apt-get/the repos are working fine and I am not getting warnings anymore. Maybe they were fixed in the meantime. 

Thanks for the help

---

### Post by Sef on 2007-10-12
Aptitude is or was an updated apt-get.    The latter has caught up with the the former from what I hear.

---

