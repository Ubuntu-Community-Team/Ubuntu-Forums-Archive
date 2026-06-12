---
title: "Active Directory and Ubuntu and ProFTPd"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by galaumiy on 2011-01-08
Hello,

I have a windows 2003 primary domaincontroller and a ubuntu machine.
I joined Ubuntu to the domain domein.net with the use of SAMBA and winbind. I can see all my users with wbinfo -u command, however when I try to configure proftpd, I cannot enter the usernames from my Active Directory, because it is not there. How to I configure proftpd so I can allow access to my users from ActiveDirectory?

Can anyone help me with this?

I searched google, people was talking about LDAP, but I don't know how to install and configure this?

My information:

domain: domein.net
samba ubuntu workgroup: domein
kerberos realm: domein.net

win2003 ip address: 192.168.1.2 / 24
win2003 computername: win2003
FQDN: win2003.domein.net

ubuntu ip address: 192.168.1.3 / 24
ubuntu computername: ubuntu
FQDN: ubuntu.domein.net

Please help me, I really looked for days and weeks for a solution !

---

### Post by davidmohammed on 2011-01-08
...

what issues have you encountered when you follow [this]("http://peterebbelink.wordpress.com/2009/02/28/authenticating-proftpd-to-windows-2003-ad/") guide?

---

### Post by galaumiy on 2011-01-18
> **davidmohammed said:**
> ...

what issues have you encountered when you follow [this]("http://peterebbelink.wordpress.com/2009/02/28/authenticating-proftpd-to-windows-2003-ad/") guide?

In order to use this guide, I need to bind my WIN2003 server with the Ubuntu machine with openLDAP.
But I have no idea where to start, after you send this message I tried different ways to install and configure the ubuntu (desktop) machine.
I am not familiar with ldap, but did try "something"
If I look into my /etc/ldap/ldap.conf I see the next:
[PHP]#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE	dc=example,dc=com
#URI	ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT	12
#TIMELIMIT	15
#DEREF		never[/PHP]

When I type ldapsearch into terminal I get:
[PHP]root@ubuntu:~# ldapsearch
SASL/DIGEST-MD5 authentication started
Please enter your password: 
ldap_sasl_interactive_bind_s: Invalid credentials (49)
	additional info: SASL(-13): user not found: no secret in database
[/PHP]

and with ldapsearch -x
[PHP]root@ubuntu:~# ldapsearch -x
# extended LDIF
#
# LDAPv3
# base <> (default) with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 32 No such object

# numResponses: 1
[/PHP]

---

### Post by galaumiy on 2011-01-18
Hello, please help me.

I think I fixed the bind thingy.
 
Also proftpd can find my username from active directory, but it shows up as Incorrect Password (503) error.
I tried a different user which does not exist, there it says the user is not existing, which is correct.

I changed the password, but I still get the same.. I think it has something to do with encrytion or with PAM configuration..

Please help me..

---

