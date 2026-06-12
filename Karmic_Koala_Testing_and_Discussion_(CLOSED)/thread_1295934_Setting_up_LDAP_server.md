---
title: "Setting up LDAP server"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xingmu on 2009-10-20
I am trying to set up a OpenLDAP server for the first time with Karmic Koala.  I am using the instructions at [https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html) and got stuck on step 2: "sudo dpkg-reconfigure slapd".

According to the docs, I should be prompted for a domain name and password when configuring the package.  But there is no such prompt.  I read on some dev list that Karmic Koala's slapd package no longer sets up a frontend database (forgot link, sorry).  The problem is I can't figure out how in the world to set up a database myself.  Most tools I have found like phpldapadmin or ldaptor-waebui assume that I have already created a database.

After reading docs on OpenLDAP, I tried to use the slapadd command and some config text from the man page:
```

dn: olcDatabase=bdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcBdbConfig
olcDatabase: bdb
olcSuffix: "dc=home,dc=local"
# The database directory MUST exist prior to
# running slapd AND should only be accessible
# by the slapd/tools. Mode 0700 recommended.
olcDbDirectory: /var/lib/ldap
# Indices to maintain
olcDbIndex:     objectClass  eq
olcDbIndex:     cn,sn,mail   pres,eq,approx,sub

```

This doesn't work and end with an error:
```

str2entry: invalid value for attributeType objectClass #1 (syntax 1.3.6.1.4.1.1466.115.121.1.38)
slapadd: could not parse entry (line=1)

```

I am at a lost of what to do here!  How are we expected to create a LDAP directory in Karmic??

---

