---
title: "apt-get upgrade problem"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by ullal on 2008-03-27
I just went through the usual apt-get update and apt-grade upgrade sequence, and after saying yes to the question of upgrading dovecot-common and dovecot-imapd, my communication line dropped when the screen about the new configuration file came up.

After reconnecting, I keep getting the following error messages, regardless of whether I say apt-get upgrade or dpkg --configure -a to complete the upgrade:

dpkg: error processing dovecot-common (--configure):
  subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of dovecot-imapd:
  dovecot-imapd depeneds on dovecot-common (..); however:
    dovecot-common is not configured yet.
dpkg: error processing dovecot-imad (--configure):
  dependency problems - leaving unconfigured
Errors were encountered while processing:
  dovecot-common
  dovecot-imapd

Please help!!!

---

### Post by bapoumba on 2008-03-27
From a terminal, please run:
```
sudo dpkg --configure -a
```

---

### Post by ullal on 2008-03-28
Thanks you for the suggestion! I think that you did not read that part in my first post that I did use dpkg --configure -a and got the same error messages. I left out the sudo part, which I normally use, in order to save time.

---

