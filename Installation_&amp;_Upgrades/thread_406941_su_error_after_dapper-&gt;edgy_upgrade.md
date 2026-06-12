---
title: "su error after dapper-&gt;edgy upgrade"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by herot on 2007-04-11
i used the official method to upgrade dapper to edgy and everything seems to work for the most part... however, i get this message when changing to root:

andrew@andrew-desktop:~$ su
Password: 
configuration error - unknown item 'FAIL_DELAY' (notify administrator)
root@andrew-desktop:/home/andrew# 

what does this mean? what should i do?

---

### Post by bulldog on 2007-04-11
Try the command```
sudo -s
```

---

### Post by herot on 2007-04-12
that didn't do anything

i still get the message

---

### Post by bulldog on 2007-04-12
Hmmm.........strange,after typing my password,I'm root with this command,without any error notifications.

---