### Post by xingmu on 2009-10-20
Ok, I found more info on the changes to ldap/slapd in Karmic at [https://lists.ubuntu.com/archives/ubuntu-server/2009-August/003179.html](https://lists.ubuntu.com/archives/ubuntu-server/2009-August/003179.html)

So I tried to follow the advice from the link above and ran ldapadd with the special args:

```

$ sudo ldapadd -Y EXTERNAL -H ldapi:/// -f home.ldif 
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "dc=home,dc=local"
ldap_add: Server is unwilling to perform (53)
	additional info: no global superior knowledge

```

Still wondering how to get this thing working?  Also wondering why the maintainer thought that *not* setting up a frontend database is a good thing?

The file I was trying to init data with is a sample file copied from [http://www.zytrax.com/books/ldap/ch8/#format-sample:](http://www.zytrax.com/books/ldap/ch8/#format-sample:)

```

## DEFINE DIT ROOT/BASE/SUFFIX ####
## uses RFC 2377 format
## replace example and com as necessary below
## or for experimentation leave as is

## dcObject is an AUXILLIARY objectclass and MUST
## have a STRUCTURAL objectclass (organization in this case)
# this is an ENTRY sequence and is preceded by a BLANK line

dn: dc=example,dc=com
dc: example
description: My wonderful company as much text as you want to place 
 in this line up to 32K continuation data for the line above must 
 have <CR> or <CR><LF> i.e. ENTER works 
 on both Windows and *nix system - new line MUST begin with ONE SPACE
objectClass: dcObject
objectClass: organization
o: Example, Inc.

## FIRST Level hierarchy - people 
## uses mixed upper and lower case for objectclass
# this is an ENTRY sequence and is preceded by a BLANK line

dn: ou=people, dc=example,dc=com
ou: people
description: All people in organisation
objectclass: organizationalunit

## SECOND Level hierarchy
## ADD a single entry under FIRST (people) level
# this is an ENTRY sequence and is preceded by a BLANK line
# the ou: Human Resources is the department name

dn: cn=Robert Smith,ou=people,dc=example,dc=com
objectclass: inetOrgPerson
cn: Robert Smith
cn: Robert J Smith
cn: bob  smith
sn: smith
uid: rjsmith
userpassword: rJsmitH
carlicense: HISCAR 123
homephone: 555-111-2222
mail: r.smith@example.com
mail: rsmith@example.com
mail: bob.smith@example.com
description: swell guy
ou: Human Resources

```

---

### Post by xingmu on 2009-10-20
So according to the URLs in the previous message, Karmic is trying to put the burden of building a database on other packages instead of slapd.  So I tried to install yet another ldap administration tool: phamm-ldap.

It prompts me to create an empty LDAP base for Phamm and I say yes.  I give it my domain and then proceed to set passwords (one for admin, one for limited privileges user).  But the dpkg configuration fails miserably with the following messages:

```

Setting up phamm-ldap (0.5.15-1) ...
ldap_bind: Invalid credentials (49)
dpkg: error processing phamm-ldap (--configure):
 subprocess installed post-installation script returned error exit status 49
Errors were encountered while processing:
 phamm-ldap
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems that the phamm package isn't using the special method for connecting to the LDAP server (-Y EXTERNAL...).  So I guess that is another broken package for LDAP.

It seems that this recent major revision to LDAP in Karmic has no documentation for developers or users??  Still hoping someone with LDAP experience could point me in the right direction.

---

### Post by xingmu on 2009-10-23
I have found the latest docs for Karmic at [http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html](http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html) and the instructions for setting up OpenLDAP are out-dated.  So I have filed a bug against ubuntu-docs at [https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/459403](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/459403)

Meanwhile, if anyone knows how to successfully create a directory database in OpenLDAP using ldapadd, please do post here.

---

### Post by xingmu on 2009-10-23
Just found a wishlist bug filed by another user against openldap at [https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/442498](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/442498).

---

### Post by xingmu on 2009-10-25
Got support from #ldap (thanks to hyc) on this issue and happy to say things are working now.

The problem with my first attempt was that the back_bdb module had not been loaded so I couldn't add a bdb database (if you want to use hdb then you need back_hdb).  In all my reading about OpenLDAP I never saw anything about loading modules.  I'm guessing other people would get stuck by the same problem.  So here's a step-by-step guide to getting a basic directory up and running.  This reflects my current understanding of LDAP (only learned in a few days), so there may be some inaccuracies.  Please feel free to point them out.

**Step 1**

Run the following command to add all the LDAP schemas in the slapd package to your cn=config (by default only core is added):

```

ls /etc/ldap/schema/*.ldif | xargs -I {} sudo ldapadd -Y EXTERNAL -H ldapi:/// -f {}

```

**Step 2**

Create a file called db.ldif with the following contents.  This will setup a database for a domain dc=home,dc=local (aka home.local).  Also, only the cn=admin,dc=hoome,dc=local can manage this database (pass:admin). 

```

# Load modules for database type
dn: cn=module,cn=config
objectclass: olcModuleList
cn: module
olcModuleLoad: back_bdb.la

# Create directory database
dn: olcDatabase=bdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcBdbConfig
olcDatabase: bdb
# Domain name (e.g. home.local)
olcSuffix: dc=home,dc=local
# Location on system where database is stored
olcDbDirectory: /var/lib/ldap
# Manager of the database
olcRootDN: cn=admin,dc=home,dc=local
olcRootPW: admin
# Indices in database to speed up searches
olcDbIndex: uid pres,eq
olcDbIndex: cn,sn,mail pres,eq,approx,sub
olcDbIndex: objectClass eq
# Allow users to change their own password
# Allow anonymous to authenciate against the password
# Allow admin to change anyone's password
olcAccess: to attrs=userPassword
  by self write
  by anonymous auth
  by dn.base="cn=admin,dc=home,dc=local" write
  by * none
# Allow users to change their own record
# Allow anyone to read directory
olcAccess: to *
  by self write
  by dn.base="cn=admin,dc=home,dc=local" write
  by * read

```

Run the following command on the file above to add the database to the LDAP server.  Note that Karmic uses the EXTERNAL SASL binding to communicate with the LDAP server.  There is no admin user or password here:

```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f db.ldif
```

**Step 3**

Create another file for all the people you want to add, we'll call it people.ldif

```

# Create top-level object in domain
dn: dc=home,dc=local
objectClass: top
objectClass: dcObject
objectclass: organization
o: home.local
dc: home
description: Home network 

dn: ou=people,dc=home,dc=local
objectClass: organizationalUnit
ou: people

dn: ou=groups,dc=home,dc=local
objectClass: organizationalUnit
ou: groups

dn: uid=john,ou=people,dc=home,dc=local
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: john
sn: Doe
givenName: John
cn: John Doe
displayName: John Doe
uidNumber: 1000
gidNumber: 10000
userPassword: password
gecos: John Doe
loginShell: /bin/bash
homeDirectory: /home/john
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: john.doe@example.com
postalCode: 31000
l: Toulouse
o: Example
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: System Administrator
postalAddress: 
initials: JD

dn: cn=example,ou=groups,dc=home,dc=local
objectClass: posixGroup
cn: example
gidNumber: 10000

```

Since we have created our own access control lists for the dc=home,dc=local database, we must change the binding method (i.e. auth with the admin user and password).  Add the data for the directory via the following command:

```

sudo ldapadd -x -D cn=admin,dc=home,dc=local -w admin -f people.ldif

```

**Step 4**

From a client, you can now check to see if you can read the database:

```

ldapsearch -x -H ldap://dustball.home.local -b dc=home,dc=local

```


**Troubleshooting**

[I]ldap_add: Other (e.g., implementation specific) error (80)
	additional info: <olcModuleLoad> handler exited with 1[/I]

You are trying to load the same module twice, e.g. you already ran ldapadd on db.ldif once and now you're doing it again.

[I]ldap_add: Invalid syntax (21)
	additional info: olcSuffix: value #0 invalid per syntax[/I]

You have quotes around the olcSuffice value, e.g. olcSuffix: "dn=home,dn=local".  Despite what you see in the docs, quotes aren't needed or wanted.

[I]ldap_add: Server is unwilling to perform (53)
	additional info: no global superior knowledge[/I]

You are trying to add something to a domain that doesn't exist, e.g. you are trying to add John Doe to dn=home,dn=local but dn=home,dn=local hasn't been created yet.

---

### Post by eti.que on 2009-10-25
Hi,

Thanks for sharing ! I have a slightly different problem.

I have database files existing (from my previous installation) and I am not sure on how to reimport them.

Should I just skip the step 3 above ?

---

### Post by isrich on 2009-10-26
Thank you! xingmu

I'd spent all my weekend looking for this howto.

---

### Post by xingmu on 2009-10-26
eti.que,

I think you have to check how your previous database handled access control.  If you have a admin with a password like this howto does, then you could simply use your own LDIF file from your old database in Step 3.  Also, make sure that you update the dc=home,dc=local values in Step 2 to your own domain.

---

### Post by bmarius on 2009-10-26
Thanks a lot for this. I've been banging my head against a wall the last couple of days trying to figure this out :)

---

### Post by tarekeldeeb on 2009-10-28
I have the same (or close) problem,
I was not asked for a password during the installation.

When I follow your steps .. all fail.

Step-1:

```
ls: cannot access /etc/ldap/schema/*.ldif: No such file or directory
```
I have no files in there !!

Step-2:

```
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
	additional info: <olcModuleLoad> handler exited with 1

```
I donno what's wrong with me !

Step-3:

has no meaning with the previous errors.

Can you help me please?

---

### Post by xingmu on 2009-10-28
tarekeldeeb,

For your first error, are you running Ubuntu 9.10 (Karmic Koala)?  Are you sure that you successfully installed the packakges?  Try running the following command to (re)install and then try Step 1 again:

```

sudo apt-get install slapd ldap-utils

```

Your second error is already covered in the Troubleshooting section:

> 
ldap_add: Other (e.g., implementation specific) error (80)
additional info: <olcModuleLoad> handler exited with 1

You are trying to load the same module twice, e.g. you already ran ldapadd on db.ldif once and now you're doing it again.


---

### Post by tarekeldeeb on 2009-10-28
> **xingmu said:**
> tarekeldeeb,

For your first error, are you running Ubuntu 9.10 (Karmic Koala)?  Are you sure that you successfully installed the packakges?  Try running the following command to (re)install and then try Step 1 again:


I'm on Karmic, and Yes the packages are well installed. 

I'm totally lost ..

---

### Post by xingmu on 2009-10-28
tarekeldeeb,

I believe something is wrong with your package, the list of files clearly includes the schma ldifs (see [http://packages.ubuntu.com/en/karmic/i386/slapd/filelist](http://packages.ubuntu.com/en/karmic/i386/slapd/filelist)).  You may try purge the packaging and reinstalling:

```

sudo apt-get purge slapd ldap-utils
sudo apt-get install slapd ldap-utils

```

You may also try using ```
sudo ls /etc/ldap/schema/*.ldif
``` in case you have something changed the permissions of your /etc directory.

---

### Post by tarekeldeeb on 2009-10-29
> **xingmu said:**
> tarekeldeeb,

I believe something is wrong with your package, the list of files clearly includes the schma ldifs (see [http://packages.ubuntu.com/en/karmic/i386/slapd/filelist](http://packages.ubuntu.com/en/karmic/i386/slapd/filelist)).  You may try purge the packaging and reinstalling:

```

sudo apt-get purge slapd ldap-utils
sudo apt-get install slapd ldap-utils

```

You may also try using ```
sudo ls /etc/ldap/schema/*.ldif
``` in case you have something changed the permissions of your /etc directory.

oops .. I have a problem installing slapd:

```
Setting up slapd (2.4.18-0ubuntu1) ...
  Backing up /etc/ldap/slapd.d/ in /var/backups/slapd-2.4.18-0ubuntu1... done.
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to 
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -h 'ldap:/// ldapi:///' -g openldap -u openldap -F /etc/ldap/slapd.d/ 
invoke-rc.d: initscript slapd, action "start" failed.
dpkg: error processing slapd (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ldap-utils (2.4.18-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

it installs fine using aptitude !
but aptitude seems to be doing a nasty job .. 

Can you give me a clue ?

---

### Post by xingmu on 2009-10-29
There are several clues for you already in the error messages.  You should follow those instructions first and see what you can figure out.  I have seen bugs on upgrading slapd on Launchpad ([https://bugs.launchpad.net/ubuntu/+source/openldap](https://bugs.launchpad.net/ubuntu/+source/openldap)).  You may check if their problems are similar.  And if you are still stuck after following the instructions in the error message, perhaps you need to file a bug.

---

