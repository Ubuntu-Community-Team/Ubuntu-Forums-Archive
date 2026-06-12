---
title: "samba problem"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2006-09-10
this is my samba.conf file

```

[global]
    ; General server settings
    netbios name = server
    server string = Mitja B. %h - server (Samba, mitjab)
    workgroup = Doma
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
   valid users = %S
   create mode = 0600
   directory mode = 0755
   browseable = no
   read only = no
   veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.

[mreza-vsi]
    path = /home/samba/
    browseable = yes
    writable = yes
    read only = no
    guest ok = yes
    public = yes
    create mask = 0644
    directory mask = 0755
    force user = mitjab
    force group = mitjab

```

No one can write in mreza-vsi even i have write to yes.

Another problem is that mreza-vsi must be public but i can see it onl if i enter username and passwd when i click ok Mitja B. server - server (Samba, mitjab) computer. 
Mreza-vsi must be public so anyone must see it. Why they do not se it?

thx

---

