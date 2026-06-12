---
title: "how to install a ppa package by apt"
date: 2020-01-29
forum: Installation &amp; Upgrades
---

### Post by janvi2 on 2020-01-29
I like to resolve depencies by 

@Artemis:~/kicad$ sudo apt-get build-dep kicad-dev-nightly
Reading package lists... Done
E: Unable to find a source package for kicad-dev-nightly

Before I installed the ppa by 
sudo add-apt-repository ppa:js-reynaud/kicad-dev-nightly

It appears in the Software&Update Other Tab while apt complains about no source package

---

### Post by deadflowr on 2020-01-29
The ppa contains no such package as kicad-dev-nightly
There is
kicad-nightly
kicad-nightly-dbg
kicad-nightly-demos

---

### Post by TheFu on 2020-01-29
Did you refresh all the packages after adding the new PPA?
```
sudo apt update
```

---

### Post by janvi2 on 2020-01-29
Many thx. Update was done and kicad-nightly instead kicad-dev-nightly works correct.
I wonder about that before 18.04LTS accepted the kicad-dev-nightly package name.
Version now is 19.10 Desktop

---

