---
title: "ldap bind issue"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by associates on 2011-08-07
Hi,

I am having difficulty getting the openldap to work on my Ubuntu Server 11.04. 

After following the steps as shown in the openldap server guide - [https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html)

I've created both backend.mycompany.com.au and frontend.mycompany.com.au. I got an error message saying "ldap_bind: Invalid credential (49)" when trying to run "sudo ldapadd -x -D cn=admin,dc=mycompany,dc=com,dc=au -W -f frontend.mycompany.com.au.ldif

Here is my backend.mycompany.com.au.ldif
# Load dynamic backend modules
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb

# Database settings
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=mycompany,dc=com,dc=au
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=mycompany,dc=com,dc=au
olcRootPW: secret
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=mycompany,dc=com,dc=au" write by
anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=mycompany,dc=com,dc=au" write by * read
 
Here is my frontend.mycompany.com.au.ldif
# Create top-level object in domain
dn: dc=mycompany,dc=com,dc=au
objectClass: top
objectClass: dcObject
objectclass: organization
o: mycomporg, Ltd
dc: mycompany
description: LDAP Server 

# Admin user.
dn: cn=admin,dc=mycompany,dc=com,dc=au
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: secret

dn: ou=people,dc=mycompany,dc=com,dc=au
objectClass: organizationalUnit
ou: people

dn: ou=groups,dc=mycompany,dc=com,dc=au
objectClass: organizationalUnit
ou: groups

dn: cn=Manager,dc=mycompany,dc=com,dc=au
objectClass: organizationaRole
cn: Manager

dn: ou=addressbook,dc=mycompany,dc=com,dc=au
objectClass: organizationalUnit
ou: addressbook

dn: uid=jack.beth,ou=people,dc=mycompany,dc=com,dc=au
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: jack.beth
sn: beth
givenName: jack
cn: Jack Beth
displayName: Jack Beth
uidNumber: 1000
gidNumber: 10000
userPassword: XXXXX
gecos: Jack Beth
loginShell: /bin/bash
homeDirectory: /home/jbeth
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: [email]jbeth@mycompany.com.au[/email]
postalCode: 30040
l: Toulouse
o: mycompany
mobile: N/A
homePhone: N/A
title: System Administrator
postalAddress: 
initials: JB

dn: cn=users,ou=groups,dc=mycompany,dc=com,dc=au
objectClass: posixGroup
cn: users
gidNumber: 10000

I have triple-checked between the frontend and the backend but unable to find any faults in them.

By the way, I am also unable to find slapd.conf file under /etc/ldap. All I can see under /ldap directory are ldap.conf, sasl, schema and slapd.d.

Any help that you could give is greatly appreciated.

Thank you

---

