---
title: "[SOLVED] Authenticate against LDAP on 8.04?"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by derdud on 2008-06-03
I was wondering if it's possible to have logins authenticate against our Active Directory server. I'm running the server version (no GUI) of 8.04. 

Is there a guide that explains this for someone who has never worked with LDAP authentication on Ubuntu before?

---

### Post by borobudur on 2008-06-11
What you need are user accounts and access control on the LDAP server:


**User Account**
Create an user in your tree structur with an encrypted password
```
slappasswd -h {MD5}
```Copy the string to the user data:
```
gedit ~/useraccount.ldif
``````
dn:uid=user_x,ou=users,dc=subdomain,dc=dyndns,dc=org
uid: user_x
userPassword: {MD5}xKrscj3G9/oSEv5AoeEg==
objectClass: top
objectClass: account
objectClass: simpleSecurityObject
```Add the user file data: 
 ```
sudo ldapadd -x -D 'cn=Manager,dc=subdomain,dc=dyndns,dc=org' -W -f useraccount.ldif
```**Access Control**

Edit the accesss declarations in ***/etc/ldap/slapd.conf***, e.g.:

```
access to dn.children="ou=addressbook,dc=subdomain,dc=dyndns,dc=org"
        by dn="uid=user_x,ou=users,dc=subdomain,dc=dyndns,dc=org" write
        by anonymous auth
        by * read
```The user user_x (second row) has write privilege to all children of the address book (first row).

With the ldapsearch statement you get all entries of the address book (-b = access node, -D = user):

```
ldapsearch -LLL -x -b 'ou=addressbook_user_x,dc=subdomain,dc=dyndns,dc=org' -H ldap://subdomain.dyndns.org -D 'uid=user_x,ou=users,dc=subdomain,dc=dyndns,dc=org' -W
```Hope that what you are looking for.
Cheers,
borobudur

PS: Encrypted connection would also be smart!

---

