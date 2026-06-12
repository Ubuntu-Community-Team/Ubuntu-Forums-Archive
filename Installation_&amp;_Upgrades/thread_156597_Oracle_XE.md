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

### Post by ape on 2006-04-07
Have you run the configure option as it stated at the end of installation?  You should run `sudo /etc/init.d/oracle-xe configure` and answer the questions asked.

---

