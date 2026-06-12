---
title: "openLDAP with memberOf attribute"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by moksh on 2011-12-30
Hi,

I am very new to LDAP and I wanted to know how to authenticate a user based on which group they belong in. I am trying to setup an LDAP server with the following structure: (On ubuntu server 9.10)

[B]dn: dc=example,dc=com
objectClass: top
objectClass: dcObject
objectclass: organization
o: Example Organization
dc: Example

dn: cn=admin,dc=example,dc=com
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: secret


dn: ou=people,dc=example,dc=com
objectClass: organizationalUnit
ou: people

dn: ou=groups,dc=example,dc=com
objectClass: organizationalUnit
ou: groups

dn: cn=test,ou=people,dc=example,dc=com
objectClass: inetOrgPerson
uid: test
sn: test
givenName: test
cn: test test
displayName: test test
userPassword: mypass
mail: [email]test@example.com[/email]
title: System Administrator

dn: cn=developers,ou=groups,dc=example,dc=com
objectClass: groupOfNames
cn: developers
member: cn=test,ou=people,dc=example,dc=com[/B]


I have followed the guide from here until populating the database. [https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.04/serverguide/C/openldap-server.html) 

The LDAP server sets up perfectly and I can access it using Apache directory studio but when I try the following filter (uid=test), I get a hit back. But when I do (&(uid=test)(memberOf=cn=developers,ou=groups,dc=example,dc=com)) I don't get any hits. I am using the following filter in bugzilla to authenticate valid users from developers group:

(memberof=cn=developers,ou=groups,dc=example,dc=com) which gets AND by the LDAPloginattribute of "uid". If I don't specify the attribute then I can login with user test in bugzilla, but with the filter it fails. 

Can someone please help me?

---

### Post by luvshines on 2011-12-30
It fails because there is no 'memberof' attribute defined for that user.
LDAP will not create memberof for you if you have mentioned it as 'member' under the group
You'll have to change your filter

---

### Post by moksh on 2011-12-30
How do I create a memberOf attribute for that user?

---

### Post by luvshines on 2011-12-31
> **moksh said:**
> How do I create a memberOf attribute for that user?

I think the 'memberOf' overlay should work fine for you.
Check it out under 12.8 [http://www.openldap.org/doc/admin24/overlays.html](http://www.openldap.org/doc/admin24/overlays.html)

Also man slapo-memberof

This should do the trick of creating memberOf attribute for you and updating it as and when the member group attribute is changed.

PS: I haven't used it personally though

---

### Post by moksh on 2011-12-31
In the guide that you gave me, I have to modify the slapd.conf file in /etc/ldap folder, but there's no such file. I see ldap.conf and I think the slapd.conf file is no longer in use! From the guide that I posted I am using the following as my config to create the database. What do I need to add in order to make the memberOf working properly?

[B]# Load dynamic backend modules
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb.la

# Database settings
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=example,dc=com
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=example,dc=com
olcRootPW: secret
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=example,dc=com" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=example,dc=com" write by * read[/B]

---

### Post by luvshines on 2012-01-01
Oops !! I am still using the orthodox method of slapd.conf so won't be able to help much here

The following link has info on the same [http://forum.zentyal.org/index.php?topic=4174.0](http://forum.zentyal.org/index.php?topic=4174.0)

You might want to give it a try or wait for some new config style LDAP expert to reply to this thread [-o<

Note: You'll have to delete and repopulate the 'groupOfNames' entries after enabling the overlay so that memberOf is populated too

---

### Post by moksh on 2012-01-02
I tried that solution but it doesn't seem to work because I don't have one of the file it is asking me to edit. These are the files I have:

root@ldap:/etc/ldap/slapd.d/cn=config# ls
cn=module{0}.ldif  cn=schema.ldif              olcDatabase={-1}frontend.ldif
cn=schema          olcDatabase={0}config.ldif  olcDatabase={1}hdb.ldif

So I edited the **olcDatabase={1}hdb.ldif** and did everything it asked me to do in there but no avail. Are you aware of any other LDAP service on linux that I can implement which doesn't have memberOf overlay implementation such a pain?

---

### Post by moksh on 2012-01-06
Just did the following to make it work

vi memberof.ldif

------

dn: olcOverlay={0}memberof,olcDatabase={1}hdb,cn=config
objectClass: olcConfig
objectClass: olcMemberOf
objectClass: olcOverlayConfig
objectClass: top
olcOverlay: memberof

-------

sudo ldapadd -Y EXTERNAL -H ldapi:/// -f memberof.ldif

**[SOLVED]**

---

### Post by ExPerT2k on 2012-01-07
hi,

it's not working for me.
i'm getting:
```
adding new entry "olcOverlay={0}memberof,olcDatabase={1}hdb,cn=config"
ldap_add: Invalid syntax (21)
	additional info: objectClass: value #1 invalid per syntax
```

what i'm doing wrong?

---

### Post by luvshines on 2012-01-07
> **ExPerT2k said:**
> hi,

it's not working for me.
i'm getting:
```
adding new entry "olcOverlay={0}memberof,olcDatabase={1}hdb,cn=config"
ldap_add: Invalid syntax (21)
	additional info: objectClass: value #1 invalid per syntax
```

what i'm doing wrong?

Maybe you are referring to some objectClass which is not known to the ldap server since the schema which contains it has not been loaded.

---

