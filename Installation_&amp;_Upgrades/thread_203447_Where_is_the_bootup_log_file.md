---
title: "Where is the bootup log file?"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-06-25
A few days ago I tried the 'hibernate' option on shutdown. I have a dual boot machine and it didn't come back up when I chose Ubuntu, it just locked up partway through. Anyway I cold-booted and seems to work now. The only thing is that I'm getting a few strange messages regarding 'etc/rcS.d' upon booting. It doesn't seem to affect how Ubuntu eventually runs, but it delays the booting process substantially. 

My question is really: how or where can I find a log file of my bootup messages so that I can see exactly what is or isn't working right. I've opened up the system log viewer but I can't find any log file that resembles what I see upon bootup.

I'm a linux newb running a Dapper/XP machine.

---

### Post by taurus on 2006-06-25
It should be in /var/log/messages.  Also, you can view it by
```

sudo more /var/log/messages
-or-
dmesg | more

```

---

