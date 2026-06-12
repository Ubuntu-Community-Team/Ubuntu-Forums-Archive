---
title: "Samba4 NT_STATUS_NO_SUCH_DOMAIN"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by norland on 2010-09-27
[SIZE=3]sudo smbclient -L //127.0.0.1 gives the above error NT_STATUS_NO_SUCH_DOMAIN on Ubuntu 10.04 desktop edition.  I also can't view my linux machine from other computers using "net view" command.  Is there any particular (network?) package that I am missing or should I be using the older samba packages.[/SIZE] [SIZE=3] What is preventing Samba from being visible?[/SIZE]

I also  get these warnings when running "samba restart"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest only"
Ignoring unknown parameter "guest only"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"

[SIZE=3]Should their be a newer way to configure samba for samba4?[/SIZE]
my smb.conf file is as show below:

[global]
;    guest account = nobody
;    netbios name = Linux
        server string = Linux
    security = share
;    socket options = TCP_NODELAY IPTOS_LOWDELAY
    workgroup = workgroup
;    server string = samba 3.4.7
    encrypt passwords = no
    guest ok = yes
        hosts allow = 192.168.0.13
        interfaces = lo etho

[public]
    path = /home/linuxuser
    guest ok = yes
    guest only = yes
    read only = no
        writable = yes
        create mask = 0666

---

### Post by mycroes on 2010-09-29
Is your samba running? The init script that accompanies samba4 is broken, so do a 'ps ax | grep samba' to see if samba is running. If you manually create a /var/run/samba folder, samba4 will start, however this doesn't persist after reboot.
Regards,

Michael

---

