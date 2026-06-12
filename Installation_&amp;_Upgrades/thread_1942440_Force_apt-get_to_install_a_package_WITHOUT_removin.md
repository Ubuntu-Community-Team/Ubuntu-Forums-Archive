---
title: "Force apt-get to install a package WITHOUT removing the packages it wants to remove?"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by Amurko on 2012-03-17
```
sudo apt-get install foomatic-db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopencascade-foundation-6.5.0 libgl2ps0 libnspr4-0d:i386
  libboost-date-time1.46.1 blcr-dkms gnash-common blcr-util openmpi-checkpoint
  libopencascade-modeling-6.5.0 libboost-thread1.46.1 libcgns2 libcr0
  openmpi-bin gnash octave-splines mpi-default-bin openmpi-common
  libnss3-1d:i386
Use 'apt-get autoremove' to remove them.
Suggested packages:
  m2300w cjet c2050
The following packages will be REMOVED:
  foomatic-db-compressed-ppds **ubuntu-desktop**
The following NEW packages will be installed:
  foomatic-db
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 1,048 kB of archives.
After this operation, 17.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```


Is there an option to force it to install foomatic-db WITHOUT removing ubuntu-desktop.  I don't care if it is dangerous;  I fully accept the consequences!

---

### Post by matt_symes on 2012-03-17
Hi

You could use apt-get to download the packages only and then install them manually using dpkg.

```
sudo apt-get download foomatic-db
```

or 

```
sudo apt-get install --download-only foomatic-db
```

Check the man page for downloading only with apt-get just to be sure as i forget which ones which.

```
sudo dpkg -i .....
```

You may need to install any dependencies yourself.

I think that may work and as you say, you understand the consequences...

Kind regards

---

### Post by Cheesehead on 2012-03-17
Ubuntu-desktop is simply a metapackage (package containing a list of packages), not the entire desktop system. You can (and should) safely let it be removed.

You can easily reinstall it later, though that will autoremove foomatic-db.

foomatic-db and foomatic-db-compressed-ppds are simply incompatible. They break each other. And the latter is a dependency of ubuntu-desktop. If you force the change, then *every* subsequent package operation will throw an error message about broken dependencies. That's just apt doing it's job.

Apt's recommendation is sound. Let it remove ubuntu-desktop.

Next time you plan to do a release-upgrade, it's a good idea to remove foomatic-db and reinstall ubuntu-desktop before upgrade. That way, all changes to ubuntu-desktop will automatically occur. After the upgrade, you can reinstall foomatic-db.

---

