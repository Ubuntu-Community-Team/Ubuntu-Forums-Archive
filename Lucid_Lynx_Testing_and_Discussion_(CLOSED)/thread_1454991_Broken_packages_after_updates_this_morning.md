---
title: "Broken packages after updates this morning"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kanikilu on 2010-04-15
So I updated this morning, and got the same problem with ttf-indic-fonts as others. I'm not too worried about that one, since I don't use those fonts, but now I seem to have some other broken packages:

```
:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  evolution-data-server initramfs-tools 
The following packages will be upgraded:
  evolution-data-server-common initramfs-tools-bin 
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 226kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  initramfs-tools: Depends: initramfs-tools-bin (= 0.92bubuntu73) but 0.92bubuntu72 is to be installed.
  evolution-data-server: Depends: evolution-data-server-common (= 2.28.3.1-0ubuntu1) but 2.28.3.1-0ubuntu2 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
evolution
evolution-couchdb
evolution-data-server
evolution-exchange
evolution-indicator
evolution-plugins

Keep the following packages at their current version:
initramfs-tools [0.92bubuntu71 (now)]
initramfs-tools-bin [0.92bubuntu71 (now)]

Leave the following dependencies unresolved:
evolution-common recommends evolution
gnome-control-center recommends evolution-data-server
gnome-panel recommends evolution-data-server
ubuntu-desktop recommends evolution
ubuntu-desktop recommends evolution-couchdb
ubuntu-desktop recommends evolution-exchange
ubuntu-desktop recommends evolution-indicator
ubuntu-desktop recommends evolution-plugins
Score is -992
```

Any suggestions? :confused:

---

### Post by dino99 on 2010-04-15
report made on launchpad, and many duplicates too, wait a little to see 8ubuntu2 into repo

this package seem to have relations with  initramfs-tools

For the others packages, i've not trouble, so clean your cache and try install -f

---

### Post by philinux on 2010-04-15
```
sudo apt-get update && sudo apt-get upgrade

then

sudo dpkg --configure -a
```

I did a dist-upgrade to pull in the new kernel.

---

### Post by Yarrgh on 2010-04-15
The only problem I had this morning was the ttf-indic-fonts. Everything else installed just fine.

---

### Post by philinux on 2010-04-15
Looks like the problem with ttf-indic-fonts-core has been fixed. No need for "dpkg -configure -a" now.

---

### Post by Yarrgh on 2010-04-15
Yup. I can confirm that it is now fixed. Installed successfully

---

