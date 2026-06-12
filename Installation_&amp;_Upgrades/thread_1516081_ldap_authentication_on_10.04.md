---
title: "ldap authentication on 10.04"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by danber on 2010-06-23
Hi, I am trying to allow my freshly installed ubuntu 10.04 to authenticate with ldap. I did follow the doc [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) and some other hints with no success.
My needs is just to use an ldap existing server (active directory in my site, but i wish to use it via ldap, not via samba/winbind) to validate users on services using pam modules.
After the package installation the command getent passwd retrieve just local users and I don't understand if my ubuntu client is not querying the server or the server reply with some message.
Has anybody here realized this goal and can give me a clue?
Thank you
Daniele

---

### Post by danber on 2010-07-02
Hi, I did believe this was a quite common item for many of us; may be I was wrong since nobody replied. Or may be this problem arise with this new release ...
I'll try with an older one or centos.
Regards
Daniele

---

### Post by vargax on 2011-01-25
look this... [http://serverfault.com/questions/152134/pam-ldap-authentication-with-ubuntu-10-04](http://serverfault.com/questions/152134/pam-ldap-authentication-with-ubuntu-10-04)

---

