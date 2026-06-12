---
title: "Updated from 15.04 to 15.10, SSH no longer works, but SFTP does"
date: 2015-10-22
forum: Installation &amp; Upgrades
---

### Post by Justin_Slay on 2015-10-22
So this is a first for me. SSH is not working, but I can SFTP into the server over port 22.

Just did an upgrade over ssh to 15.10. Any suggestions?

I have checked the listenaddress in /etc/ssh/sshd_conf and :: and 0.0.0.0 are both uncommented.

---

### Post by TheFu on 2015-10-23
Try:
```
ssh -vvv userid@IP
```
to see if there are any clear issues in the verbose connection data.

---

### Post by disturbed4686 on 2015-11-05
Update to the newest version of putty, same thing just happened to me. I think there was a security hole that got patched, so you need the newer client.

---

