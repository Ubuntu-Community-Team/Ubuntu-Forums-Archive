---
title: "Samba Problems (NT_STATUS_ACCESS_DENIED)"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Thomas_Matthew on 2011-03-04
Hello, I'm a student building a Domain Controller for my school as a small project. Using Ubuntu 10.04 with Samba.
 
The problem I am having is that when I input:
 
**net rpc rights grant "studentdomainjpiihs\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege \SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege** 
 
It says:
 
**Failed to grant privleges for studentdomainjpiihs\Domain Admins (NT_STATUS_ACCESS_DENIED)**
 
I'm using the documentation from here: [https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html)
 
If someone could help, it would be really appreciated, Thanks!

---

### Post by Avanesov on 2011-04-20
I had this same issue and found my answer here:

[http://www.mail-archive.com/samba@lists.samba.org/msg96263.html](http://www.mail-archive.com/samba@lists.samba.org/msg96263.html)

sudo net rpc rights grant "domainname\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege [COLOR="Red"]-U user-in-the-admin-group[/COLOR]

---

