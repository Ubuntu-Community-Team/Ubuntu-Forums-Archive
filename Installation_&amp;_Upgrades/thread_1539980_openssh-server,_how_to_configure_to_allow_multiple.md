---
title: "openssh-server, how to configure to allow multiple logins?"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by midaskensai on 2010-07-27
***EDIT: IGNORE THIS PLEASE, for some reason I uninstalled my sshd while being logged in***. *mods feel free to del this*


Hi all,

I would like to login to the openssh-server multiple times simultaneously using the same user and client. How does the config look for that?

It used to work by default on Badger, but now it allows just one connection.

Help appreciated.

---

### Post by Rhubarb on 2010-07-27
That's odd.

It works for me fine here.
Using Ubuntu 10.04 64bit (I also know it works for 32bit clients as well).

Settings for the ssh server can be found in /etc/ssh directory

Otherwise you may have to reset your ssh server back to its default settings:
```
sudo dpkg-reconfigure openssh-server
```
- Which should do the trick.

---

