---
title: "samba 4.15.13 nt1 problem"
date: 2023-03-10
forum: Installation &amp; Upgrades
---

### Post by acumensystemleo on 2023-03-10
Today ubuntu samba update to 4.15.13. After update my old mac ( mac os 10.6 ) cannot list the folder . server min protocol = NT1 has been setup in samba . Thanks. 


ubuntu version: 20.04
samba 4.15.13

---

### Post by TheFu on 2023-03-10
Can't help with MacOS and Samba.  The few weeks I had a Mac, it was broken (CIFS integration).
But Linux and MacOS are Unix-based OSes, so perhaps using NFS would be a better option?
[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)
NFS is how Unix systems share storage and has been around 30+ yrs, at least.  NFSv4 has been around since before 2005, so the protocol is very stable. It is usually a bit faster than CIFS, but it is a server-to-server setup, not dependent on any single user. Native POSIX file systems are supported with all the things those provide. The main thing is that native UNIX permissions are fully supported so chgrp and chmod work as expected.

If you insist on staying with Samba, perhaps reviewing the release notes for every version between the prior and current version would make sense?  Normal troubleshooting for samba is to run **testparm** on the server to see what the actual config on the server is.  Sometimes what humans think are set, aren't really set.

---

### Post by MAFoElffen on 2023-03-10
Please post the results of
```

grep 'min protocol' /etc/samba.conf
nmap -p445 -Pn -vvv --script smb-protocols

```
...there is also a minimum setting for 'client min protocol'... Though if not there, min to NT1 ( smbv1 ) and the max to SMBv3, which SMB3 defaults to SMB3_11, which is complaint with Windows 10... NT1 as min should allow all. So that does not explain why you can't connect, because of that.

---

