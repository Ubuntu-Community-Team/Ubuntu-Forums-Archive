---
title: "Clean Upgrade  to 16.04 - how to install same apps as in old install"
date: 2016-06-15
forum: Installation &amp; Upgrades
---

### Post by SBFree on 2016-06-15
Hi:
I've would like to make the move to 16.04 and install the same apps as I have been using in 14.04. Is there an automated way to do this?
Thanks,
scott

---

### Post by Frogs Hair on 2016-06-15
Upgrade or clean installation ?

---

### Post by SBFree on 2016-06-15
I've been in the habit of doing a clean install. Is that unnecessary?
I would welcome an opinion about upgrade in place vs clean install.
Thanks - Scott

---

### Post by Impavidus on 2016-06-15
If the system is reasonably clean, an upgrade is quite reliable. I've done many and only had minor problems a few times. But if the system is not clean, it's less reliable. Make sure that you disable any third-party repositories and proprietary drivers, if you have any. Although I think it should do so automatically.

Note that the upgrade from 14.04 to 16.04 will only be officially available 21 July.

To get the same software packages after a clean install, you could run```
dpkg --get-selections > package.txt
```on the old system to get a list of installed packages in the file package.txt. On the new system, run```
sudo dpkg --set-selections < package.txt
sudo apt-get dselect-upgrade
```to install the same packages. You may be able to make it even cleaner by using **apt-mark** (I haven't read the manual, but you can try) to get the right packages marked as manually installed. And of course, some packages may no longer be available or replaced by others.

---

