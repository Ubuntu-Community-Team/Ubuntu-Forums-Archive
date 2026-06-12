---
title: "kubuntu repositories"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by odysseus.lost on 2006-09-30
Hi,

I am running Ubuntu 6.06. Could someone tell me the kubuntu repositories please? Need to install something from there...

Thx.

---

### Post by pay on 2006-09-30
You could try these```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest dapper main
```

---

### Post by odysseus.lost on 2006-10-02
Thx for that.

---

### Post by aysiu on 2006-10-02
I thought Kubuntu used the same repositoires as Ubuntu...

---

