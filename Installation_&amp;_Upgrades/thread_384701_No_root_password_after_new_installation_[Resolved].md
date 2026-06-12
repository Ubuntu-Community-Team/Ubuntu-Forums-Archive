---
title: "No root password after new installation [Resolved]"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by duli on 2007-03-14
Hello!

I just installed ubuntu 6.10 on my notebook. Now it seems that during the installation process I just was asked to set up a user account with name and password but had no possibility to enter specify a root password. As I'm quite reluctant to drop the whole installation and install again it would be nice to know whether there are ways to get such password. Any hints?

---

### Post by r4ik on 2007-03-14
Please read,

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck !

---

### Post by JAwuku on 2007-03-14
Ubuntu, like Mac OSX, uses the  **sudo** prefix to enable root privileges. You just use your own user password. For example, to install the c compiler, you type

```
sudo apt-get install build-essential
```

If you want root priveleges for GUI apps, e.g. gedit, simply use the **gksudo** prefix

```
gksudo gedit /etc/apt/sources.list
```

There are ways of setting up a separate root account if you prefer, but it's beyond my expertise.

---

### Post by JAwuku on 2007-03-14
> **r4ik said:**
> Please read,

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck !

beat me to it!:lolflag:

---

### Post by duli on 2007-03-14
It works. 
Thanks a lot!

---

