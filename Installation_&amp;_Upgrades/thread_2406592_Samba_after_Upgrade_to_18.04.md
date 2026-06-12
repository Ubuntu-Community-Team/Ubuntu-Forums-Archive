---
title: "Samba after Upgrade to 18.04"
date: 2018-11-22
forum: Installation &amp; Upgrades
---

### Post by dalewis62 on 2018-11-22
I have upgraded from 16.04.5 to 18.04 and I cannot get Samba to work with any level of authentication for old SMB1 clients.  Only works with my old clients if I set up a public share.  Any ideas or wisdom to resolve would be appreciated.

Here is my Global and and example share settings.

[global]
        usershare allow guests = yes
        server role = standalone server
        map to guest = bad user
        workgroup = WORKGROUP
        pam password change = yes
        server string = %h server (Samba, Ubuntu)
        wins support = true
        dns proxy = no
        unix extensions = no
        unix password sync = yes
        syslog = 0
        os level = 20
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000
        follow symlinks = yes
        wide links = yes
        log file = /var/log/samba/log.%m
        netbios name = thor
        passdb backend = tdbsam
        remote announce = 192.168.1.4
        obey pam restrictions = yes
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


[Jukebox]
        force user = dan
        valid users = dan,@dan
        writeable = yes
        path = /media/WD20EARX/RaidMain/JukeBox
        force group = dan

---

