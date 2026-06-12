---
title: "CRON Error retrieval"
date: 2016-12-13
forum: Installation &amp; Upgrades
---

### Post by j-a-c-k on 2016-12-13
I am new to Ubuntu and confused.
I want to setup a simple cron job and I see that I am getting errors but I may not see the content of the error because I have no mail transport installed?
Surely there is no requirement that I setup a mail server and a mail client so that I can see why my cron job is failing?
Is there no way to simply redirect the error to a place where I can read the error message?

Jack

---

### Post by steeldriver on 2016-12-13
Have you tried simply redirecting the command(s) standard output and/or standard error to a file?

```

* * * * * /path/to/some/command >> /path/to/some/logfile 2>&1

```

---

### Post by deepakdeshp on 2016-12-13
Hello, This should help you. . [https://ubuntuforums.org/showthread.php?t=2346322](https://ubuntuforums.org/showthread.php?t=2346322)

---

### Post by j-a-c-k on 2016-12-13
Yes, I have tried this, 
* * * * * /path/to/some/command >> /path/to/some/logfile 2>&1

The problem is fixed.
The php page that I was trying to execute now executes and updates the database.

THANK YOU

---

### Post by ajgreeny on 2016-12-13
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

