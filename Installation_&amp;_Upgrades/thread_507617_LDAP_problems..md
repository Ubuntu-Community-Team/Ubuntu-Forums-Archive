---
title: "LDAP problems."
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by Peque on 2007-07-23
Hey Forum. 

As I needed the install a LDAP Server for authentication at my work - I thought off Ubuntu /LDAP and use the guide found at : [https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28LDAP%29](https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28LDAP%29)

BUT - after doing half the guide - and actually did confirm that the LDAP was workling - I was doing Migrating Data part - and after adding the different parts from /tmp*.ldif I choose to reboot my machine - And know I can see that most users suchs as root,syslogd,klogd etc are not known for the system ??? How could that be and what did I do wrong?? 
Caurse I cannot login - It will not start my services (Like apache,bind mm) and I cannot login to the machine at any point - even though I tried to rescue the things from a live CD - But as soon as I'm going back to harddisk - the users aren't known for the system ??? 

So what should I do from here ???

---

### Post by cropr on 2007-10-22
I just  installed gutsy and have a very similar problem , which I did not have on feisty.
When I change passwd group and shadow fields in the nsswitch.conf file to "files  ldap", the system works perfect with my ldap setup ("getent passwd" gives the correct result) .  But after a reboot the systems hangs when starting klogd.
Booting via the recovery and changing the passwd group and shadow fields to "files" give me a bootable system (of cours"e withotu the ldap users)
This seems to be a bug

---

### Post by Ubuntu Warrior on 2007-10-22
Exact same problem with our installs. LDAP seems to work just after doing all the laborious config work but hangs after a reboot.

Hope someone can resolve this ASAP as we need to get Gutsy rolled out to workstations that are not supported all that well in Feisty eg. Dell Optiplex 740 with screen driver issues.

---

### Post by joker-eph on 2007-10-23
Duplicate with : [http://ubuntuforums.org/showthread.php?p=3598637](http://ubuntuforums.org/showthread.php?p=3598637)

---

