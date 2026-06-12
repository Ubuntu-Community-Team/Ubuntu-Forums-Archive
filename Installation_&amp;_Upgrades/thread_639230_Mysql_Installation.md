---
title: "Mysql Installation"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by kapilsatija on 2007-12-12
Hi Guys,

I am new to Ubuntu and i am trying to install the mysql on my system.
I typed the following command for the installation of the mysql on my system after inserting the Ubuntu installation CD.

sudo apt-get install mysql

and it showed me the following error message.

Reading package lists...Done
Package mysql is not available,but is reffered to by another package.
This may mean that the package is missing,has been obsoleted,or is only available from another source.
E:Package mysql has no installation candidate.

Can any one help me in installing the MYSQL on Ubuntu.

---

### Post by Partyboi2 on 2007-12-13
mysql is known by another name.
```
sudo apt-get install mysql-client mysql-server mysql-common
```If you are wanting extras,  open up Synaptic Package Manager and do a search for mysql (System>Admin>Synaptic Package Manager)

---

