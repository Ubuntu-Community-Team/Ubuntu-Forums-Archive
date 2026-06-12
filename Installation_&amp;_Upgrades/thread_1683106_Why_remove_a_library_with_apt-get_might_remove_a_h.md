---
title: "Why remove a library with apt-get might remove a huge number of packages?"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by fangzy on 2011-02-07
Remove some library such as libxml2 with apt-get will require the removal of a huge list of packages: 
 
code: ```
sudo apt-get remove libxml2
```
 
message: "The following packages will be REMOVED:
  abiword abiword-common abiword-help abiword-plugin-grammar
  abiword-plugin-mathview alacarte apport apport-gtk apturl at-spi
  avahi-daemon avahi-utils bind9-host bluez-cups bluez-gnome bluez-gstreamer
  ..."
 
In my understanding, the above packages are likely only require "libxml2" library during compilation, but no longer depends on it any more after compilation and installed as binary executable files. If this is true, why apt-get does not allow the user to remove simply "libxml2" rather than such a huge list? Isn't such a huge dependency affects a lot the convenience of package installation and removal?

---

### Post by dino99 on 2011-02-07
if you want to remove a dependency then a bunch of packages are concerned

---

### Post by fangzy on 2011-02-07
> **dino99 said:**
> if you want to remove a dependency then a bunch of packages are concerned

I think the packages are actually not dependent on the library to remove (for example, abiword on libxml2), so why not just allowing the removal of a single library?

---

### Post by TBABill on 2011-02-07
They are dependent upon that file in order to operate. If you remove the dependency lib, you also remove the capability of those programs to run. Thus the condition that to remove it you must also remove the others. The system is not designed to leave broken dependencies behind a removal.

---

