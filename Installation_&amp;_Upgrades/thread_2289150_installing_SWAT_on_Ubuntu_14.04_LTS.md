---
title: "installing SWAT on Ubuntu 14.04 LTS"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by Aeid on 2015-08-01
Hi , i was wondering is SWAT is still available as a web interface for Samba? last time i installed samba was moons a go ,and i remember that i used SWAT to manage file shares using web access ,i have installed Ubuntu server 14.04.2 and added samba ,but when i typed apt-get install samba it shows me this message attached,please let me know if there is any substitute if this one has gone

---

### Post by Vladlenin5000 on 2015-08-01
Hi and welcome.

With just a quick Google search one can easily understand it is no longer available and cannot be installed in recent releases.

> SWAT is no longer actively maintained, and its default configuration is 
not secure for use over an untrusted network.  SWAT will also rewrite 
smb.conf, rearranging the entries and deleting all comments as well as 
include= and copy= options, so is not suitable for use in conjunction 
with hand-edited smb.conf files or the default package-managed 
configuration.

---

