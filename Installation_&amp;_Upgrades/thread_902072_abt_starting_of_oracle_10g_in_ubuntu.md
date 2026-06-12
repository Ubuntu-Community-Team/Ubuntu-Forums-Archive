---
title: "abt starting of oracle 10g in ubuntu"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by bikramthakur on 2008-08-27
is thr anbody who can help me...... in the oracle 10g database setup in ubuntu......m not able to start the database as i get the error on the screen that comes after i select APPLICATION->ORACLE 10g express edition "Operation failed. bikramjit is not a member of 'dba' group."

---

### Post by Partyboi2 on 2008-08-27
Open a terminal (Applications>Accessories>Terminal) and add the user to the group.
```
 sudo usermod -a -G dba bikramjit
```

---

### Post by bikramthakur on 2008-08-27
Thanks Mr. Partyboi2.....but now when i m going to start the database than m not gettin the any screen.....frankly speakin m the new user of oracle ..... so will u plz tell me hw to start the database ....

---

### Post by Partyboi2 on 2008-08-27
Sorry I don't actually use oracle so don't know if I would b e much help. If you are using hardy maybe you can follow [[COLOR=Blue]this guide[/COLOR]]("http://www.pythian.com/blogs/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron") for installing oracle 11g and see if it solves your problem.

---

### Post by bikramthakur on 2008-08-27
no m not using hardy ....!!

---

