---
title: "sendmail error due to messup my /etc/hosts"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by asuten on 2010-04-24
Linux*#localhost*somesite.com*2.6.24-24-server*#1*SMP*Fri*Sep*18*16:47:05*UTC*2009*x86_64

How to fix the #localhost back to localhost, anyone can help

---

### Post by _0R10N on 2010-04-25
I don't understand what your problem really is. But if what you need is to edit the /etc/hosts file, then
```
sudo gedit /etc/hosts
```
should do the trick

Then, remove the # from the beginning of the line and save the changes.
You would probably need to run
```
sudo /etc/init.d/networking restart
```
after editing the /etc/hosts file.

Kind regards!

_0R10N >>

---

### Post by _0R10N on 2010-04-25
Here I let you the output of my /etc/hosts file.
127.0.0.1    localhost
127.0.1.1    0S1R1S
192.168.1.3    serverca


_0R10N >>

---

