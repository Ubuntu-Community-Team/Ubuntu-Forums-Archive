---
title: "LDAP server authentication grievance"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by Hainje on 2007-12-12
Hello everyone,

I'm desperately trying to get 7.10 Gutsy to do LDAP authentication. (I'm only at it for 6 months now ;-) )
My current setup has an UBUNTU 6.06.1 LTS server and an UBUNTU 7.04 client.
This works OK.
An LDAP user can
-log onto client console/desktop
-log onto server console
-remotely log onto server using SSH

I now have managed to get an Ubuntu 7.04 client to authenticate to a 7.10 server
but the server does not recognise LDAP users

Everything on the server seems fine. I can do ldapsearch -x and get valid results.
I can edit LDAP database using PHPldapAdmin.
The 7.04 client has no trouble authenticating to the 7.10 server

if I change /etc/nsswitch.conf on either the 7.10 server or a 7.10 client :

passwd    files ldap
group      files ldap
shadow   files ldap

the bootup process hangs at "starting kernel log".
on the 7.10 client, the KDE GUI (kdm) does not start.
on the 7.10 server i _know_ openldap (/etc/init.d/slad) hasn't been started because that happens later than klogd starting

Usually I do get a login prompt on the 7.10 systems. This does accept input for username and password, but then retuns a 'login timed out after 60 seconds.'.

All I can do then is reboot using CD and use 'repair broken system' to change nsswitch.conf back to:

passwd    compat
group      compat
shadow   compat

Then, the 7.10 machines will boot normally, but LDAP users will not be recognised (of course).

on the server I have nss and pam looking for:

host 127.0.0.1

on the client:

host 192.168.157.20 (which is server IP)


I do wait starting clietn machine until server is up and running

Regards,
Marout Borms
Amsterdam

---

### Post by davidleelambert on 2007-12-18
I'm not sure if I have the same problem.  I'm trying to get some Ubuntu F and G servers to pull user and group information from OpenLDAP 2.1.30 running on Gentoo.  We've had a cluster of other Gentoo and RedHat boxes authenticating against this LDAP server successfully for a long time, and we even have an Ubuntu D server that does so. 

I've tried a lot of different settings in /etc/ldap.conf and /etc/ldap/ldap.conf.  I've tried some settings in /etc/libnss-ldap.conf.  Nothing works.

One clue is that the command-line tools from ldap-utils do not work unless I specify the "-x" option.  They give the error-message "ldap_sasl_interactive_bind_s: No such attribute (16)".  

Another clue is that, on one box, I can see that the computer is doing something, because it takes about a second to return no result from "getent passwd _uid_" when LDAP lookup is enabled in /etc/nsswitch.conf and much less time otherwise.  

Finally,  all the working machines have the line:

```
pam_password crypt

```

in /etc/ldap.conf;  but adding that doesn't fix anything on these machines.

Any ideas?

---

### Post by iiibill on 2008-01-09
I had originally installed gutsy on two boxes last October.  I had pam_ldap and nss_ldap working just fine. Then last week I did what I thought would be a simple aptitude upgrade and all hell broke loose.  The pam_ldap.conf file and libnss_ldap.conf file were merged into the ldap.conf file.  I just hand edited the new file to make sure it was okay.  When I rebooted the system it would not run any init.d scripts after the kernel logs.  It took me forever to figure out that the problem was that I needed to specify an ldap host that was _not_ the local system.  It looks like the startup the startup has been modified to wait for the ldap service before it runs the init.d scripts.  Of course, one of my init.d scripts starts openldap.  Until I figure out the correct way to do this I have change /etc/ldap.conf to have a host specification of:

host 127.0.0.1 205.90.146.12

The system boots correctly now.

Of course, this is not the correct solution.  It does not address the problem of having only one server that runs a local openldap and you want to use pam/nss ldap on.

Not sure if yours is the same problem, but you had the same login time out symptom that I was seeing.

Bill

---

