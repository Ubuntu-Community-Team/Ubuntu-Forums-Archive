---
title: "fail2ban broken in karmic"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by stmiller on 2009-09-11
fail2ban is still broken as of karmic. A fix is possible by installing python2.5 and editing the fail2ban server startup to call python2.5. 

[https://bugs.launchpad.net/ubuntu/+source/fail2ban/+bug/372304](https://bugs.launchpad.net/ubuntu/+source/fail2ban/+bug/372304)

Could this be worked into a patch? Or pull an update to fail2ban that works with the python 2.6.

Help!

---

### Post by Raptor Ramjet on 2009-09-16
Hmmm...

It's also broken in 9.04.  Even worse I just tried the "install python2.5 and change the shebang in /usr/bin/fail2ban-server" trick from [http://forum.ubuntu-fr.org/viewtopic.php?pid=2605566#p2605566](http://forum.ubuntu-fr.org/viewtopic.php?pid=2605566#p2605566) and it now fails with the following python error:

```

me@myhost:~$ sudo /etc/init.d/fail2ban  restart
 * Restarting authentication failure monitor fail2ban  
Traceback (most recent call last):
  File "/usr/bin/fail2ban-server", line 38, in <module>
    from server.server import Server
  File "/usr/share/fail2ban/server/server.py", line 27, in <module>
    from threading import Lock, RLock
ImportError: No module named threading

```

Just thought it was probably worth mentioning here rather than starting my own "fail2ban doesn't work" thread.

---

### Post by stmiller on 2009-09-16
Update: Chris provided a patch, and a fix has been uploaded. w00t!

[https://bugs.launchpad.net/ubuntu/+source/fail2ban/+bug/372304](https://bugs.launchpad.net/ubuntu/+source/fail2ban/+bug/372304)

---

