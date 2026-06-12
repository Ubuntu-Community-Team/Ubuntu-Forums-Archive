---
title: "Update through iso"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by hero9595 on 2010-08-03
How do you update ubuntu to the next version through ISO.Becauce i  have an iso version of ubuntu 10.10 and i want to update ubuntu 10.04

---

### Post by Darkness Des on 2010-08-03
You could just press Alt+F2 and type in "update-manger -d" and be on your way, OR you could do it your way. Open up Applications -> Accessories -> Terminal and type this in
```
mkdir ~/VirtualDisc
sudo mount "/path/to/maverick.iso" ~/VirtualDisc/ -t iso9660 -o loop
```
and replacing /path/to/maverick.iso with the actual path to the ISO.

---

