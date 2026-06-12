---
title: "Oracle XE"
date: 2006-04-07
forum: Installation &amp; Upgrades
---

### Post by gustavo.martim on 2006-04-07
The command to start Oracle XE doesn't work in my Ubuntu 5.10.

I didn't have error message while the instalation and now with the command /etc/init.d/oracle-xe start I don't have any message but the Oracle doesn't start.

Where can I find log information? What can I do?

Thanks,
Gustavo.

---

### Post by lnxpwr on 2006-04-07
how do you recognize that oracle is not running ? did you tried the graphical start/stop ? did you tried in a terminal: sqlplus "/as sysdba" --> this should tell you the status of the db. are you the right user who is allowed to use the db ?

---

### Post by gustavo.martim on 2006-04-07
[QUOTE=lnxpwr]how do you recognize that oracle is not running ? did you tried the graphical start/stop ? did you tried in a terminal: sqlplus "/as sysdba" --> this should tell you the status of the db. are you the right user who is allowed to use the db ?[/QUOTE]

I used "ps aux" to see that the oracle is not running.

---

### Post by lnxpwr on 2006-04-09
try to log in with the "oracle" user, and start the database via:
  sqlplus "/as sysdba"
  sqlplus> startup

---

