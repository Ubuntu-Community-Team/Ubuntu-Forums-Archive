---
title: "[proplem] Update Manager"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by maksen on 2009-12-02
when I login I see this message from Update Manger
I use ubuntu 9.10 desktop

"
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 67 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
"

---

### Post by Soul-Sing on 2009-12-02
```
sudo gedit /etc/apt/sources.list
```
Scroll down to line 67
maybe some third party software source  => put a # in front of that line/or check the syntax
```
sudo apt-get update
```

---

