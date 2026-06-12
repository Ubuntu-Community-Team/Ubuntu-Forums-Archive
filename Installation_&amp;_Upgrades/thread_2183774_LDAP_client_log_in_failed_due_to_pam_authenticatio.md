---
title: "LDAP client log in failed due to pam authentication failure"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by webappl on 2013-10-26
Dear all,

I followed this guide ([https://help.ubuntu.com/lts/serverguide/openldap-server.html](https://help.ubuntu.com/lts/serverguide/openldap-server.html)) to install OpenLDAP on a server and a client. After installation, i can log in the OpenLDAP server with an LDAP user. On a client machine, I can query the LDAP user using 'id' command. However, when I tried to log in the client machine with a LDAP user account, I got authentication problem. Looking at /var/log/auth.log, I found the following error:

     [FONT=arial narrow]pam_ldap: ldap_initialize Bad parameter to an ldap routine
     pam_authenticate: Authentication failure[/FONT]

Googled but not able to find anything useful. Does anyone know how to solve this problem? Both server and client machines installed Ubuntu 12.04

Thanks in advance.

Alex

---

### Post by webappl on 2013-10-26
I solved the problem by replacing the /etc/ldap.conf on the client machine with the same named file from another client machine which has a working LDAP configuration. Unfortunately, I don't know what configuration(s) in ldap.conf caused the problem.

---

