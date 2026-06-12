---
title: "procmail not working when fetchmail ran"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by kwrxxx on 2006-10-29
I just installed 6.10 and I have installed fetchmail and procmail along with the .fetchmailrc .procmailrc in my home directory. When I run fetchmail procmail is not called. I have setup logging for both programs and there is no log file written for procmail and email is not filtered.  I am also running postfix as the mda. Where should I look to solve this problem?

Beginning of .procmailrc
```

LOGFILE=$HOME/fetchlog/log-procmail-`date +%m-%y-%U`
VERBOSE=no
PATH=/usr/local/bin:/usr/bin:/bin:/sbin:/usr/sbin:/usr/local/sbin:$HOME/bin

```
.fetchmailrc header
```

set postmaster "username"
set logfile $HOME/fetchlog/mailfetch-log

```


TIA
:???:

---

