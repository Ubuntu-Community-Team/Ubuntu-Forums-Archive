---
title: "Display duplicating on new install"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by tseibert on 2016-05-16
Brand new install with both ubuntu-14.04.4-desktop-amd64.iso and ubuntu-16.04-desktop-amd64.iso

No additional drivers appear for the display and no settings in the display options make any difference.

Pc is an HP ProOne 600 G2 - [https://www.cdw.com/shop/products/HP-ProOne-600-G2-Core-i5-6500-3.2-GHz-4-GB-500-GB-LED-21.5in/3859190.aspx](https://www.cdw.com/shop/products/HP-ProOne-600-G2-Core-i5-6500-3.2-GHz-4-GB-500-GB-LED-21.5in/3859190.aspx)

Any help or suggestions would be greatly appreciated.
[ATTACH=CONFIG]269125[/ATTACH]

---

### Post by tseibert on 2016-05-17
Found a similar display issue on another thread and tried getting the drivers for the intel HD graphics 4600 via

```
sudo apt-add-repository ppa:ubuntu-x-swat/intel-graphics-updates
sudo apt-get update 
sudo apt-get dist-upgrade
```

with no success.

---

### Post by lisati on 2016-05-17
Shouldn't that be:
```
sudo apt-add-repository ppa:ubuntu-x-swat/intel-graphics-updates
sudo apt-get update
sudo apt-get dist-upgrade

```
with the commands on separate lines?

---

### Post by tseibert on 2016-05-18
Yeah sorry about that.

---

