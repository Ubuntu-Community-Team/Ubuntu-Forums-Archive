---
title: "upgrading ubuntstudio to gutsy; repositories down?"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by bernhardtjeff on 2008-02-25
i'm trying to upgrade ubuntustudio 7.04 to 7.10, but i get an error saying a few repositories couldn't be resolved. here's exactly what it says:

Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'archive.ubuntustudio.org'

is this temporary or is there some other problem? could i just use the regular ubuntu repositories instead? if so, what are they and where do i add them?

thanks.

---

### Post by Cope57 on 2008-02-25
**ALL** UbuntuStudio's packages are now in the official Ubuntu repositories, so there is no need for a separate repository anymore. 
```
sudo gedit /etc/apt/sources.list
```
You should be able to upgrade to Gutsy simply by replacing *archive.ubuntustudio.org *with **archive.ubuntu.com**.
Save it...

 Then a normal dist-upgrade should be entirely possible.
```
sudo apt-get update
```
```
sudo apt-get dist upgrade
```

Then you are finished

---

