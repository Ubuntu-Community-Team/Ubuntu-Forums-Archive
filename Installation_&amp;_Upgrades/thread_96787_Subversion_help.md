---
title: "Subversion help"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by karmon on 2005-11-29
hey im trying to install subversion, but every time i enter: sudo apt-get install subversion on the root terminal, i get:

Reading package lists... Done
Building dependency tree... Done
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate

---

### Post by Leif on 2005-11-29
sudo gedit /etc/apt/sources.list, remove the #s in front of the lines with "universe" and "multiverse", do a "sudo apt-get update", and try again

---

### Post by karmon on 2005-11-29
thanks, but the same thing happened. i'll past my source.list incase i missed anything:


deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by Leif on 2005-11-29
ok, could you please try to delete the #s in front of all the lines starting with deb ?

---

### Post by karmon on 2005-11-29
thanks, i did what you said, did a sudo apt-get update, then tried again, and it worked.

---

