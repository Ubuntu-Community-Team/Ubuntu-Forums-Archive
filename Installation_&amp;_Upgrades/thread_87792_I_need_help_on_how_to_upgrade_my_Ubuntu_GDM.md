---
title: "I need help on how to upgrade my Ubuntu GDM"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by unixnorks on 2005-11-08
hi to all...

First of all, Im a linux newby residing in Philippines...  And Ubuntu is the only overwhelming OS that convince me to use it... However, i want to make some modification on its login authentication... Why should i need to modify it? ...<that's a good question>...Well, basically me and my teammates programmer dreaming to spread out the use of Ubuntu here in Philippines and we proposed some schools the benefit of using Ubuntu, but the school asked us to create CUSTOMIZED LOGIN for students before they will going to accept any among our proposals...

Here's what they want to happen... The school has a student database that monitor every single records of the student, including username, password, remaining credits etc... Now, the system administrator relies on their database (from their old system, window-based program) as to be authenticated when they log-on to their account... So I must know how I can modify the source of login authentication or what so ever name to call it from the login screen provided by GDM login... 

But the problem is i dont even know how it really able to authenticate system users... Well, i expect some guys reading this letter are now calling me IDIOT...lol...  I've been reading more than 2 weeks already about the development of this software and I found out (if theory is right) that if I can modify the SOURCE of verify-shadow.c inside in GDM package my whole task will be accomplished before the end of this month.  Well, the since the source is written in C i might have a chance to make a revision..

But here is the main and my greatest PROBLEM, i cant install my modified GDM. In other words, its all messed me up to find myself desperate on this project... Something is lacking... I dont know and only UBUNTU GURU could give me that idea...

the GDM that i downloaded from [http://ftp.acc.umu.se/pub/GNOME/sources/gdm/2.13/](http://ftp.acc.umu.se/pub/GNOME/sources/gdm/2.13/) is this version gdm-2.13.0.0 
I followed it INSTALLATION Instructions.... after I type 

$>./configure

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.28... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... [COLOR="Red"]configure: error: XML::Parser perl module is required for intltool[/COLOR]


and the error occured... I hope guys, with my long telling examples and explanation, i helped you to help me... Any respond from anyone is highly appreciated...


:)

---

### Post by michael_salcher on 2005-11-08
1) just looks like you haven't installed the XML Parse Perl module. look for it in synaptic and install it.

2) i think you're totally on the wrong track regarding this whole task. authentication has nothing to do with GDM or KDM or terminal login or whatever you are using. what you want is a server that knows all the users and many clients which let a user connect if the server authenticates them. that's a networking / sys admin issue. i REALLY don't think you need to modify GDM.

---

### Post by mlomker on 2005-11-08
> checking for XML::Parser... [COLOR="Red"]configure: error: XML::Parser perl module is required for intltool[/COLOR]


Install the libxml-parser-perl package using Synaptic.

---

### Post by majed on 2005-11-09
alternatevely, you can just export the school database to an LDAP directory and use it as  the database as well as for authentication :)

easy.. straightforward (i think!), free, open-source, and standard!

Good luck!

---

### Post by unixnorks on 2005-11-18
> alternatevely, you can just export the school database to an LDAP directory and use it as the database as well as for authentication 

Well, hard to admit but your suggestion sounds good!...lol.. Well, sir, do you mind if i will ask you more about configuring LDAP and can i ask a little guidance about its HOWTOs??  please ....;)

---

### Post by majed on 2005-11-18
hi .. glad u like the idea!

i'm not really an LDAP guru, rather a nerd user :) but from my humble experience, LDAP is not so somplicated, and there are many versions and much documentation and literature online..

you can start here: 
[http://ubuntuforums.org/showthread.php?t=10187]("http://ubuntuforums.org/showthread.php?t=10187")
[http://craige.mcwhirter.com.au/blog/archive/2005/01/17/making_a_debian_or_ubuntu_mach]("http://craige.mcwhirter.com.au/blog/archive/2005/01/17/making_a_debian_or_ubuntu_mach")

good luck!

---

### Post by unixnorks on 2005-11-20
Hey! thanks a lot!!:D

---

