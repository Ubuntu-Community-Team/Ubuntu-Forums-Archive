---
title: "error updating ubuntu"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by justaman on 2008-07-30
I keep getting this error when I try to update my Ubuntu software... 


Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


How do I fix that?

---

### Post by zvacet on 2008-07-31
```
gksudo gedit /etc/apt/sources.list
```

and put # sign in front of deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_   line.save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by justaman on 2008-08-17
now when ever I type a certain combination of letters or numbers fast for example.. when I type "www." my ubuntu screen darkens around the application I was using and freezes, causing me to be able to do nothing but reboot. 

Anyone run into this yet? or is it just me....

-Justaman

---

