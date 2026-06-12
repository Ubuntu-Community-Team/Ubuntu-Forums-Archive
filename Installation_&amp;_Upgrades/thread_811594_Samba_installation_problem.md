---
title: "Samba installation problem"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by Kimster on 2008-05-29
Hello

I used webmin at first to install samba but something happened there and it didnt end as it should.

Anyway, I tried to install it via commandshell later and it didnt work out. So I tried to uninstall it via commandshell and it gives me a lots of errors.

I have tried 
apt-get install samba
apt-get remove samba
apt-get purge samba
apt-get install update-inetd
apt-get -f install samba
apt-get install --reinstall samba samba-common

I have read many threads that nearly looks like mine, but I havent managed fix it.

The error I get for using: apt-get -f install samba

Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 66 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up samba-common (3.0.28a-1ubuntu4) ...
Not replacing deleted config file /etc/samba/smb.conf
chmod: cannot access `/etc/samba/smb.conf': No such file or directory
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 3.0.28a-1ubuntu4); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 samba
 smbclient


Anyone please ?

---

### Post by Kimster on 2008-05-30
Well, I dont know how, but I managed to solve it, I think.
I just took another smb.conf file and put it in the /etc/samba dir. Then installation worked.  

funny..

---

