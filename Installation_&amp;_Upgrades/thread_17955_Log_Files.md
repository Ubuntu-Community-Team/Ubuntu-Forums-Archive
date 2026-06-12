---
title: "Log Files"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by rusi_pathan on 2005-03-03
Quick question

How do I get all the files in /var/log to be replaced every time the system boots instead of being appended.

Just dont want them to grow a lot.

Thanks

---

### Post by alastair on 2005-03-03
They shouldn't - they get rotated daily i.e. moved to a ".1" etc. This is controlled via the /etc/logrotate* system, run via anacron.

---

