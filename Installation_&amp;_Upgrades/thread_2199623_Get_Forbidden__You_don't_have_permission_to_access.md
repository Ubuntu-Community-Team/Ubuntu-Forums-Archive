---
title: "Get Forbidden  You don't have permission to access / on this server."
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by sochinda on 2014-01-14
Dear all,

I'm a new comer in Ubuntu Server, and I got an error when I have change Apache2 document root to another location as:
"/media/root/iDisk/wwwroot", that **iDisk** is a new drive that I use open-iscsi from another server.

Please let me know what can i do and what should I have to do. 
Thanks for your advice.

---

### Post by bertan2 on 2014-01-15
In the <Directory /> part of your main configuration file, you have to change the Options to allow access.

---

### Post by spjackson on 2014-01-15
You also need to check that the Apache2 user (www-data) has read access to /media/root/iDisk/wwwroot.

---

