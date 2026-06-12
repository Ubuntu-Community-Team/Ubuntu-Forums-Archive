---
title: "Automatic Login In Server 6"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by juanbe on 2006-07-10
I have e installed the server version of UBUNTU 6 and I need to make an automatic login of a user, to run after this NCPFS (ncpmount with a certain user) and a CRON task for making backup from a Novell Server.
How can I make the automatic Login ? In Ubuntu there's no mingetty...and when I tried to install it with the apt-get there tons of dependencies where needed...
Thanks
Best regards.

---

### Post by mssever on 2006-07-10
I don't know about NCPFS, but to use cron, you don't need to be logged on. As long as the machine is up, it will run cron jobs as the user that owns the job.

---

