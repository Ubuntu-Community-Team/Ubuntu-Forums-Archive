---
title: "can't install limewire from .deb"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by Ludford on 2008-01-22
Any idea? package installer has just crashed.

Iv'e tried frostwire aswell but that just won't start


EDIT: I logged out and in and now it's saying "only one software management tool is allowed to run at the same time"

EDIT2: wile trying to install java runtime from add/remove I get 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by stephenbrazier on 2008-01-22
> **Ludford said:**
> Any idea? package installer has just crashed.

Iv'e tried frostwire aswell but that just won't start


EDIT: I logged out and in and now it's saying "only one software management tool is allowed to run at the same time"

EDIT2: wile trying to install java runtime from add/remove I get 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


When installing Limewire, and you dont already have Java installed, you must click Terminal at the bottom of the installer then agree to the Java EULA. Then it installs. I think this is a flaw as it would be better if it came up in popup form. I had the problem and it messed my Ubuntu up, so i reinstalled it. Back up all your data, and if no one comes up with a fix after a while, reinstall Ubuntu, and next time open terminal mode and agree.

Sorry but I cant think of a fix other than reinstall. Worked for me :)

Have a good night.

---

### Post by wolfen69 on 2008-01-22
do what it says and:
```
sudo dpkg --configure -a
```

---

