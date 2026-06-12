---
title: "Installation problem"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by Poma on 2006-10-11
I have installed xubuntu linux(xubuntu-6.06-amd64) on my machine. After installation I've entered "sudo oem-config-prepare". After reboot the following erro occurs 4 times:

Treceback (most recent call last):
  File "/usr/sbin/oem-config-dm", line 58, in ?
    sys.exit(dm.run(*sys.argv[3:])) 
  File "/usr/sbin/oem-config-dm", line 44, in run
    sys.kill(server.pid, signal.SIGTERM)
OSError: [Errno 3] No such process

And then system asks me to add new user. What should I do?
P.S. I don't know how to work in Linux, and I want to start GNOME to do something.

---

### Post by jason10 on 2006-12-28
> **Poma said:**
> I have installed xubuntu linux(xubuntu-6.06-amd64) on my machine. After installation I've entered "sudo oem-config-prepare". After reboot the following erro occurs 4 times:

Treceback (most recent call last):
  File "/usr/sbin/oem-config-dm", line 58, in ?
    sys.exit(dm.run(*sys.argv[3:])) 
  File "/usr/sbin/oem-config-dm", line 44, in run
    sys.kill(server.pid, signal.SIGTERM)
OSError: [Errno 3] No such process

And then system asks me to add new user. What should I do?
P.S. I don't know how to work in Linux, and I want to start GNOME to do something.




i just had the same problem.  its trying to set the thing up for someone else (if your a reseller). i fixed it by just reinstalling and choosing the first option (command) instead of the oem way.  worked just fine.

---

### Post by jason10 on 2006-12-28
..what are beans?

---

