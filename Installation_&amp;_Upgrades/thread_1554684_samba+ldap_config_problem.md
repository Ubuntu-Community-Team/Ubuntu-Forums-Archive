---
title: "samba+ldap config problem"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by ani0079 on 2010-08-17
Hello guys,

I've recently installed ubuntu 10.04 x64 on my laptop and was trying to create a PDC on it withamba & ldap so i followed instructions here [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html#openldap-configuration](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html#openldap-configuration) to configure ldap for samba but at this stage

             Then create the directory, reload the **apparmor** profile, and copy              the DB_CONFIG file:             
                         **sudo -u openldap mkdir /var/lib/ldap/accesslog**
**sudo -u openldap cp /var/lib/ldap/DB_CONFIG /var/lib/ldap/accesslog/**
**sudo /etc/init.d/apparmor reload**
 

i noticed that i dont have any DB_config present so i created one and continued

everything went fine and i was getting result as per the document said but at this stage
**ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess**
 where output should be something like this :

[B]dn: olcDatabase={1}hdb,cn=config
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=exampl
 e,dc=com" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=example,dc=com" write by * read
[/B]
it was as follows[B]
ldap_bind: Invalid credentials (49)[/B]
So i dont know what to do with it 

Please Guide me in the matters....
Thanks in advance
Aniruddh Katkar

---

