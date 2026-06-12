---
title: "Proftp not working correctly since upgrade"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by dajasc on 2010-05-10
Before upgrade:
Proftp was accepting either secure (sftp) or insecure connections

After upgrade:
It will accept only secure connections.  Nothing has been changed in the proftpd.conf file, TLSRequired off is still set as it was.  One clue is that when I start proftpd it warns that 127:0.0.0:21 is already in use by "DJJC-Netserver".  It turns out that that is the server name given to the ftp server by proftpd.conf and if I change it there it does change the warning accordingly.  I have checked after stopping proftpd that nothing has port 21 and then as soon as I start the server it warns essentially that it is already using that port.

I know very little about this whole thing any ideas would be appreciated.

---

