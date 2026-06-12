---
title: "Lost mysql root info"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by musse1 on 2007-03-22
I really messed up my mysql account. Now I can't login from prompt since I changed the "Host" column. Is there a way to reset the mysql root account or do I need to reinstall it? If i need to reinstall. How do I do that?

---

### Post by upbeat.linux on 2007-03-22
0. Stop mysqld daemon.

1. Locate and open your "my.cnf" file

2. Under [mysqld] insert: skip-grant-tables

3. Find bind-address, make sure it is set to 127.0.0.1. Comment this line out and insert: skip-networking

4. Save and close

5. Restart mysqld

Not quite certain this will work, but its my first suggestion....

---

