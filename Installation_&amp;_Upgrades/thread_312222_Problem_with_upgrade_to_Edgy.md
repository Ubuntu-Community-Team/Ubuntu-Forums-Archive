---
title: "Problem with upgrade to Edgy"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by OsakaWilson on 2006-12-04
I'm trying to upgrade from 6.06 to 6.10. I have a 64 bit system. I've been using Ubuntu for only a few months. 

I did a gksu "update-manager -c" and ran into a problem. I got the following message:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://ubuntu.moshen.de/dists/dapper/Release:](http://ubuntu.moshen.de/dists/dapper/Release:) Unable to find expected entry  flash/binary-amd64/Packages in Meta-index file (malformed Release file?)
[http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:) 404 Not Found
[http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:) 404 Not Found

This brought everything to a stop. What do I do? Anyone?

---

### Post by OsakaWilson on 2006-12-04
I just deleted the repositories that didn't seem to work. At least it got the upgrade started.

---

### Post by leona on 2007-08-28
So what do you do if the repo its complaining about ISN'T in your Source list?
I have same problem.
Go to the url and the list is listed perfectly.
its saying this is invalid 
```
http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release
```
This line isn't in my source list at all.
I get
```

Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release Unable to find expected entry  multive/source/Sources in Meta-index file (malformed Release file?)

```
Source list
```

# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://gb.archive.ubuntu.com/ubuntu dapper main restricted
deb http://gb.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://gb.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://gb.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://gb.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper-updates universe multive


```

Arr hang on is it these two causing me the problems
```

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://gb.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper-updates universe multive

```
???
ya it was, commented out, now working fine thanks. :) sorry to bother you guys, it will not let me delete my post. so my aplogies.

---

