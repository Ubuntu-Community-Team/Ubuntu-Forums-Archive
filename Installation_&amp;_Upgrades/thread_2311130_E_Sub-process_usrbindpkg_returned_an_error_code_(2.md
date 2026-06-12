---
title: "E: Sub-process /usr/bin/dpkg returned an error code (2) ubuntu 14.04"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by criboy45 on 2016-01-24
when ever I try to update or install an apt I usually get this message in the software center

Package operation failed The installation or removal of a software package failed.

and in the terminal I usually get this

$ sudo apt-get install unity-tweak-tool
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libxfixes3:i386
The following NEW packages will be installed:
  unity-tweak-tool
The following packages will be upgraded:
  libxfixes3:i386
1 upgraded, 1 newly installed, 0 to remove and 79 not upgraded.
1 not fully installed or removed.
Need to get 0 B/343 kB of archives.
After this operation, 2,669 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
E: Sub-process /usr/bin/dpkg returned an error code (2)

Can anyone help me fix this?

---

### Post by Bashing-om on 2016-01-25
criboy45; Hello .

Given:
> 
1 upgraded, 1 newly installed, 0 to remove and 79 not upgraded.


What results when updating the system:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```

Get the system fully updated, then

[INDENT][INDENT]see if a situation still exist
[/INDENT][/INDENT]

---

