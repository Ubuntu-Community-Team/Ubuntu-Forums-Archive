---
title: "Dovecot upgrade from Courier"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by apettitt on 2011-01-19
I created a new server for a webmail system because the old server crashed.  When I created the server, I installed Dovecot and the old server had Courier.  On the new server, I'm doing virtual users where the old one created system users.  I moved all the folders over for all the users on to the new server and ran the Courier-Dovecot migration script.  The files were created successfully with no issues.  The issue I'm having now is that Dovecot is not seeing any mail in the user's directory.  If I created a new user, it can receive mail with no problems.  Also, if I send an email to an existing user, it gets delivered to the new folder but the dovecot does not see anything in the new folder. 

Any ideas?

---

