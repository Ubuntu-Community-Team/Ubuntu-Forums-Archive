---
title: "&quot;Unable to Fetch....&quot;"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by king_nile on 2007-10-26
Ahoy all,

I'm having a problem upgrading to Gutsy Gibbon and can't seem to get beyond this error.


>> Failed to fetch [http://mirror.phy.bnl.gov/debian-root/dists/fiesty/fiesty/binary-i386/Packages.gz](http://mirror.phy.bnl.gov/debian-root/dists/fiesty/fiesty/binary-i386/Packages.gz) 404 Not Found


Any ideas are greatly appreciated, thanks.

---

### Post by Pumalite on 2007-10-26
Check you connection. If OK., you could change your server to Main in System>Administration>Sofware Sources; where it says 'Download From'

---

### Post by king_nile on 2007-10-26
My connection is working fine, and I just tried switching my software sources from United States server to Main server. However, after reloading the information about available software from in the sources app I receive the same error.


>> [http://mirror.phy.bnl.gov/debian-root/dists/fiesty/fiesty/binary-i386/Packages.gz:](http://mirror.phy.bnl.gov/debian-root/dists/fiesty/fiesty/binary-i386/Packages.gz:) 404 Not Found

:(

---

### Post by whistlerspa on 2007-10-26
Same here  - in my case it's trying to fetch a package that's not in /etc/apt/sources.list

---

### Post by king_nile on 2007-10-27
any ideas?

---

### Post by taurus on 2007-10-27
Why don't you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out that repo by placing a # in front of it.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

