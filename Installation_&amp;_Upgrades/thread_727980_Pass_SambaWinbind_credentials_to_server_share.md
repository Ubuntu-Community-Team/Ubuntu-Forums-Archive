---
title: "Pass Samba/Winbind credentials to server share"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by wayne869 on 2008-03-18
I have Ubuntu 7.1 installed and authenticating to my Windows2003 AD Domain and everything working correctly, I just can't figure out how to mount file shares without creating a password file that I have to edit every 45 days when my password changes. I would like to know if there is a way to pass the credentials to the server that I logged onto Ubuntu with (Which is my AD username/Password)

---

### Post by wayne869 on 2008-03-19
Ok I figured out that I wasn't getting a Kerberos Ticket so I have fixed that issue and I am able to browse to my share through Firefox via. smb://server/share and not be asked for a password and I can connect to server and not be asked for a password but I can't figure out how to mount a windows 2003 Server share through fstab or any other way.  I see the option of using sec=krb5 with cifs but that don't seem to work.

---

### Post by wayne869 on 2008-03-20
Ok I figured it out if anyone else is interested.  Not on my own but with alot of googling..  I used pam and edited pam_mount.conf

Mount based upon group membership

volume @@DomainGroup smbfs <server> share /home/DOMAIN/&/mountfolder

Or Anyone

volume * smbfs server share /home/DOMAIN/&/mountfolder

---

