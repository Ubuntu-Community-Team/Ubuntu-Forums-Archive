---
title: "Needing to upgrade Libgtk =&gt; 1,2,0"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by eNathan on 2008-01-11
Hi, I'm new to these forums. I'm a windows developer wanting to start coding on Linux systems. I'm running Ubuntu 7,10. I'm trying to install Kylix 3, and during the installation, I get this error:

> Libgtk version >= 1.2.0....FAILED

Your system does not meet the minimum system requirements.
Setup cannot continue.


In the installation guide it specifies that I need atleast Libgtk 1,2,0. Apparently, I do not have it. I need to upgrade (I've trued things like sudo apt-get libgtk, etc, with no luck).

**How do I install Libgtk => 1,2,0?**

Thank you. Any help would be greatly, greatly appreciated. My entire linux experience has been nothing but problem after problem (thus far). :(

:lolflag: <-- Nice smilie.

---

### Post by Partyboi2 on 2008-01-11
Maybe you need libgtk1.2-dev 
```
sudo apt-get install libgtk1.2-dev
```or later version libgtk2.0-dev
```
 sudo apt-get install libgtk2.0-dev
```

---

