---
title: "Samba Member Server error"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by xsystemx on 2008-03-18
Configured samba to be a member server. I am planning on making a small SAN.
When I run sudo testparm I get the following error:

Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
**WARNING: No path in service printers - making it unavailable!**
NOTE: Service printers is flagged unavailable.
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER


Here is a copy of my smb.conf "changed domain name just for posting"

#Global parameters
[global]
workgroup = EXAMPLE
realm = EXAMPLE.UBUNTU.FAKE
preferred master = no
server string = Samba file and print server
security = ADS
encrypt passwords = yes
log level = 3
log file = /var/log/samba/%m
max log size = 50
#winbind separator = +
printcap name = cups
printing = cups
idmap uid = 10000-20000
idmap gid = 10000-20000

[homes]
comment = Home Directories
valid users = %S
read only = No
browseable = No

[printers]
comment = All Printers
browseable = no
printable = yes
guest ok = yes

HELP!

---

