---
title: "Samba update broke Winbind?"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by Slim Backwater on 2010-02-23
Our Ubuntu 9.10 workstation has stopped authenticating with our Active Directory, apparently after the most recent Samba Update.

The most recent update broke our smb.conf due to changes in the idmap config syntax, maybe I've failed to understand the docs and properly reconfigure it, but many diagnostic commands succeed.

Everything appears to work, except actual authentication.  All these diagnostic commands work:
1. root~# wbinfo -u/-g
2. root~# getent password {domainuser}
3. root~# getent group {domaingroup}
4. root~# kinit
5. root~# net ads testjoin
6. root~# net ads leave ; # removes the computer object from AD
7. root~# net ads join -U Administrator; # creates the computer object.
8. root~# smbclient -k -L //server

These fail:
1. root!# testparm; # produces warning rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
2. root~# wbinfo -a ADAccount failes.
3. ssh to the server with ad credentials fails.
4. The Account Lockout policy never trips. I can make multiple attempts with good and bad passwords but the account never locks.  This makes me inclined to say that it's not actually attempting an authentication.

I've gathered this information as per the DebuggingSamba Edubuntu page ( [https://wiki.edubuntu.org/DebuggingSamba](https://wiki.edubuntu.org/DebuggingSamba) )
```

root@l3220:~# dpkg-query -W -f='${Package} ${Version} ${Source} ${Status}\n' | grep samba
libsmbclient 2:3.4.0-3ubuntu5.5 samba install ok installed
libwbclient0 2:3.4.0-3ubuntu5.5 samba install ok installed
samba 2:3.4.0-3ubuntu5.5  install ok installed
samba-common 2:3.4.0-3ubuntu5.5 samba install ok installed
samba-common-bin 2:3.4.0-3ubuntu5.5 samba install ok installed
smbclient 2:3.4.0-3ubuntu5.5 samba install ok installed
smbfs 2:3.4.0-3ubuntu5.5 samba install ok installed
winbind 2:3.4.0-3ubuntu5.5 samba install ok installed

root@l3220:~# cat /etc/samba/smb.conf 
[global]
    security = ads
    realm = INTERFAST.CA

    workgroup = INTERFAST

    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431

    encrypt passwords = yes

    server string = %h server (Samba, Ubuntu)

    wins support = no
    disable netbios = yes

    log file = /var/log/samba/log.%m

    max log size = 1000

    panic action = /usr/share/samba/panic-action %d

    allow trusted domains = no
    
    idmap config INTERFAST : backend = rid
    idmap config INTERFAST : range = 16777216-33554431
    idmap config INTERFAST:base_rid = 0
    
    winbind use default domain = Yes
    winbind enum users = No
    winbind enum groups = No
    winbind nested groups = No
    template shell = /bin/bash
    dns proxy = no
    winbind refresh tickets = yes

root@l3220:~# cat /etc/krb5.conf
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 default_realm = INTERFAST.CA
 dns_lookup_realm = true
 dns_lookup_kdc = true
 ticket_lifetime = 24h
 forwardable = yes

[realms]

[domain_realm]

[appdefaults]
 pam = {
   debug = false
   ticket_lifetime = 36000
   renew_lifetime = 36000
   forwardable = true
   krb4_convert = false
 }

root@l3220:~# smbclient -k -L //penny
OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
... many valid shares listed ...
Connection to penny failed (Error NT_STATUS_CONNECTION_REFUSED)
NetBIOS over TCP disabled -- no workgroup available

root@l3220:~# cat /etc/pam.d/common-auth 
auth    sufficient    pam_winbind.so
auth    sufficient    pam_unix.so nullok_secure use_first_pass
auth    required      pam_deny.so

root@l3220:~# cat /etc/pam.d/common-account 
account sufficient      pam_winbind.so
account required        pam_unix.so

root@l3220:~# cat /etc/pam.d/common-session
session required        pam_unix.so
session required        pam_mkhomedir.so umask=0022 skel=/etc/skel

root@l3220:~# cat /etc/pam.d/common-password 
password   requisite   pam_unix.so nullok obscure md5
password   optional   pam_smbpass.so nullok use_authtok use_first_pass missingok


```

Oh My, I just solved it by adding this to smb.conf
    client ntlmv2 auth = yes

I had it in my previous smb.conf but commented it out while trying to solve this problem.  I must have had multiple failures and fixed the other problem somewhere along the line.  If I had to guess, it was that ntpd was trying an old internal server and the time had drifted off by over an hour.  Or there was a required change to the pam.d/* files with the new smb.conf syntax, or that I didn't convert the idmap lines in the smb.conf properly...

Oh well.  I've finished this so I'll just post it as solved as this collection of config files works for me.

._.

---

