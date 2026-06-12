---
title: "Why Samba does not recognize my (only) password on the system?"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by ButchMel on 2013-10-07
I am unable to edit the smb.conf so to get my connexions working between computers/systems (Ubuntu 12.04.3 LTS)  - newly installed (not upgraded).

No matter if I try the Samba GUI or go through a terminal : the admin passord (and teh sole password on this system) is not recognized !...

Is there a solution to this, else than flushing and reinstalling everything from scratch ?  Anything (command) I could o to print a result and take it here for correct interpretation?

Thanks

B

---

### Post by steeldriver on 2013-10-07
what terminal command are you using exactly, and what version of Ubuntu?

---

### Post by ButchMel on 2013-10-07
I am on Ubuntu 12.04.3 (installed Server edition then added the GUI after). 

The command I am trying:

gksu gedit /etc/samba/smb.conf

Or, I go to Dash Home and click on SAMBA - either way, I am faced with same bug: password is not recognized.

Thanks for your time.

B.

---

### Post by ButchMel on 2013-10-08
Can''t access any of the 5 drives (and cannot see them from a Mac PC - just see name of the Ubuntu machine) - cannot enter (password refused):

Those are results of parmtest -w:

robert@CrabConnect:~$ testparm -w
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

---

### Post by steeldriver on 2013-10-09
if you're still having problems with 'gksu gedit' then run

```
gksu-properties
```

and make sure the mode is set to 'sudo' not 'su'

---

### Post by ButchMel on 2013-10-09
> **steeldriver said:**
> if you're still having problems with 'gksu gedit' then run

```
gksu-properties
```

and make sure the mode is set to 'sudo' not 'su'

Wow... Yep that was the case exactely ! mode was set to 'su' ... Now that I have changed it, I can enter and edit... Many thanks for this steeldriver !

However, still need to figure out why I'm not getting the 5 drives there (even though they are all mounted and all NTFS)

Now a new issue when trying to access from the Mac machine (Mac OS X 10.8.5) :

''The version of the server you are trying to connect to is not supported. Please contact your system administrator to resolve the problem.''

Then if I try to connect as Guest:

''Check the server name or IP address, and then try again. If you continue to have problems, contact your system administrator''

What the hell is that ??

---

