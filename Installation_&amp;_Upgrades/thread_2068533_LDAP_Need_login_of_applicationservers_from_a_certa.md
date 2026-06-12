---
title: "LDAP: Need login of application/servers from a certain group only."
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by geopcgeo on 2012-10-09
We need to configure LDAP for login to different servers and applications. We have created all users and different groups as follows:
------------------------------
dn: dc=ldapserver,dc=local
dn: ou=people,dc=ldapserver,dc=local
ou: people
dn: uid=geo,ou=people,dc=ldapserver,dc=local
dn: uid=user,ou=people,dc=ldapserver,dc=local
dn: ou=groups,dc=ldapserver,dc=local
dn: cn=server,ou=groups,dc=ldapserver,dc=local
member: uid=geo,ou=people,dc=ldapserver,dc=local
dn: cn=website,ou=groups,dc=ldapserver,dc=local
member: uid=user,ou=people,dc=ldapserver,dc=local
------------------------------

We need scenario in such a way that the users that are member of server need only login to server (that is geo) and users that are member of website need only login to websites (That is user “user”).

Please let me know how we can configure it. For login site we tried by giving DN as cn=website,ou=groups,dc=ldapserver,dc=local and Login Attribute as uid and also member but it is not working.

Can anyone please help us on it. Also please let us know is there any other option for accomplish this scenario.

Thanks
Geo

---

