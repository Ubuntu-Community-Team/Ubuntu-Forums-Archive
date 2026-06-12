---
title: "upgrading packages"
date: 2018-12-27
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2018-12-27
I have 18.04.1. I usually use synaptic to upgrade. I check Installed(upgradable) and do not see any packages listed. 

Is synaptic best way to keep 18.04.1. up to date?
Why does it appear that this is not working? It has been at least two months since I last installed a package.
Note firefox is listed at 61.0.1
"Linux" is listed at 4.15.0-33.35 and 4.15.0-33.36.

---

### Post by howefield on 2018-12-27
If you do not mind using the terminal with the following commands..

```
sudo apt update
```

this will update the package information held in your machine and near the bottom of the output will tell you how many packages that can be upgraded. Use..

```
sudo apt upgrade
```

to upgrade them.

---

### Post by Impavidus on 2018-12-27
You can use synaptic to keep Ubuntu up to date. Don't forget to click "Reload" (first button), which will cause synaptic to check for updates. Synaptic is as good as several other methods to keep Ubuntu up to date: terminal, update manager. You computer is at the moment not up to date.

---

### Post by ajgreeny on 2018-12-27
It could also be of interest to see the output you get from the ```
sudo apt update
``` command just to check the repos you have enabled are as they should be.

---

