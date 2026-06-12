---
title: "Karmic - Samba Shares not working"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by psycho5 on 2009-10-23
Hi guys,

I upgraded to Karmic; I would like to know if anyone had this problem. I can't access any PCs on my home network anymore. They can't see my shares either. 

There are two machines, one XP and one Windows 7. Both can see each other and access their shares. I know my PC is the odd one out.

Can someone tell me why this is not working anymore?

```

oj@oj-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Videos]"
Processing section "[Music2]"
Processing section "[Music]"
Processing section "[Videos]"
Processing section "[Iso]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Videos]
	comment = Videos
	path = /media/Media/oj/UbuntuStuff/Videos
	guest ok = Yes

[Music2]
	comment = Music
	path = /media/Storage 2/Dale Music
	guest ok = Yes

[Music]
	comment = Music
	path = /media/Media/oj/UbuntuStuff/Music
	guest ok = Yes

[Iso]
	comment = Disc Images
	path = /media/Storage 2/Iso
	guest ok = Yes
oj@oj-desktop:~$ 


```

```

oj@oj-desktop:~$ smbclient -L OJ-DESKTOP
Enter oj's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	Videos          Disk      
	Music2          Disk      Music
	Music           Disk      
	Iso             Disk      Disc Images
	IPC$            IPC       IPC Service (oj-desktop server (Samba, Ubuntu))
	hpdeskjet       Printer   HP deskjet
	dale music      Disk      
	videos_2        Disk      
	public          Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

	Server               Comment
	---------            -------
	OJ-DESKTOP           oj-desktop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            OJ-DESKTOP
oj@oj-desktop:~$ 


```

tried to see if samba is working correctly, in which case this command should return my IP address but it does not.

```

oj@oj-desktop:~$ nmblookup -B 192.168.0.3 _SAMBA_
querying _SAMBA_ on 192.168.0.3
name_query failed to find name _SAMBA_
oj@oj-desktop:~$ 

```

Which means to me that my machine is not communicating through the samba (ports?) I have no idea.. I know I can ping both the Windows machines. 

Btw, I was virtualizing with OpenSuse and I just tried using samba to access the shares from virtualbox and it worked, so I know something's wrong here. Can anyone tell me what I should do next?

---

### Post by dmizer on 2009-10-23
Have a look at the 6th link in my sig :)

---

