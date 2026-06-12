---
title: "After (re) installing samba smbpasswd doesn't work"
date: 2015-01-27
forum: Installation &amp; Upgrades
---

### Post by andras-merenyinet on 2015-01-27
Hello,
I purged the whole samba stuff and installed samba and smbclient packages.

I try to add users with both smbpasswd and pdbedit. It looks good first but no user in database.

```

root@snurf:~# smbpasswd -a andras
New SMB password:
Retype new SMB password:
root@snurf:~# pdbedit –L
Username not found!
root@snurf:~# pdbedit -a andras
new password:
retype new password:
Unix username:        andras
NT username:
Account Flags:        [U          ]
User SID:             S-1-5-21-2551009283-2798110900-269676425-1000
Primary Group SID:    S-1-5-21-2551009283-2798110900-269676425-513
Full Name:            Mer&#9618;nyi Andr&#9618;s
Home Directory:       [\\snurf\andras]("file://\\snurf\andras")
HomeDir Drive:
Logon Script:
Profile Path:         [\\snurf\andras\profile]("file://\\snurf\andras\profile")
Domain:               SNURF
Account desc:
Workstations:
Munged dial:
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 16:06:39 CET
Kickoff time:         Wed, 06 Feb 2036 16:06:39 CET
Password last set:    Tue, 27 Jan 2015 22:36:52 CET
Password can change:  Tue, 27 Jan 2015 22:36:52 CET
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
root@snurf:~# pdbedit –L
Username not found!
root@snurf:~#

```

I'm on Ubuntu 14.04.1 LTS.
Samba version 4.1.6-Ubuntu
smb.conf is the original one comes with the install.


Thanks in advance.

---

### Post by andras-merenyinet on 2015-01-28
Come on guys, noone has idea?

---

### Post by andras-merenyinet on 2015-01-28
I changed smb.conf and set ```
passdb backend = smbpasswd
```
Restarted smbd and ...
```

root@snurf:/etc/samba# smbpasswd -a andras
New SMB password:
Retype new SMB password:
Added user andras.
root@snurf:/etc/samba# pdbedit –L
Username not found!
root@snurf:/etc/samba# ls
gdbcommands  smb.conf  smb.conf.old  smb.conf.orig  smbpasswd  tls
root@snurf:/etc/samba# cat smbpasswd
andras:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:75CE1142D8CB66E7828823AE7A018DEA:[U          ]:LCT-54C926A2:
root@snurf:/etc/samba# pdbedit –L andras
Username not found!

```

So smbpasswd file appeared in /etc/samba and user registered in it tough pdbedit cannot see it. 
But at least I have a user database even if it is not the one I wish.

Unfortunately samba doesn't work yet. :(
```

andras@snurf:~$ smbclient -d3 -L snurf
lp_load_ex: refreshing parameters
Initialising global parameters
.
.
.
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE
andras@snurf:~$

```

So I'm not happy at all.
What is next?
Thanks

---

### Post by andras-merenyinet on 2015-01-30
Very supportive suggestions. :(

---

