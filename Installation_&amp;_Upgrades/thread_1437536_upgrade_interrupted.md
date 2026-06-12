---
title: "upgrade interrupted"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by necer_cheniki on 2010-03-24
Hello all,
Yesterday when I let my system(ubuntu 9.10) upgrading to lasted release (ubuntu 10.04 beta1)  I wend to sleep. May laptop battery was  empty and the laptop shut down automatically .
 So I don't know where the upgrade was interrupted , When I start my system today , ubuntu load the grap and try to run the system , but the prompt window appear tell me to enter my user name and my password .After I enter them , the **terminal starts** and I can't see my desktop , how can I do to recover my system.

---

### Post by stlsaint on 2010-03-24
I suggest downloading the latest lucid livecd and use it to backup and data you want and to do a fresh install.

---

### Post by necer_cheniki on 2010-03-24
but, I will lose all my programs witch are installed in my previous system , isn't there a other better solution ?

---

### Post by arjunak01 on 2010-03-24
backup all .deb files from /var/cache/apt/archives then use your karmic cd to reinstall ubuntu. then use ```
sudo dpkg -i *.deb
``` to install the programs

---

### Post by necer_cheniki on 2010-03-24
how can I back up the files ?

---

