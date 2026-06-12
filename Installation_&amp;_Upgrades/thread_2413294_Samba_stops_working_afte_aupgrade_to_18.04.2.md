---
title: "Samba stops working afte aupgrade to 18.04.2"
date: 2019-02-23
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-02-23
Samba will not start after an upgrade to 18.04. My samba is running as an NT style member server server with smbd nmbd and winbind all running. None of them will start.

```
root@louise:/var/log/samba# systemctl start smbd
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.
root@louise:/var/log/samba# systemctl status smbd
```
```

&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: ena
   Active: failed (Result: exit-code) since Sat 2019-02-23 18:01:35 EST; 20s ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 4594 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOP
 Main PID: 4594 (code=exited, status=1/FAILURE)

Feb 23 18:01:35 louise systemd[1]: Starting Samba SMB Daemon...
Feb 23 18:01:35 louise systemd[1]: smbd.service: Main process exited, code=exite
Feb 23 18:01:35 louise systemd[1]: smbd.service: Failed with result 'exit-code'.
Feb 23 18:01:35 louise systemd[1]: Failed to start Samba SMB Daemon.
lines 1-13/13 (END)
```

The information on al three processes is virtually identical.

```
root@louise:/var/log/samba# testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
handle_name_resolve_order: WARNING: Ignoring invalid list value 'hosts' for parameter 'name resolve order'
Error loading services.
```

I've found a number of posts with similar problems but none seem directly on point.

---

### Post by rsteinmetz70112 on 2019-02-23
OK I think I solved it. I changed the name resolv order, that allowed testparm to point to a couple of other errors specifically a logon server ipaddtess with security=domain and a second wins server address.
It seems that the name resolv order stops testparm for reading the smb.conf file, not just skip the entry as the warning  implies.

I went home for the day and will test more tomorrow.

---

