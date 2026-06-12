---
title: "corrupted filesystem tarfile - corrupted package archive"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by gusul on 2010-09-29
Hi, 

during an upgrade process I got the message:
E: /var/cache/apt/archives/linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb: corrupted filesystem tarfile - corrupted package archive

Tried the apt-get clean
Tried changing repository

Same error. Any ideea?
Thanks

---

### Post by mikewhatever on 2010-09-29
Since everything else failed:
```
sudo rm /var/cache/apt/archives/linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb
sudo apt-get update
```

---

### Post by gusul on 2010-09-30
Thanks, will try this.

---

### Post by gusul on 2010-09-30
Have tried. Error still the same...

---

