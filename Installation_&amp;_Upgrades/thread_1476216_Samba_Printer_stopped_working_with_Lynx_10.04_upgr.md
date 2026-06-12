---
title: "Samba Printer stopped working with Lynx 10.04 upgrade"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by TrevorBradley on 2010-05-07
Hey everyone, been running Ubuntu on my server since 8.10, and have had my Samsung ML-1610 printer working great the whole time.  However, with the recent Lynx upgrade, I can no longer print from the Windows machines on my network.

The printer appears to work fine locally, is visible on an smbclient lookup, and even shows up on the other Windows machines on the samba share.  The samba file shares from my server work fine.

If I attempt to print from my Windows machine, it says it prints the document but nothing happens.  

The only reasonable thing I can think of is that something's changed in samba and my old smb.conf file isn't cutting it anymore, but I've run the config check and I don't see any errors.

The log files in /var/log/samba are disturbingly spare, and searching for these errors doesn't appear to turn up a fix on google:

/var/log/samba/log.nineveh:
```
[2010/05/07 12:48:06,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/05/07 12:48:06,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/05/07 12:50:38,  1] smbd/service.c:1063(make_connection_snum)
  nineveh (192.168.11.2) connect to service ML-1610 initially as user trevor (uid=1000, gid=1000) (pid 4155)
[2010/05/07 12:50:54,  1] smbd/service.c:1240(close_cnum)
  nineveh (192.168.11.2) closed connection to service ML-1610
[2010/05/07 12:51:00,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/05/07 12:51:00,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
```

My smb.conf file: (the relevant bits, comments taken out):

```

[global]

	workgroup = ARBUTUS
	server string = %h server (Samba, Ubuntu)
	dns proxy = no
	interfaces = eth1
	bind interfaces only = yes
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	encrypt passwords = true
	passdb backend = tdbsam

	obey pam restrictions = yes
	unix password sync = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes
	map to guest = bad user

	usershare allow guests = Yes

	usershare owner only = False
	username map = /etc/samba/smbusers

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
	writeable = yes
	guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin
```

I'm close to being stumped.  Any ideas?

Thanks!
Trevor

---

### Post by TrevorBradley on 2010-05-07
An update.. I dug back in my samba logs, and the errors above are there before the update when the samba printer share was working.  So the log data above isn't going to help diagnose the problem... :(

---

### Post by TrevorBradley on 2010-05-07
I refuse to believe the logs won't help here...

tail -f /var/log/* /var/log/*/* (during the print attempt - snort junk removed):

```
==> auth.log <==
May  7 13:07:31 pergamon smbd[4950]: pam_unix(samba:session): session opened for user trevor by (uid=0)

==> samba/log.winbindd-idmap <==
[2010/05/07 13:07:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/05/07 13:07:31,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/05/07 13:07:31,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/05/07 13:07:31,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/05/07 13:07:31,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/05/07 13:07:31,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!

==> auth.log <==
May  7 13:07:41 pergamon smbd[4950]: pam_unix(samba:session): session closed for user trevor

==> samba/log.nineveh <==
[2010/05/07 13:07:41,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/05/07 13:07:41,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

==> daemon.log <==
May  7 13:07:51 pergamon avahi-daemon[1497]: last message repeated 2 times

==> samba/log.winbindd-idmap <==
[2010/05/07 13:07:51,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/05/07 13:07:51,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/05/07 13:07:51,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/05/07 13:07:51,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/05/07 13:07:51,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/05/07 13:07:51,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/05/07 13:07:51,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/05/07 13:07:51,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/05/07 13:07:51,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/05/07 13:07:51,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/05/07 13:07:51,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/05/07 13:07:51,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/05/07 13:07:51,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/05/07 13:07:51,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/05/07 13:07:51,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/05/07 13:07:51,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/05/07 13:07:51,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!

==> samba/log.winbindd-idmap <==
[2010/05/07 13:08:31,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/05/07 13:08:31,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/05/07 13:08:31,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/05/07 13:08:31,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/05/07 13:08:31,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/05/07 13:08:31,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!

```

---

### Post by TrevorBradley on 2010-05-07
Rats, I thought this thread would help, but no dice:

[http://ubuntuforums.org/showthread.php?t=1471622&page=2](http://ubuntuforums.org/showthread.php?t=1471622&page=2)

Also, connecting by WINS name or by IP address both work for file shares, but not for the printer.

Ugh.

---

### Post by TrevorBradley on 2010-05-07
What the hell?  It just started working.

Only changes:

Resetting smbpassword for one user (but not for another user which is also working).  (and after this it still wasn't working)

Restarting smbd and nmbd (and still didn't work)

Rebooting a Windows 7 machine on my network... then it worked for all machines on my network.

Spooky.

---

### Post by tjbonzo on 2010-11-04
apt-get remove winbind
solved the problem for me. 

No idea why winbind was even installed although as I was debugging I stumbled upon the statement: "If winbind appears installed and there is no reason why you run a winbind server on your client (if you don't know what it is, you probably don't need it),.."

Here are the errors I was seeing:

/var/log/samba# tail log.winbindd-idmap
[2010/11/03 23:23:56,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/11/03 23:23:56,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/11/03 23:23:56,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
  Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
[2010/11/03 23:23:56,  1] winbindd/idmap.c:321(idmap_init_domain)
  idmap initialization returned NT_STATUS_UNSUCCESSFUL
[2010/11/03 23:29:30,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)

---

