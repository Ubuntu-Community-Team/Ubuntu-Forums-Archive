---
title: "how to uninstall virtualbox"
date: 2019-11-23
forum: Installation &amp; Upgrades
---

### Post by gardnermarquis43 on 2019-11-23
I had downloaded virtualbox via their website then downloaded from ubuntu repositories and think this was a mistake. How to uninstall programs? I hope im inthe right subforum.

---

### Post by SeijiSensei on 2019-11-23
The package Oracle distributes is called virtualbox-6.0 while the one in the Ubuntu repositories is named just virtualbox. If you had downloaded the Ubuntu version first, installing from the Oracle repositories would have removed it.  I don't know if that's true when the order is reversed. So I suggest you try
```
sudo apt remove virtualbox
```
You might discover it's already gone.

I also strongly recommend following the instructions on the VirtualBox site to add the Oracle repository to your installation.  See [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) for details.

If you want to remove both packages then use
```
sudo apt remove virtualbox virtualbox-6.0
```

General help on package management: [https://discourse.ubuntu.com/t/package-management/11908](https://discourse.ubuntu.com/t/package-management/11908)

---

