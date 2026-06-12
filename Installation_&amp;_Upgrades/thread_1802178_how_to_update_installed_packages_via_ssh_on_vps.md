---
title: "how to update installed packages via ssh on vps?"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by geekcube on 2011-07-11
installed on: vps using 10.10 64 bit

i just want to make sure my lamp stack, mongo + other installed software is up to date, but i only have ssh. i run apt-get update, and it shows me available package, but it does not install the updates.

is there a quick command for this?

i tried searching for "update 10.10" before posting this thread.

thanks inadvance :)

---

### Post by papibe on 2011-07-13
'apt-get update' does not modify any software installed in your server. What it does is update the list of changes that are available. In order to actually get the newest versions you need to ran an upgrade.

They both are usually run one after the other:
```
$ sudo apt-get update
$ sudo apt-get upgrade
```
Regards.

---

