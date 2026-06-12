---
title: "How to make a DEB from a tar.gz, here code..."
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by frenchn00b on 2010-01-26
apt-get install dh-make build-essential 
#and so on

 
unpack the tar.gz i.e. ${1}

```
make clean ; DEBFULLNAME="myname" ; export DEBFULLNAME ; dh_make -e  myname@gmail.com -f "../${1}"
./configure ; make ; dpkg-buildpackage -rfakeroot


```

is it the right procedure ?

---

