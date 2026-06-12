---
title: "Printer in VMWare install of 8.10 Intrepid"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by jimbofoxman on 2008-11-30
I have been testing Ubuntu 8.10 on VMWare.  Dual Boot is too much work when I want to switch between systems to go back to my gaming, Lightroom, etc.  Plus it allows me to get familiar with Ubuntu/Linux.

I have a USB printer, Canon ip4500.  Should I be able to see it in Ubuntu on VMWare?  I am just having a bear of a time trying to get it setup.

---

### Post by lemming465 on 2008-12-01
I think to see the printer in a vmware windows guest OS you'll need to disable the Vmware file sharing and turn on Samba with printer queues. The /etc/samba/smb.conf doesn't need a lot of stuff; mine (which is used for LAN printer sharing) has```

[global]
	workgroup = LEINWEBER
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

---

