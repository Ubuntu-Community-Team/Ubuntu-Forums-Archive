---
title: "Installing DenyHosts on Ubunto 9.10 server"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2010-03-08
Hello
 i am trying to install denyhost on ubuntu 9.10 server, to make it run as daemon.
I am following steps from this link
[http://ubuntuforums.org/showthread.php?t=254149](http://ubuntuforums.org/showthread.php?t=254149)

I have downloaded version 2.5 of denyhosts, but i cannot find thi sfile

/usr/bin/denyhosts.py

Could anyone help me out?

thanks and regards
 marco

---

### Post by anglican on 2010-03-09
The python script that runs denyhosts (assuming you installed from the repository) is /usr/sbin/denyhosts (no .py extension). Everything else is in /usr/share/denyhosts (well apart from the config file and the init script). Installed from the repo. and you should only need to edit /etc/denyhosts.conf.

H

---

