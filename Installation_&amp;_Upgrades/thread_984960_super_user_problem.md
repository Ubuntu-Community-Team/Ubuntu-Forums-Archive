---
title: "super user problem"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by esmailgad on 2008-11-17
Hi everyone
When I activate the update manager and try to install the updates I recieve the following  massage:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


in the terminal when I inter the order SU and the password (composed of letters and numbers) I receive the following message:

melitza@melitza-desktop:~$ su
Password: 
su: Authentication failure
melitza@melitza-desktop:~$ 

How can I solve this problem knowing that the user has already the root permissions in the user groups

---

### Post by rakris on 2008-11-17
Same old 'SU' Problem :P

Ubuntu has disabled Root. Try using "SUDO" prefixed to your any admin command. Give ur user passwd

---

### Post by taurus on 2008-11-17
Why not just run

```
sudo dpkg --configure -a
sudo apt-get update
```

And of course, you need to close update manager first before you run those two commands from a terminal.

---

