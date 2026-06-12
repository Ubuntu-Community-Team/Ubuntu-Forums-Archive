---
title: "LDAP Installation and Configure"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by VaineDragon on 2010-02-28
I did indeed install LDAP, using **sudo apt-get install slapd ldap-utils** my issue is that when I try to use **sudo dpkg-reconfigure slapd** I'm unable to get the base configuration to work. 

I'm always asked "If you enable this option, no initial configuration or database will be created for you "                                     

Omit OpenLDAP server configuration?                                                   
<Yes>                             <No>                           
                                                                                                  
Either answer does not allow me to configure mt LDAP server for base settings?How do I remove and start over from the get go?
I have tried sudo apt-get purge slapd ldap-utils and sudo apt-get remove slapd ldap-utils

And then sudo apt-get install slapd ldap-utils, but once again no base configuration.


I'm lost here, since this the first time for me with LDAP?

---

### Post by briandu on 2010-02-28
The maintainer has changes the code so it will not work. 

The tutorials in the forum do not work - well so far I have spent a lot of time on this.

---

### Post by VaineDragon on 2010-02-28
So what do you suggest at this point?

---

### Post by briandu on 2010-02-28
I compiled and install berkley db. Done

When I took openladp latest version to compile and build - it wants links to the DBD.h files.

When I put the environment link in it still does not. BUT maybe my C flags are wrong?

I used:

env CPPFLAGS=-I/home/briand/Desktop/db-4.8.26/build_brew LDFLAGS=-L/home/briand/Desktop/db-4.8.26/build_brew ./configure


Maybe I have this all wrong? as the configure fails

---

### Post by briandu on 2010-02-28
I get this :

configure: error: BDB/HDB: BerkeleyDB not available

but the file dbd.h is in the path.

Maybe I do not know what I am doing here?

Anybody HELP?

---

### Post by VaineDragon on 2010-02-28
You know way more that I do at this point.

---

### Post by briandu on 2010-02-28
I think this is working - well partially anyway: it is a start for me.

[http://www.howtoforge.com/install-and-configure-openldap-on-ubuntu-karmic-koala](http://www.howtoforge.com/install-and-configure-openldap-on-ubuntu-karmic-koala)

note there are several place where it has dc-"exampl........com" - disregard the " " as they are not required.

---

### Post by briandu on 2010-02-28
I think it is now working. Just be careful of the " " all over the place.

and NB it is sudo for the command lines

Now to add users.

Good luck

---

