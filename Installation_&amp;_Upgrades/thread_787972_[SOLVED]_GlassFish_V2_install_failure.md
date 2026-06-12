---
title: "[SOLVED] GlassFish V2 install failure"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by glowplug61 on 2008-05-09
Glassfish installation - can not create domain problem...

Ubuntu 8, fresh install then mysql5, netbeans 6.01, glassfish v2 - all from repository

8 rows of...
Using port xxxx for abcdef
...then

----------------------
Domain being created with profile:cluster, as specified by variable AS_ADMIN_PROFILE in configuration file.
Security Store uses: JKS
keytool error: java.io.IOException: Invalid keystore format

CLI130 Could not create domain, domain1
Could not create default domain domain1 at /var/lib/glassfishv2/domains.

Create required domains manually using asadmin2
---------------------------

I've tried using asadmin with path, password and passwordfile but still the same error.

Any help greatly appreciated

Regards,
Greg

---

### Post by glowplug61 on 2008-05-09
At the risk of being deemed impatient I need a solution ASAP.

I have spent almost all of my spare time over the last week trying to solve this and a few other problems on my own.

In a nutshell I developed my website [http://glowplug@bitasylum.net/](http://glowplug@bitasylum.net/) using Netbeans 6.01, to run on GlassFish V2 with MySQL 5.

I've tried a number of other distros for dev. environment however they don't touch Ubuntu in terms of meeting my overall needs.

Many thanks in advance,
Regards Greg (aka glowplug)

---

### Post by glowplug61 on 2008-05-10
Could somebody PLEASE PLEASE help me, this has cost me OVER A WEEK in DOWNTIME?

Maybe you can afford that but I can't (let alone all the downloading)!

I have done a number of fresh Ubuntu installs with combinations of Netbeans etc from repository or Sun bundle - before or after post Ubuntu install updates.

I have tried quite a number of command permutations from the "man asadmin" but I am very confused.
For example  - which passwordfile??

In the end everything produces the same error....

Security Store uses: JKS
keytool error: java.io.IOException: Invalid keystore format
 
CLI130 Could not create domain, domain1

....

Thanks in advance,
Greg (aka glowplug)

---

### Post by Partyboi2 on 2008-05-10
If you are using open JDK change to sun JDk
([http://forums.java.net/jive/message.jspa?messageID=271690](http://forums.java.net/jive/message.jspa?messageID=271690))

---

### Post by glowplug61 on 2008-05-10
> **Partyboi2 said:**
> If you are using open JDK change to sun JDk
([http://forums.java.net/jive/message.jspa?messageID=271690](http://forums.java.net/jive/message.jspa?messageID=271690))

This is the case, thank you for your help, much appreciated.

Regards,
Greg

---

### Post by Partyboi2 on 2008-05-10
happy to have helped :)

---

