---
title: "Problem in Instaling Sun-java6 on Ubuntu 11.04"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by agni10 on 2011-05-24
I am trying to install Java and when I install sun-java6-jre it says:
Error: Dependency is not satisfiable: sun-java6-bin
but when I tried to install sun-java6-bin it says:
Error: Dependency is not satisfiable: sun-java6-jre

---

### Post by ajgreeny on 2011-05-24
If you use software center or synaptic this will not happen.

I assume you are trying to install packages you have downloaded, or something similar to that.  If so, providing they are .deb packages, you can put them both (or all you need if there are more) in a folder somewhere in /home and then run the command ```
sudo dpkg -i /path/to/folder/*.deb
```

---

### Post by agni10 on 2011-05-24
thanks...

---

