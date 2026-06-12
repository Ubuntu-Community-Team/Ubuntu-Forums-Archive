---
title: "Error BrokenCount &gt; 0"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by cov on 2011-01-12
I use [Lazarus]("http://www.lazarus.freepascal.org/") for programming in Pascal and update it through SVN.

Update Manager has determined that BrokenCount is greater than zero and repairing my system will require the removal of Lazarus.

It also intends to reinstall Evolution (I use Thunderbird if I'm not using Gmail) which I removed as I am running out of space on my root partition.

---

### Post by sikander3786 on 2011-01-12
Please post the output of this command.

Applications > Accessories > Terminal.

```
sudo apt-get install -f
```

Press 'n' where it asks you to make a choice and just post the output.

---

### Post by cov on 2011-01-12
```
root@SNECCII:/opt/lazarus/tools/install# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  fp-units-multimedia fp-units-gtk2 fp-units-fcl fp-units-gfx fp-units-gtk
  libmodplug-dev libdts-dev fp-units-net fp-units-db libogg-dev fp-units-math
  fp-units-fv fp-units-rtl libdca-dev libmad0-dev fp-ide fp-units-base
  liba52-0.7.4-dev fp-compiler fp-units-gnome1 libvorbis-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  lazarus
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 315328 files and directories currently installed.)
Removing lazarus ...

```

---

### Post by sikander3786 on 2011-01-12
Seems like you removed *lazarus*. Did you try re-installing it? Does it still list some broken packages?

And there are some un-needed packages. To remove them,

```
sudo apt-get autoremove
```

---

