---
title: "Upgrade ubuntu to LTS??"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Chow on 2008-04-02
Hi, I need an LTS installation to install Zimbra. I only have the minimal installation done. How can I make it LTS without reinstall??

---

### Post by dstew on 2008-04-02
Do you mean a GUI installation? LTS is "Long Term Support", and it applies to Ubuntu distributions Dapper Drake 6.06 and Hardy Heron 8.04. The latter is still in beta, so the only currently available LTS is Dapper Drake.

I think you want a graphical (desktop) version, and right now you only have the command-line version. If that is correct, you can download the desktop to run on your minimal install by issuing the command:```
sudo apt-get install ubuntu-desktop
```If you have enough memory (more than 256 Mb) and enough disk space (about 10 Gb) this should be able to run a desktop. It takes about an hour to download and install all the packages at DSL speed. After the apt-get command finishes, issue the command```
startx
```and you should get a desktop.

---

### Post by Chow on 2008-04-02
Ah ok. So LTS is only the way of support. Didn't understand that. I thought it was a different install than a normal Ubuntu install.. Thnx for helping me out. New at Ubuntu ;)

---

