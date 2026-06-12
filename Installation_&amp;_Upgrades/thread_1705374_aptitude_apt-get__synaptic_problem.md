---
title: "aptitude apt-get  synaptic problem"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by cjejuni on 2011-03-12
how do i remove a virtual file this ghost in my machine that's triggering  apt-get to stop installs:

E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

APT::Immediate-Configure  <===== where/how-to configure file to change to get rid of this virtual file?

good night, ghosts!

---

### Post by andrewthomas on 2011-03-14
Try 

```
sudo dpkg --configure -a
```

---

### Post by Dr Widdleguy on 2012-03-12
I'm running into this same issue. I've tried that command but all it does is quickly take me a new line to input a command. That command does nothing for me. :/

---

### Post by oldos2er on 2012-03-13
Closed, necromancy.

---

