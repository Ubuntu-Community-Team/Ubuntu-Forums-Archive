---
title: "openldap ldap_bind: Invalid credentials (49)"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by sanjaydelhi on 2011-01-03
I was trying to learn OpenLdap on Ubuntu 9.04.

```
# slapd.conf - Configuration file for LDAP SLAPD
##########
# Basics #
##########
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/inetorgperson.schema
pidfile /var/run/slapd/slapd.pid
argsfile /var/run/slapd/slapd.args
loglevel none
modulepath /usr/lib/ldap
# modulepath /usr/local/libexec/openldap
moduleload back_hdb
##########################
# Database Configuration #
##########################
database hdb
suffix "dc=example,dc=com"
rootdn "cn=Manager,dc=example,dc=com"
[B]#rootpw secret
rootpw {SSHA}EN3+ZmSaaZSb5ndB9FlDLzs+fM2Sc2lL[/B]
directory /var/lib/ldap
# directory /usr/local/var/openldap-data
index objectClass,cn eq
########
# ACLs #
########
access to attrs=userPassword
       by anonymous auth
       by self write
       by * none
access to *
       by self write
       by * none
```



my ldap.conf is



```
# This file should be world readable but not world writable.

#BASE	dc=example,dc=com
#URI	ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT	12
#TIMELIMIT	15
#DEREF		never

# LDAP Client Settings
URI ldap://localhost
BASE dc=example,dc=com
BINDDN cn=Manager,dc=example,dc=com
SIZELIMIT 0
TIMELIMIT 0
```


then I tested my configuration using

```
sudo slaptest -v -f slapd.conf
```

which was ok.

Then I restared openldap server using


```
sudo invoke-rc.d slapd restart
```


I get following prompt

Enter LDAP Password: 

I entered **secret**


but I get following error

ldap_bind: Invalid credentials (49)

Please help

---

### Post by sanjaydelhi on 2011-01-03
I managed to solve it some how. It was problem that server did not find my configuration file so it started with default configuration. So when I started server manually giving location of file, it started normally.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-21
Could you explain how you did this please. Im going through hell with Samba+OpenLDAP,itll let me use credentials to add the frontend, but after that it just denies access :(

---

### Post by NeedALotOfHelpXD on 2012-03-08
on ubuntu 12.04
following the tutorial here [https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)
i keep getting the ldap_bind: Invalid credentials (49)
when i try ldapadd.
and i'm quite sure that the password for slapd was the one i am using, because i have dpkg-reconfigured it just now.

---

