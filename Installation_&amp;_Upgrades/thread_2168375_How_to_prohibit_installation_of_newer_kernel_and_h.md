---
title: "How to prohibit installation of newer kernel and headers?"
date: 2013-08-17
forum: Installation &amp; Upgrades
---

### Post by rotation2 on 2013-08-17
Apparently some of my Software does not like newer Kernels. 
Can somebody tell me how to prohibit the installation of newer kernels and headers without compromising apt-get dist-upgrade?

---

### Post by Frogs Hair on 2013-08-17
If you have the synaptic package manager installed there is a lock version option but I have never used it. I can't tell you what associated packages  if any may need to be locked as well. Kernel  updates may included security updates and other benefits. so may want to describe what programs are is breaking and if they are from the Ubuntu repository .

---

### Post by ajgreeny on 2013-08-17
To pin a package version you can add these lines to  /etc/apt/preferences:
```
Package: name
Pin: version (number from repos)
Pin-Priority: 1001
```
However, I am not sure about the use of this for kernels, as each numbered kernel is a different package, so it may not work. There may, however be some way to stop any further linux-image packages being installed, as is the case in Linux Mint, which by default does not install kernel packages during normal updates.  I am searching for this but so far no answer has appeared; I'll keep looking.

---

