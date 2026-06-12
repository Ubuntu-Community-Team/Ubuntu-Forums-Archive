---
title: "How do I use APTonCD"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by jacatone on 2013-10-06
I created a backup CD using this APTonCD program and restored all my .deb files to my /var/apt/cache file but can't seem to figure out how to reinstall everything. The APTonCD online manual says  "you can install them using apt-get, aptitude or synaptic without need to download them." When I try using apt-get I keep getting "command not found" when I use dpkg -i. How would I go about do this? Thanks.

---

### Post by heir4c on 2013-10-06
U have to be root to use apt-get.
```
sudo apt-get .......
```

---

### Post by oldos2er on 2013-10-06
What was the exact command you used? You'd want something like ```
cd /var/cache/apt/archives

sudo dpkg -i *.deb
```

---

### Post by jacatone on 2013-10-07
I guess I forgot the wild card. Seems to be working. Thanks.

---

