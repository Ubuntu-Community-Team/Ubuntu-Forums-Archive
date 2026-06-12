---
title: "[SOLVED] &amp;quot;Privilege separation user sshd does not exist&amp;quot;  Que'?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by winkerbean on 2007-10-25
I just installed OpenSSH from source and received this message at the end of 'make install':
[INDENT]
/usr/local/sbin/sshd -t -f /usr/local/etc/sshd_config
Privilege separation user sshd does not exist
make: [check-config] Error 255 (ignored)
[/INDENT]

What does the message mean and do I need to worry about it to use SSH Server correctly?

---

### Post by winkerbean on 2007-10-25
I got it.  I had to add sshd as a group and user via groupadd and useradd, respectively.

---

