---
title: "Upgrade stuck upon reboot"
date: 2018-07-16
forum: Installation &amp; Upgrades
---

### Post by rimorob on 2018-07-16
Upgraded 17.10 to 18.04; start-up screen froze on "Starting Network Manager...".  What do I do next?

P.S. I *can* boot into safe mode and am now doing some obvious checks, but I doubt it's any of broken disk/corrupt filesystem/lack of space.

---

### Post by rimorob on 2018-07-16
Further information: fsck freezes after "Reached target Swap"

---

### Post by mIk3_08 on 2018-07-17
Hardware Specification Please

---

### Post by mIk3_08 on 2018-07-17
try to reboot again and try to do the ff. code;
```
sudo fsck -y
```
Then after it was successful you can do;
```
sudo apt-get update
```
```
sudo apt-get clean
```

---

### Post by rimorob on 2018-07-17
This is on Lenovo T430, 16GB RAM, 128GB SSD (30GB free)

---

### Post by rimorob on 2018-07-17
Will try the fsck -y, thanks for the tip.

---

### Post by mIk3_08 on 2018-07-18
okay good luck.

---

### Post by rimorob on 2018-07-25
For anyone who has this issue after me, the problem was nvidia driver on Ubuntu 18.04 not being configured properly out of the box (or the wrong version).  What worked for me was to set it at version 350.

---

