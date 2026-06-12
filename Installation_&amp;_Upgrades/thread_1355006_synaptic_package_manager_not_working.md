---
title: "synaptic package manager not working"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by anamika on 2009-12-14
my synaptic package manager is not working. 
this is the error
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i cant install vlc media player  or anything else

itried running this script but its not working
this was the error
dpkg: parse error, in file `/var/lib/dpkg/updates/0076' near line 1:
 EOF after field name `

please help

---

### Post by stlsaint on 2009-12-14
> **anamika said:**
> my synaptic package manager is not working. 
this is the error
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i cant install vlc media player  or anything else

please help

in terminal run: sudo dpkg --configure -a

---

### Post by kellemes on 2009-12-14
> **anamika said:**
> my synaptic package manager is not working. 
this is the error
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i cant install vlc media player  or anything else

please help

Just follow the advise.
Open a terminal window and enter..
```
sudo dpkg --configure -a
```

---

### Post by wojox on 2009-12-14
Okay open the terminal Applications > Accessories > Terminal and run:

```
sudo dpkg --configure -a
```

---

