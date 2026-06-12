---
title: "system-config-printers can't connect to server, cups won't uninstall/reinstall"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by mpnordland on 2011-03-09
A few days ago out of the blue, cups quit working. I tried restarting it, and different things, but none worked so I thought, I'll just reinstall. No go. for some reason, whenever I try to uninstall it, once it gets to removing cups, it just sits there. Please help.

---

### Post by mpnordland on 2011-03-09
bump
bump
I need some help here :)[-o<

---

### Post by siraf on 2011-03-26
Here's what I did to break my cups (below is how I fixed it): 
I installed xpdf-utils, which un-installed a number of items, including "ubuntu-desktop" which is a meta-package.

I fixed my system by reinstalling "ubuntu-desktop":
```
sudo apt-get install ubuntu-desktop
```

if that doesn't work, try:
```
sudo apt-get install ubuntu-desktop --reinstall
```

and if that still doesn't work, try installing these:

```
sudo apt-get install bluez-cups cups cups-driver-gutenprint cups-common ghostscript-cups hplip poppler-utils
```

I sincerely hope that helps. PM me if it doesn't.

---

