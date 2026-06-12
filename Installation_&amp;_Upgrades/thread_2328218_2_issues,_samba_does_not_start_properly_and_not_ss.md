---
title: "2 issues, samba does not start properly and not ssh from older clients"
date: 2016-06-18
forum: Installation &amp; Upgrades
---

### Post by egandt on 2016-06-18
I assume the older client issue is protocol related, but I'd like confirmation:

Error is in key excahneg:
[Jun 18 18:32:19] 1001 Algorithm_negotiation_failure, Algorithm: KEX, Client algorithms: diffie-hellman-group1-sha1,extension1-sha1@ssh.com, Server algorithms: [email]curve25519-sha256@libssh.org[/email],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-

The bigger one is samba is it is masked I have no idea why so I have to start it via:
service start nmbd ; serverice start smbd 
    even then it is not started, and it does not work.  First why is the systemd samba masked, second why is the service failing to start on boot, the sysv-rc-conf shows they are set to autostart in multi-user modes (which I'm in) and this is not a systemd script?

Thanks,
ERIC

---

