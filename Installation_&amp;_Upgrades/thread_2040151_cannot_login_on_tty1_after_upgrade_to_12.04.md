---
title: "cannot login on tty1 after upgrade to 12.04"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by hbrandt on 2012-08-10
After upgrading from 11.10 to 12.04 I wasn't able to logon to any tty(1-6) any longer.
I found a note in /var/auth.log:
Aug 10 10:13:45 Carlo login[2169]: PAM unable to dlopen(/lib/security/pam_limits.so): /lib/security/pam_limits.so: cannot open shared object file: No such file or directory
I was lucky to find it in /lib/i3186-linux-gnu/security and copied it over to /lib/security.
Now logon is possible again.

---

