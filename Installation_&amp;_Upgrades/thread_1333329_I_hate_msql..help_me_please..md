---
title: "I hate msql..help me please."
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by acousticstraw on 2009-11-21
Ok I am a noob..kind of. Been a geek all my life but took the next step to geek hood and got ubuntu. But I cannot fix msql server. I can't get rid of it, or anything. Its so annoying. I have tried all the apt-get -f and everything nothing works. Please help. here is the code that I am getting when I try and fix the bug. oh and I can't report the bug because ubuntu tells me that msql is not a ubuntu package. HELP!!! Thanks all.
[B]
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
chown: cannot access `/var/run/mysqld': No such file or directory
Reloading AppArmor profiles : done.
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

---

