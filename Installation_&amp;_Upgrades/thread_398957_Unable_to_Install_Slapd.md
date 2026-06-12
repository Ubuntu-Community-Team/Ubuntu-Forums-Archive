---
title: "Unable to Install Slapd"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by Novaoblivion on 2007-04-01
We have a small home office and have been using Ubuntu for our servers for a while and it works great :). We currently have a samba domain controller in place mainly so I have a central location to administrate everything from, when we get new employees or fire olds ones its easy for me to make/remove user accounts for them. We are now going to add some Mac OS X machines to our office and from what I have gathered I need to have an LDAP server in order to add the OS X machines to the domain. 

I have been trying to experiment with setting up ldap in a VMWare virtual machine so I can correct any problems I need to before I go to actually re-setup our server. Unfortunately I cant even get slapd to install. 

When trying to install slapd using either sudo apt-get or sudo aptitude I get this toward the end of the installation:

> 
E: Sub-procces /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up slapd (2.2.26-5ubuntu3.1) ...
 Creating initial slapd configuration... done.
 Creating initial LDAP directory... slapdd: Bad configuration file!
Faild to slapdd the data:
dn: dc=hsd1,dc=nm,dc=comcast,dc=net,dc=
objectClass: top
objectClass: dcObject
objectClass: organization
o: hsd1.nm.comcast.net.
dc: hsd1

dn=admin,dc=hsd1,dc=nm,dc=comcast,dc=net,dc=
objectClass: simpleSecurityObject
objectClass: orginizationalRole
cn: admin
description: LDAP administrator
userPassword: {crypt}EmkCkMO0o51BI
dpkg: error proccesing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing: 
 slapd


I am not sure where it is getting the dc=hsd1,dc=nm,dc=comcast,dc=net,dc= stuff from. We use comcast as our ISP but when it asked me the questions during setup I told it dc=tallgrassinc,dc=com (our company domain name). Any ideas on how to get it working? VMWare is running on a Vista machine if that helps any, I have also tried it in Parallels on a Mac but it did the same thing. I am using the Ubuntu 6.10 Server ISO to install. Thanks!!

(If this is the wrong place for this thread please move it! Thanks!)


For anyone who has this problem I found the solution! edit the /etc/hosts files and change the line that in my case said:

testserver.hsd1.nm.comcast.net. to yourserver.yourdomain.com and it will work :D.

---

