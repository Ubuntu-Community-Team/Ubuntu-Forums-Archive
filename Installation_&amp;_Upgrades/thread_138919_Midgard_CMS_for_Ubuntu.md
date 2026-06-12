---
title: "Midgard CMS for Ubuntu"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by rcpettit on 2006-03-02
Anyone had any experiance with installing Midgard CMS on Ubuntu.  I would like to give this a try.  So far no luck in getting it to run.

---

### Post by pccampos on 2006-05-03
Hi,


I used to run Midgard on a breezy install without any problems. Wath out on /var/cache/midgard permission, it is a good idea to run:

```
chown apache:apache . -R
```

on that dir.

On dapper I'm having some problems, I think "apache-mpm-prefork" kills my server. Anyone had any issue on dapper and this apache model?


Pedro

---

### Post by jan on 2007-03-02
Hi,

I just tried to install Midgard on Edgy and I am getting following:
> kozuch@kozuch-desktop:~$ sudo apt-get install midgard-data
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

