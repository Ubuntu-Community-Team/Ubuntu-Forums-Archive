---
title: "Installing 3rd Party .debs Wont Install in the Software UI"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by Linux_Resource on 2016-04-22
I have noticed that when you attempted to install 3rd Party deb files via the Software Center UI it will hang, and get stuck in a pending install status until you log off and reboot instead of erroring out. 

Any ideas as to when this might be patched, or at the very least a better work around going forward instead of having to resort to using dpkg to manually install?

Thanks,

- Linux Resource

---

### Post by kc1di on 2016-04-22
install gdebi and use that instead of software center for downloaded .deb files. 
terminal command```
sudo apt-get install gdebi
```

---

