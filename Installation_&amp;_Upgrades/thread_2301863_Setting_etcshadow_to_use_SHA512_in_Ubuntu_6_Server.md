---
title: "Setting /etc/shadow to use SHA512 in Ubuntu 6 Server"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by squall_leonhart2 on 2015-11-05
I am constrained to using Ubuntu 6.06 Server and it is using MD5 to hash the user passwords I set in /etc/shadow.  I can't seem to find how to configure the system to use SHA512 to encrypt user passwords (e.g. when a user runs the passwd command) so that the passwords are more securely stored on this machine.  How can this be done?

I apologize if I have overlooked this somewhere, but everything I can find relates to just creating a SHA512 hash of a string in the command line, or upgrading SSL certificates, etc. which is not what I need to do.

Thank you for any insight.

---

