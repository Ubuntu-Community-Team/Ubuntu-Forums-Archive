---
title: "Hardy Upgrade caused apt problem"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by quee0849 on 2008-04-28
I have just upgraded to Hardy from Gutsy on my 64 bit system. I had alamin-server installed previously (to send SMS messages) - now Synaptic wont work, apt wont work, producing an error
E: alamin-server: subprocess post-removal script returned error exit status 1
I've tried to remove this package with apt-get remove; apt-get -f remove; dpkg -r alamin-server; all produce errors :

Removing alamin-server ...
chown: cannot access `/var/run/alamin': No such file or directory
dpkg: error processing alamin-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 alamin-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


Right now I cant install or remove any packages - the rest of the system works fine though.

---

### Post by Peter09 on 2008-04-28
Can you use sudo

```
sudo <any command here>
```

does it return an error?

PC

---

### Post by quee0849 on 2008-04-28
Yes I can sudo firefox no problem.

---

### Post by dboy on 2008-05-03
same issue. alamin errors when apt-get:


chown: cannot access `/var/run/alamin': No such file or directory
dpkg: error processing alamin-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 alamin-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


have no idea why it's trying to --remove

dboy

---

### Post by dboy on 2008-05-03
Ok, easy fix:

sudo touch /var/run/alamin

apt-get update


dboy

---

