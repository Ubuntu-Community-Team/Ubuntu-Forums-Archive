---
title: "Error while installing samba on Ubuntu 14.04.3 LTS"
date: 2015-09-03
forum: Installation &amp; Upgrades
---

### Post by ice-simx on 2015-09-03
System: Ubuntu 14.04.3 LTS

when trying to install samba using synaptic, getting following error

samba:
 Depends: heimdal-hdb-api-8
 Depends: python-dnspython but it is not going to be installed
  Depends: samba-common (=2:4.1.6+dfsg-1ubuntu2.14.04.7) but 2:4.1.6+dfsg-1ubuntu2.14.04.8 is to be installed
  Depends: samba-common-bin (=2:4.1.6+dfsg-1ubuntu2.14.04.7) but 2:4.1.6+dfsg-1ubuntu2.14.04.8 is to be installed
 Depends: samba-dsdb-modules but it is not going to be installed
 Depends: tdb-tools but it is not going to be installed
 Depends: libhdb9-heimdal but it is not going to be installed
 Depends: libkdc2-heimdal but it is not going to be installed
  Depends: samba-libs (=2:4.1.6+dfsg-1ubuntu2.14.04.7) but 2:4.1.6+dfsg-1ubuntu2.14.04.8 is to be installed
 Recommends: attr
 Recommends: samba-vfs-modules but it is not going to be installed

---

### Post by ice-simx on 2015-09-22
comment all the source link in /etc/apt/source.list and add following lines:

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty main restricted

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates universe

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

---

