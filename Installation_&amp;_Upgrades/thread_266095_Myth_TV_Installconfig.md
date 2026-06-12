---
title: "Myth TV Install/config"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by daverab on 2006-09-26
Hey everyone,

I obviously have no idea what I'm doing. I'm trying to get mythtv working under dapper drake. I can get as far as the setup screen, but it can't connect to the database. Is there something I need to do to initialize a database for mythtv prior to attempting to run mythtv-setup?

I've tried a few different guides and I get to the same point and get stuck.

---

### Post by neptune39 on 2006-09-26
have you installed my-sql, have run mythtv-setup logged in as the mythtv user?

---

### Post by daverab on 2006-09-27
I did that now, but it can't find a spcific table now.

---

### Post by rattking on 2006-09-27
Have you ran
mysql -u root < /usr/share/mythtv/sql/mc.sql
to create the initial database?
hope that helps

---

### Post by teet on 2006-10-07
Dude, you may want to hold off trying to set up a myth box on Dapper.

The next version of Ubuntu, which should be released sometime in October, comes with MythTV 0.20 (compared with the 0.18.1 version we have now in dapper) plus there are supposed to be working LIRC modules so you can get your remote control to work easily.

-teet

---

### Post by lonce on 2006-10-07
Its not to hard to get myth setup on dapper.  I set them up for a living using .20 myth on ubuntu.  Check out my website in my signature.

---

