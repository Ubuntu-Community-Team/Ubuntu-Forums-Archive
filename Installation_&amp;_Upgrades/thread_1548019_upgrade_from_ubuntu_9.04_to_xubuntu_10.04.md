---
title: "upgrade from ubuntu 9.04 to xubuntu 10.04"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by herbert tamayo on 2010-08-07
Hi, I'm still running ubuntu 9.04, I want to upgrade to xubuntu 10.04 but i don't know if this is possible, so here there are my questions:

1. do i have to remove ubuntu-desktop first?
2. what is the package to xubuntu? xunbuntu-desktop?
3. do i have to change my repos?
4. can I use: apt-get dist-upgrade?

regards

---

### Post by ajgreeny on 2010-08-07
It is not so simple, I'm afraid.  In the first place you will have to do this in two steps, 9.04 to 9.10, then 9.10 to 10.04.  You can not uninstall ubuntu-desktop and then do an online upgrade, as that meta-package is needed for that to happen.

If you really want to do it that way, don't do anything about adding **xubuntu-desktop** until you have done the two upgrades of your ubuntu; if you do you will simply download and install, only to then have to download and install in those two steps the upgraded versions.

In all honesty, and to save time and trouble, I think it will be safer and quicker to backup your /home and then do a clean install of either ubuntu or xubuntu.  If you choose xubuntu and decide you don't like it, you can always add ubuntu-desktop to it and you'll have the same as a standard ubuntu, but with the xubuntu apps as well.

---

### Post by snowpine on 2010-08-07
1) Easy way: back up documents and do a fresh reinstall.

2) Hard way: Upgrade 9.04 to 9.10, then 9.10 to 10.04, then [switch to Xubuntu]("http://www.psychocats.net/ubuntu/purexfce").

---

