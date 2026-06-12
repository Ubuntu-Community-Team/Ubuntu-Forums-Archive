---
title: "Complete internet install?"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by revenger681 on 2011-02-08
Hello.
Perhaps this was covered somewhere else, forgive me if it is... But I am wondering if there is a way to install ubuntu netbook edition completely from the WWW. I thought I had done it before (almost certain I did), but I might have done it with SuSE, not sure. I've googled and searched and haven't found instructions yet with Ubuntu. The articles I found were either installing from a local network and etc. but not from the world wide web.. Others had programs to download (which I might try) to get the installation rolling. I remember doing it the first time simply booting my laptop up (it's an old laptop), pointing it at some http or FTP server, and it downloaded the boot/install files from there and began installing packages right from the boot menu. I didn't have any programs installed on windows or anything else prior, if I remember correctly... 

Can someone point me in the right direction?
Again I apologize, I'm sure it's here somewhere... But i've been searching for hours....

---

### Post by P4man on 2011-02-09
Im not quite sure what you are trying to achieve. If you want a minimal install cd/stick to boot from and kickstart the installation, have a look here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If you need a "no install medium" install, you would need a machine that supports booting PXE (or similar) network boot, but thats not routable over the internet AFAIK, and would probably be terribly slow anyway.

---

