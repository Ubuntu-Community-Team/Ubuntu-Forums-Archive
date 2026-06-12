---
title: "Prevent package update"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by benhall on 2011-02-26
I've recently downgraded kaffeine to 0.8.8 to get back the EPG which was working under hardy. Is there a simple way to prevent a package from updating when I update the rest of the system? I realise that this is not normally a good idea to keep packages back like this, but the upgrade to kaffeine caused the loss of a useful tool.

---

### Post by sikander3786 on 2011-02-26
Find your package in Synaptic Package Manager under System > Administration sub-menu. Select it, go to Package > Lock Version.

---

### Post by Rubi1200 on 2011-02-26
Yes, there is a way.

In Synaptic Package Manager > find the package > highlight > then from the menu Package > Lock Version

---

### Post by ajgreeny on 2011-02-26
Or you can pin the version you have so that the package will not appear in any terminal update commands you issue.

To pin a package version add these lines to  /etc/apt/preferences:
```
Package: *name*                
Pin: *version* (number from repos)    
Pin-Priority: 1001
```

---

### Post by benhall on 2011-02-27
Thanks for the solutions to all who replied!

---

