---
title: "Update log"
date: 2017-01-22
forum: Installation &amp; Upgrades
---

### Post by Otto-C on 2017-01-22
Ubuntu 12.04.5 updated.

Is there a log where I can see what my last updates were?

tia
otto-c

---

### Post by wildmanne39 on 2017-01-22
Copy and paste this command into the terminal:
```
tail -n25 /var/log/apt/history.log
```
that will list the last 25 if you want more just change 25 to the value you want and run the command.
Thanks

---

### Post by ajgreeny on 2017-01-22
I tend to use the command ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
```which shows only the packages that have been upgraded, listed according to the date it was done and also shows the original and new versions.

You can also see packages installed or removed by using the correct word in place of upgrade, ie
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log

The lists will be long, probably, but have info only about the action you asked for in the form of
```
/var/log/dpkg.log.1:3635:2016-12-20 15:42:23 upgrade ifupdown:amd64 0.8.10ubuntu1.1 0.8.10ubuntu1.2
```

---

