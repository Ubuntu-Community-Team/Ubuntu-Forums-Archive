---
title: "Samba not working after release-upgrade from 18.04 LTS to 20.04 LTS"
date: 2021-02-06
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2021-02-06
I upgraded a Ubuntu 18.04 LTS samba to 20.04 yesterday testing it I find the Samba part of the server is no working properly.

The new Samba Version 4.11.6-Ubuntu. The PDC is running 4.7.6-Ubuntu. I plan to upgrade the PDC as soon as I finish this one.

The server is a MEMBER SERVER of a NT4 style domain. smbd, nmbd and winbind are running but wbinfo and getent don't seem to be getting anything. I cannot browse the computer.

I have not edited the smb.conf file.
The output of testparm and the global section is below.
```
 # testparm
 Load smb config files from /etc/samba/smb.conf
 Loaded services file OK.
 Server role: ROLE_DOMAIN_MEMBER

 Press enter to see a dump of your service definitions

 # Global parameters
 [global]
         log file = /var/log/samba/log.%m
         max log size = 1000
         name resolve order = wins bcast host
         panic action = /usr/share/samba/panic-action %d
         security = DOMAIN
         server string = %h file server (Samba, Ubuntu)
         template shell = /bin/bash
         winbind enum groups = Yes
         winbind enum users = Yes
         winbind use default domain = Yes
         wins proxy = Yes
         wins server = 192.168.1.24
         workgroup = ATLANTA
         idmap config * : range = 10000-20000
         idmap config * : backend = tdb
         admin users = administrator rob
         hosts allow = 192.168.1.0/255.255.255.0
```
I think it likely that the problem is caused by changes in the Ubuntu networking.

---

### Post by rsteinmetz70112 on 2021-02-06
OK I've solved it. 
I think I knew this 20.04 uses samba version  4.11.6-Ubuntu which requires SMB2 as a minimum, that is new since 4.11.
Apparently  4.7.6-Ubuntu doesn't speak SMB2, I though it was new enough that it did.
Adding
 ```
 client min protocol = NT1
        server min protocol = NT1
```
To the smb.conf file fixed it.

Once I get the other server upgraded I'll test it out and see if I can eliminate it. I think all of my clients can speak SMB2 or don't need it. All of the Windows are Windows 10. I don't think any of the devices need SMB at all. 
I've checked the release notes and found that 4.7 is supposed to speak SMB2, what I don't understand is why they couldn't negotiate an SMB2 connection.

---

### Post by equi000 on 2021-02-07
I had the same issue yesterday after upgrading to 20.04 (clean install). My FritzBox router&#8216;s NAS only speaks V1, too.

---

