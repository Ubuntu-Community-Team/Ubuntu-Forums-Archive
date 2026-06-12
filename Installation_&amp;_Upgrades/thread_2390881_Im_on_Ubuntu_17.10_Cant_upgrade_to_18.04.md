---
title: "Im on Ubuntu 17.10 Cant upgrade to 18.04"
date: 2018-05-03
forum: Installation &amp; Upgrades
---

### Post by swapnil.misal on 2018-05-03
E:The repository 'http://in.archive.ubuntu.com/ubuntu zesty Release' does not have a Release file.
This is the error during the update.

---

### Post by oldos2er on 2018-05-03
Either disable or remove that repository.

---

### Post by dino99 on 2018-05-03
Zesty is no more supported; choose a more recent release (18.04 aka bionic is the new released Long Term Support)
Edit : >  sudo nano /etc/apt/sources.list to update it (erase/comment out the zesty line)

---

### Post by oldos2er on 2018-05-03
17.10 Artful is supported until July.

---

### Post by swapnil.misal on 2018-05-04
This worked thank you dino99.

---

