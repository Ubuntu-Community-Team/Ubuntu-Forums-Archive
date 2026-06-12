---
title: "Move old database to new disk"
date: 2016-04-10
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2016-04-10
I had a lots of troubles at the end at my 14.04.4 installation and decided to get a new hard disk and install 15.10.

I copied the database directories from the old disk to the new disk into /var/lib/mysql/<database>
phpmyadmin can access the tables and data.

I miss now only the users (and their password). How can I easy copy these data from the old site?

---

### Post by ubfan1 on 2016-04-10
How about the user files (all those under /home/...)?  Don't forget the groups either.  You can try moving the four files /etc/passwd, /etc/shadow, /etc/group, and /etc/gshadow and the /home/... directories and see if that works.  At least the setup will be consistent if you have to go in and reset the passwords to some new default.  save the original files to ensure the non-user groups/userids are still the same in the moved file as on your new system, those could easily change.  If a new non-user id has an old user id, you should change the old user id and the ownership of the user files.

---

### Post by ELMIT on 2016-04-12
Need more help than I thought ;-(

I copied the database directories over, and phpadmin, sees the databases, but when I try to browse the tables, I get:

```
#1146 - Table 'xxxx' doesn't exist
```

How can I get the data?

---

