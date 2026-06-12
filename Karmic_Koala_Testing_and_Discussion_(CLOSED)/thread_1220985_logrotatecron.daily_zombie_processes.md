---
title: "logrotate/cron.daily zombie processes"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by omgbots on 2009-07-23
Anybody else having and issue with logrotate becoming a zombie every night?  Some of my logs are rotating properly, but others (messages, daemons, maybe a couple others) seemed to have stopped.  If I run the logrotate command by hand, it finishes and returns (although still doesn't rotate some logs that should be I think)... so maybe it is an issue with cron.daily not wait()'ing on the process in combination with some screwed up /etc/logrotate.d/ configs?

---

