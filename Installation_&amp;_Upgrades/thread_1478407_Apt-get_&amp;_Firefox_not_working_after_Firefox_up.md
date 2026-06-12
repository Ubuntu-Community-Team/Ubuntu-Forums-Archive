---
title: "Apt-get &amp; Firefox not working after Firefox update"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by ve3dvv on 2010-05-09
Symptoms after the updates;
- have 2 systems running ubuntu 9.10 and both did the same thing after the update. 
Firefox gives message: Firefox can't find the server at .......

- After uninstalling Firefox I found out Apt-Get cannot access the network anymore also. Reinstalling Firefox from the the distro CD did not help.

- Update Manager stopped working as well. "Could not resolve 'us.archive.ubuntu.com'

NOTE:
Somehow my virtual machines installed under VBox can still use the network and use Apt-Get, Update Manager or Firefox, but only when bridged.

John

---

### Post by lemming465 on 2010-05-10
Smells like a DNS problem.  Do you get a different result from *dig [www.wisc.edu](www.wisc.edu)* than from *dig @8.8.8.8 [www.wisc.edu](www.wisc.edu)*?  If so, hand-edit /etc/resolv.conf (sudo nano ...) and put some nameserver lines in, e.g. *nameserver 8.8.8.8*.  Beware, the configuration problem may have dhclient and NetworkManager reverting it to broken on you.

---

### Post by ve3dvv on 2010-05-11
You are right on! 
I edited /etc/resolv.conf an put a valid address in it (my routers address).

I also can get my updates again............................

Thanks a bunch:guitar:

John

---

