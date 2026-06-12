---
title: "Samba drives me ^&amp;*"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-09-07
I have a desktop, which has a printer and more space then my notebooks. I would like to use my desktop to share printer and a directory.

grep -v ^# /etc/samba/smb.conf|grep -v ^\;|grep -v ^$
> [global]
   workgroup = ELMIT
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY
wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[Ronald Shares]
path = /home/ronald/Desktop/Ronald_Shares
comment = Folder Ronald Shares with you
available = yes
browsable = yes
public = yes
writable = yes

My notebooks (Ubuntu) and another Windows machine (Visa) cannot even SEE my desktop. What am I missing?

bye

Ronald

---

