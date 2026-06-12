---
title: "webdav under apache2 -- help"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by HS-L on 2006-02-18
Hello,

I've got apache2 running, and I would love to mount my home dir through webdav on another computer on another location.

I can't really figure it out.
Does anyone know a really good how-to for ubuntu?

thx! HS-L

---

### Post by knalle on 2006-02-18
i don't think there are **mod_dav** packages for apache2 yet, if you downgrade to apache 1 you can just do;

**apt-get install libapache-mod-dav**

look for **mod_dav** on the net

---

### Post by HS-L on 2006-02-18
well, it seems that is does work with apache2, but i can only find examples with other setups than the ubuntu setup :)

HS-L

---

### Post by knalle on 2006-02-18
post an setup

---

### Post by HS-L on 2006-02-18
I've got dapper installed ( Server version: Apache/2.0.55 )
and my httpd.conf is apache2.conf and mods are included in a directory.

if i look at this how-to:[*click*](http://www.twilight-systems.com/flacco/mozcal/mozcal-webdav-apache2-rh9.html).
they have a setup that looks more as apache1.3 and i wonder if it is
possible to use the existing useraccounts for authentication.

:)

---

### Post by knalle on 2006-02-18
looks to me that all auth is done by apache so im pretty sure most other guides will work on ubuntu too

---

