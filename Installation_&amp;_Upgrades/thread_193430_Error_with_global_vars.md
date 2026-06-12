---
title: "Error with global vars?"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by tehleetnoob on 2006-06-10
I updated from breezy to dapper recently by editing my sources.list, changing all instances of breezy to dapper and installed ubuntu-desktop.  After running apt-get update and apt-get dist-upgrade, everything seemed to be workign alright.  But now when I log in as root, it says:

```
configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)
```

What is this from and how do I fix it?

---

### Post by tehleetnoob on 2006-06-10
I have narrowed the problem down to being a problem with the actual "su" command.  It seems that some variables used in /etc/login.defs may have been obsoleted by the dapper version of su.  Should I just comment out the problem variables, or do they now go by new names?

---

### Post by tehleetnoob on 2006-06-10
Got it fixed, had to make the new login.defs file (login.defs.dpkg-dist) the default instead of my out-dated one.

---

