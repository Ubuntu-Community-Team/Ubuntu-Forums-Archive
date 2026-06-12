---
title: "Upgrading Using Terminal"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Ubu-freak on 2009-12-06
Usually when I update I type 
```
 $ sudo apt-get update
```then 
```
 $ sudo apt-get upgrade
```but some stuff won't be upgraded like this, for example right now it shows
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic sreadahead
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```So when my question is how do I update these using terminal?

---

### Post by ArgentStar on 2009-12-06
sudo apt-get dist-upgrade

The basic "upgrade" command wont upgrade anything that requires the removal of something else.  That's why core components like those you mentioned weren't being installed. :)

---

### Post by Ubu-freak on 2009-12-06
yo thanx for the fast reply. it's working now :D

---

