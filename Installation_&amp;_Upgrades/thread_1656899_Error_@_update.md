---
title: "Error @ update"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by elnetotaca on 2010-12-31
Hello people, i have this rare error when I try to update;

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up man-db (2.5.7-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried 
1- sudo apt-get autoclean
2- sudo apt-get autoremove
3-  sudo apt-get clean   (limpia)
4-  sudo apt-get update   (recarga info desde los reps)
5-  sudo apt-get upgrade   (actualiza si procede)
6-  sudo apt-get install -f
and nothing, any idea?
thanks in advance.
Neto.

---

### Post by Rubi1200 on 2010-12-31
Hi,
are you still using Edgy?

what version are you currently using?

You could try this, but am not 100% sure it will work:

From the terminal:
```
fuser -v /var/cache/debconf/config.dat
```
Use this to determine which process is locking it and kill the process.

See here for more details:
[https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/349469](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/349469)

Hope this helps.

---

### Post by elnetotaca on 2010-12-31
Oh no, I have the 10.10 now, and that is the only problem I have with it so far!
I am working with the info you gave me, I will post as soon as I get it to work.
Thanks

---

### Post by elnetotaca on 2010-12-31
Thanks Rubi1200 !!!
worked just perfec.
thanks!

---

### Post by Rubi1200 on 2011-01-01
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page. That way, if other users have the same problem they can find a working solution.

---

