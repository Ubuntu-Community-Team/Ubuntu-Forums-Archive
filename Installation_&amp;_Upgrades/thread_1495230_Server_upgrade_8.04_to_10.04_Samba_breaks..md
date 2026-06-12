---
title: "Server upgrade 8.04 to 10.04: Samba breaks."
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by hkphooey on 2010-05-27
Just went through this myself, so I thought I'd post about it here, and give my solution in case it saves someone some time. 

So I decided to upgrade a server which had been humming away for three years as a fileserver and printserver when the new 10.4 release came out. I waited a few weeks for any obvious bugs to surface and then took the plunge. 

On restarting the server users were unable to login to file and print services. It turns out that all the Samba users had been removed on upgrading the server. 

My immediate solution was to recreate all the users by hand. As there were only 10 or so users this wasn't too bad. After that, I found that the passwords still weren't working so I had to recreate those. This command would have done double duty:
          > smbpasswd -a username
          Type password:
          Re-type password:

Once I'd done this samba was working as before. I could then find out why this had happened. It turns out that in the upgrade I'd switched from a version of samba that uses the /etc/samba/smbpasswd file to store user information, to one that uses the newer tdbsam format. There were no warnings during the upgrade, but the samba site says

"The default passdb backend has been changed to 'tdbsam'! That breaks existing setups using the 'smbpasswd' backend without explicit declaration! Please use 'passdb backend = smbpasswd' if you would like to stick to the 'smbpasswd' backend or convert your smbpasswd entries using e.g. 'pdbedit -i smbpasswd -e tdbsam'. "

So there is one solution then. If you have a lot of users it might be a good idea to change back to smbpasswd format until you can migrate them to the new one.

---

