---
title: "Samba broken in upgrade from 12 to 14 LTS"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by snash on 2014-09-04
I did the fully upgrade from 12 LTS to 14.04.1 LTS
Samba worked before. Doesn't start now.
This is a simple family shared file server. 

Nothing I do in the smb.conf seems to make any improvement.  
The Samba troubleshooting guide has no help on getting the daemon started.
As of now....

testparm works:
[FONT=Courier New]snash@NashFS:/etc/samba$ testparm smb.conf
Load smb config files from smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Storage]"
Processing section "[2TB]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions[/FONT]


smbd is not starting (no process)
nmbd process has started

/var/log/samba/log.smbd contains:

[FONT=Courier New]
[2014/09/04 15:55:03,  0] ../source3/smbd/server.c:1198(main)
  smbd version 4.1.6-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2013
[2014/09/04 15:55:03.392012,  0] ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
[2014/09/04 15:55:03.399648,  0] ../source3/auth/auth_util.c:866(make_new_session_info_guest)
  make_server_info_info3 failed with NT_STATUS_NO_SUCH_USER
[2014/09/04 15:55:03.399907,  0] ../source3/smbd/server.c:1448(main)
  ERROR: failed to setup guest info.
[/FONT]

Your suggestions would be much appreciated.

=============================
smb.conf

[FONT=Courier New][global]
        security = user
        map to guest = Bad User
        workgroup = NASH
        log file = /var/log/samba/log.%m
        max log size = 1000
#
#       encrypt passwords = yes
        encrypt passwords = no
#
        server string = %h (Samba, Ubuntu)
        default = Storage
        load printers = no
        netbios name = NashFS
#       usershare allow guests = yes
#       wins support = yes
        guest account = Family
        hosts allow = 10.42.42.

[Storage]
        browseable = yes
        writeable = yes
        delete readonly = yes
        path = /Storage
        force group = sambashare
        force user = Family
        comment = Storage for Windows
        public = yes
        available = yes

[2TB]
        comment = Disk space with no mirror
        path = /2TB
        browseable = yes
        writeable = yes
        delete readonly = yes
        force group = sambashare
        force user = Family
        public = yes
        available = yes[/FONT]
=======================================

---

### Post by snash on 2014-09-05
SOLVED
The offend term is:
guest account = Family
I have had this term in for at least three years.   I have no idea why it broke in this upgrade. 
If have also done a clean reinstall of samba, but that may have made no difference.
I can break it at will by uncommenting the offending term.

My operational config now looks like this:
# /etc/samba/smb.conf
#
# Worked 140905 after Ubuntu upgrade to 14.04.1 LTS
#======================= Global Settings =======================

[global]
        map to guest = Bad User
        workgroup = NASH
        log file = /var/log/samba/log.%m
        max log size = 1000
        server string = %h (Samba, Ubuntu)
        default = Storage
        load printers = no
        wins support = yes
        hosts allow = 10.42.42.
# Causes failure
#       guest account = Family

[Storage]
        browseable = yes
        writeable = yes
        delete readonly = yes
        path = /Storage
        force group = sambashare
        force user = Family
        comment = Storage for Windows
        public = yes
        available = yes


[2TB]
        comment = Disk space with no mirror
        path = /2TB
        browseable = yes
        writeable = yes
        delete readonly = yes
        force group = sambashare
        force user = Family
        public = yes
        available = yes

---

