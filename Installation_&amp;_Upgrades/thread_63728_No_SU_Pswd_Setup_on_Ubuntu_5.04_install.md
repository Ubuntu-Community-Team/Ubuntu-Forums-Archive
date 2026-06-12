---
title: "No SU Pswd Setup on Ubuntu 5.04 install"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by Metamorphousthe on 2005-09-08
Got the Ubuntu 5.04 (I believe Hoary, if that helps, a factory distributed cd that came packaged with "live" and "install" CDs for v5.04). I did the installation but nowhere did it ask for me to setup a root password. It did for normal user but not for su priviledges. Now I cannot do any admin work (i.e., adjust my screen resolutions above 640x480 60 hz for a 17" dell FP; install Kubuntu on top of Ubuntu, etc; no admin work). I tried blank password, my password, 'admin', anything I can think of but I can't gain priviledges. How do I set that up so I can work on settings and things?

---

### Post by Lambert on 2005-09-08
you can set up root but ubuntu doesn't do it by default...read this for why

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by bsussman on 2005-09-11
The one user that you did set up has sudo authority.  The Ubuntu designers intend  that to run commands as root.  Of course you can do that to set a root password if, after reading the above cited reference.

Personally, I am getting used to the Ubuntu way - I only use the root account when I have a lot to do that requires it.

---

### Post by Christoff UK on 2005-09-11
So when you want to do anything, just put sudo in front of the command, alternativly to make a shortcut to a grpahical program use the gksudo command...

---

