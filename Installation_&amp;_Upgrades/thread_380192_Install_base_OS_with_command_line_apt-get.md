---
title: "Install base OS with command line apt-get?"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by csf111 on 2007-03-09
Hello,
I would like to install Dapper via a command line

Something analogous to the Fedora:
yum -c my.conf --installroot=/mnt/newstuff -y groupinstall Base

Is this something I can do with either aptitude or apt-get?
Thanks for any help,
CSF

---

### Post by maxamillion on 2007-03-09
You should be able to install just a base-install with the Alternate installation CD. It should have an option to do so. Otherwise go to debian and do a net or cd install, I know their installer has the option.

p.s. - please use aptitude instead of apt-get (uses the same syntax in most cases so migration should be simple and its a better package manager)

---

### Post by csf111 on 2007-03-09
...hmm, thanks for the reply, BUT a cd is not an option.
Looks like I can do what I want with debootstrap.
CSF

---

