---
title: "New packeges, old distro...."
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by key7 on 2007-05-20
Hi to everybody,
I am an happy Ubuntu 6.06 LTS (Dapper) user. 
There is a thing that i dont' get.

When a new version of a software that i Installed come out, the upgrade manager does not always signal me that is available.
For instance, i installed via Synaptic K3b 0.12.17. Now the version 1.0 is out, the package is availabe for Feisty but not for dapper.
I also added the line 
```
deb http://archive.ubuntu.com/ubuntu **dapper-backports** main restricted universe multiverse
```
to my sources.list but both the upgrade manager and Synaptic tell me that there is nothing to upgrade.
I also tried 
```
sudo apt-get upgrade k3b
``` 
but with no results.
The same with rhythmbox, evolution and others.....

A few days ago the upgrade manager signalled me that Samba needed to be upgraded.

My questions are: 
1) Why Samba yes and K3b no ?
2) To have the latest packages (as long as they are not included in the backports) do I have to upgrade my ubuntu version every 6 months or compile them from sources ?

Thanks in advance

---

### Post by public_void on 2007-05-20
Only security and bug fixes (I think) are available for Dapper. To obtain the latest version of a program you have to install it yourself. This is to maintain the stability of the release, as newer versions of programs often require newer libraries, whereas some program require older version. Possibility leading to problems with dependencies, and to avoid this, newer packages aren't in the official repositories. The backports team create packages of some of the newer versions of packages, again to address security issues or bug fixes. If you want the latest packages, then you need the latest version of Ubuntu which will have them. However when the latest version of Ubuntu is released the package versions are frozen again to maintain stability (except for security and bug fixes), so upgrading every six months is the only solution. Although as stated before you can install your own programs.

This is how I understand it, so I hope this helps. If there is something incorrect with what I said, please say.

---

