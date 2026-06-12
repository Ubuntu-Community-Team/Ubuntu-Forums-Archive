---
title: "[SOLVED] Where does Ubuntu store all the Synaptic info?"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by iampriteshdesai on 2008-08-14
When we enable extra repositories in Synaptic for the first time, such as Hardy main. It downloads many files (ie. when it is run for the first time). Where are these package information stored? Will I be able to use the current files in case I decide to reinstall Hardy or Upgrade to Ibex.

---

### Post by Diabolis on 2008-08-14
When you enable a new repository in synaptic, it only downloads a list of available packages. It will only download packages if you install them. They are cached in this directory: **/var/cache/apt/archives/**

Why would you want to use the downloaded files if you want to make a new clean install of hardy?

If you upgrade from one version of Ubuntu to another version. It will use a different repository, each version has its own repository. It always have updated versions of the software. Why would you want to use the old files?

---

### Post by Kevbert on 2008-08-14
If you want to save a list of all installed packages, use the terminal command
```
sudo dpkg --get-selections > packback.txt
```

This will save a list of all packages in the file 'packback.txt' in your current directory (normally home).  If you 
save this file somewhere else then you can use it to install all packages to a new kernel/PC. 
When you want to re-install all packages run the following
```
sudo dpkg --clear-selections
dpkg --set-selections < packback.txt
sudo aptitude install dselect-upgrade
```

Hopefully the PC will then download and install all your old packages.

---

### Post by iampriteshdesai on 2008-08-14
Thanx!!!
Kevbert you rock!!!

---

