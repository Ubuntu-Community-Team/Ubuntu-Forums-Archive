---
title: "Feisty Upgrade using Update Manager is Failing"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by graphicghost on 2007-04-22
Hi,

I have installed Ubunty Edgy Eft 6.10 on my system and i tried to update to ubuntu Feisty Fawn 7.04 using Update Manager . While doing that i'am getting the following error.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

please help!

Also the alternate installation method using a CD is not happening. The instructions on the Upgrade webpage is too sketchy,

---

### Post by twoblackeyes on 2007-04-22
I'm having the same problem with the exact same error message. Setting the repositories back to "Main Server" in the Software Sources pref didn't help either.

---

### Post by zvacet on 2007-04-22
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by MikeDev on 2007-04-22
Ah, wondered what the problem was. I was getting the exact same error (also tried changing the server) and did the following to edit and update my sources.list file:

cd /etc/apt
sudo gedit sources.list

then uncommented the lines inserted by automatix,
under
## created by arniefreeremoved
I uncommented the next line as:
# deb http://security.ubuntu.com/ubuntu/[/url] edgy-security universe main multiverse restricted

saved the file then run
sudo apt-get update

Then the upgrade using update manager ran all the way through and I now have feisty installed and working.

---

