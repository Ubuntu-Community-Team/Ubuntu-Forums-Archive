---
title: "latest upgrade broke epiphany"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by weasel fierce on 2007-02-13
Im on dapper, and after this nights upgrade through the automatic updater, Epiphany wont load. If i run it in terminal, I get > ** (epiphany:11830): WARNING **: An error occured while calling remote method: No reply within specified time

 after a few seconds

---

### Post by bapoumba on 2007-02-13
Running upgraded edgy here and epiphany is fine.
Did epiphany crash or made forced to quit or something ?
Check if they are any epiphany processes runing (**ps ax |grep epiphany**) and **kill -9 pid**. Replace "pid" in previous command with epiphany's pid.
Does this help ?

---

