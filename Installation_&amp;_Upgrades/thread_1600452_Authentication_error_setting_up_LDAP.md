---
title: "Authentication error setting up LDAP"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by natomb on 2010-10-19
Hello,

I am quite new to Linux. Currently, I try to install Ubuntu 10.04 Server version. I have decided to install a minimal version without any previous package selection.

For installation I follow the server guide quite strictly.

When I want to install and configure LDAP I get an authentication error (```
ldap_bind: Invalid Credentials (49)
```) . I get this error when changing the configuration examples from the server guide to my values (see attached backend and frontend files).

I can "ldapadd" the backend file without problem. But when I try to "ldapadd" the frontend file or doing ldapsearch I always get the authentication error.

Using the examples from the server guide "word by word", everything works fine.

Could someone please hint me where my backend or frontend file is flawed (probably the line feed is invalid in this post due to Windows, but on the Linux box the line feed is / was corrected)?

Thank you very much
  Bjoern

---

### Post by martynbristow on 2010-10-19
Hello

I'm no Ubuntu Newbie or expert but some further details.

How did you get to this stage.
What instructions have you followed.
The exact link, i know you have put server guide but i have found several different editions

I have the same issue btw with 10.10 and cannot get it to authenticate

---

### Post by natomb on 2010-10-20
Hi there,
 
 
just want to present my analysis results.
 
First, I had a bad ACL directive
 
```
[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]olcAccess: to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=li-wuest,dc=name" write by anonymous auth by self[/SIZE][/FONT][/SIZE][/FONT]
```
 
should be
 
```
[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]olcAccess: to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=li-wuest,dc=name" write by anonymous auth by self write by * read[/SIZE][/FONT][/SIZE][/FONT]
```
 
Second, I had to add some newlines between the different ```
dn:
``` blocks. I did not know that LDAP is so particular about file format.
 
Third, I configured my own path for the LDAP database. As a matter of fact, I had to loosen up AppArmor by issuing
 
```
aa-complain /usr/sbin/slapd
```
 
After ldapadd-ing the backend and frontend, I could execute aa-logprof and aa-enforce to restrengthen AppArmor.
 
Consequently, with those three changes (proper olcAccess directive, some pretty file formatting and AppArmor profile updating) I could get my LDAP working.
 
Next steps are TLS security and using LDAP for user authentication. Thus, stay tuned for some new of my problems :)
 
@Admin: this thread can be closed then.

---

