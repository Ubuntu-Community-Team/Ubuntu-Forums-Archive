---
title: "Mail down - HELP"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by joel@parke.ods.org on 2010-06-08
Hi,  I noticed today that my mail has been down since June 6.  The mail.log file shows:
Jun  6 07:50:08 parke postfix/tlsmgr[24093]: warning: request to update table btree:/var/spool/postfix/smtpd_scache in non-postfix directory /var/spool/postfix
Jun  6 07:50:08 parke postfix/tlsmgr[24093]: warning: redirecting the request to postfix-owned data_directory /var/lib/postfix
Jun  6 07:50:08 parke postfix/tlsmgr[24093]: fatal: open database /var/lib/postfix/smtpd_scache.db: Invalid argument
Jun  6 07:50:09 parke postfix/master[1609]: warning: process /usr/lib/postfix/tlsmgr pid 24093 exit status 1
Jun  6 07:50:09 parke postfix/master[1609]: warning: /usr/lib/postfix/tlsmgr: bad command startup -- throttling

Has anyone else seen this - and what could be the problem.  the smtpd_scache.db data base exists, but is empty.

THANKS for your help!

---

### Post by joel@parke.ods.org on 2010-06-08
[SOLVED]
Solution:
deleted smtpd_scache.db
reload Postfix
- all is well!
I hope this helps someone else.

---

### Post by Smigma on 2010-07-12
Thanks a lot for this solution. This happened to me as well, for no apparent reason. Do you happen to know what causes this, or is it just a freak thing?

---

### Post by Ricardo Lima on 2010-12-15
Thank you very much, 
 
 
worked for me.

---

### Post by Ricardo Lima on 2010-12-15
;) Thank you very much,
 
worked for me.

---

### Post by estoyanov on 2011-09-29
Thank's a ton! Worked for me like a charm as well!

---

### Post by greenpete on 2012-08-18
Hi, I've had this happen twice now on my main server, people are not happy and I have no idea why this keeps happening. Did anyone find out what's causing this db file to become corrupted?

Thanks...

---

### Post by oldos2er on 2012-08-18
Hi greenpete, please start a new thread, this one's two years old.

---

