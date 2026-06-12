---
title: "SLAPD not configuring"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by _ragman_ on 2010-09-15
Hi all,
I've been trying to install slapd and ldap-utils according to various tutorials.  They all say that the installation should launch a configuration wizard asking for the likes of ldap root password ... The install configuration simply fails to launch.

I've tried 'sudo dpkg-reconfigure slapd' and the first question is:
---
If you enable this option, no initial configuration or database will be created for you.   
 Omit OpenLDAP server configuration? 
 <Yes>                       <No>
---

selecting <No> takes me to:

---Do you want the database to be removed when slapd is purged?

Then a third lengthy question about LDAPv2 protocol.

After the three questions it dumps back to the prompt without configuring the LDAP database.

I've tried a puge and reinstall of slapd, ldap-utils and the odbc packages it said were no longer in use.

BTW I'm running Karmic.

Cheers
ragman

---

### Post by _ragman_ on 2010-09-15
found it:

[http://ubuntuforums.org/showthread.php?t=1295934](http://ubuntuforums.org/showthread.php?t=1295934)

---

### Post by jcoles on 2010-09-26
I followed the directions that you linked to, and they helped up to a point. But, when I tried to add the people.ldif info, I got an error message:

ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

Any ideas what this means?

I didn't find any answer about the password. What did you conclude? When I followed the instructions, no password was requested. 

LDAP is terribly confusing and nearly everything written about it is up-in-the-clouds abstract. Actual step-by-step instructions are hard to find. Thanks for the link.

---

### Post by _ragman_ on 2010-09-27
I actually gave up on 9.10 given that the work arounds were so involved and upgraded to 10.04 in the hope it would be fixed.  It wasn't, so I persisted with the manual configurations but didn't get it fully functional. Given that it was a fresh build anyway, my final outcome was to trash the lot and install 9.04 under which the SLAPD configuration works as expected.

I'm feeling your pain in trying to get your head around LDAP. I've found the learning curve near vertical and have really struggled to get a foothold.  But now I've got my leg off the ground I've been having trouble with secure links to manage the LDAP now and have been working up SSL and the CA.  Not there yet as I've been away the past week.

cheers,
ragman

---

