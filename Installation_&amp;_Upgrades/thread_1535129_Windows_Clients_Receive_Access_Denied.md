---
title: "Windows Clients Receive Access Denied"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by brant1 on 2010-07-20
I am a newbie to Ubuntu and have just about finished configuring SAMBA for file sharing. However, my Windows clients experience an issue of being unable to create folders inside the new share I setup. I do not want any share security on this folder since its a global share that our entire office houses client information. They can view the contents but not add it.

My smb.conf has the following settings on the share
[global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    obey pam restrictions = yes
    map to guest = bad user
    encrypt passwords = true
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    server string = %h server (Samba, Ubuntu)
    default = global
    unix password sync = yes
    workgroup = DOMAIN
    os level = 20
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = yes
    max log size = 1000
    pam password change = yes

[Cls_Mstr]
    writeable = yes
    create mode = 0777
    public = yes
    path = /Shares/
    directory mode = 0777

---

### Post by gordintoronto on 2010-07-20
The Windows clients are also members of the DOMAIN workgroup?

Have you tried making it lower case?

---

