---
title: "mysql broken after dist-upgrade"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by beginner_ on 2014-04-08
I ran apt-get update and apt-get dist-upgrade and since then I can't install or use mysql.


start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've tried to completeley remove it by apt.get purge mysql-server and rebooted. However when I reinstall it I get the exact same error.

eg. see commands in [http://askubuntu.com/questions/384234/e-mysql-server-5-5-installation-error](http://askubuntu.com/questions/384234/e-mysql-server-5-5-installation-error)
which all were no help


mysql log directory is empty.

What could be the issue?

---

### Post by steeldriver on 2014-04-08
Any mysql related messages in the dmesg log?

```
dmesg | grep mysql
```

---

### Post by beginner_ on 2014-04-09
I realized that even after purging the etc/mysql directory was still there and there was still a file in it (debian start).

I got it to work by doing

sudo apt-get purge mysql-server mysql-client mysql-common mysql-server-5.5
sudo reboot (Note: this was absolutely required, else re installation failed again)
manually delete /etc/mysql folder
sudo apt-get install mysql-server

Note to all:

This was on the test server. Purging removes all mysql config and AFAIK all databases. So never to this on a production server before a proper backup!!!

---

