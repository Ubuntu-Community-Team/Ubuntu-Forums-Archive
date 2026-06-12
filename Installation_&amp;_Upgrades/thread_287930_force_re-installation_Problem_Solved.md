---
title: "force re-installation Problem Solved"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by gungner on 2006-10-29
hi, I've done something very stupid and I need to reinstall. Just using apt-get remove xxx and then apt-get install xxx doesn't help since the hole script doesn't run. In my case I deleted /var/lib/mysql and want to reinstall it. How shall I do to reinstall mysql-server as if it was the first time? I need the script to create all dirs.

cheers, tord

---

### Post by gungner on 2006-10-29
Now it's fixed :) using apt-cashe show I found it out. I used apt-get --purge remove mysql-server-5.0 and then started again and it works!

//Tord

---

