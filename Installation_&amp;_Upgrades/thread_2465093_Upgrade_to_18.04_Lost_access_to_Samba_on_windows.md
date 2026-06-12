---
title: "Upgrade to 18.04 Lost access to Samba on windows"
date: 2021-07-21
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2021-07-21
I just did a do-release-upgrade on my Samba DC from 18.04 to 20.04 the upgrade went well however now I cannot access my domain from my windows machines.

Initially I was getting an error that my Domain was not available. I can't access any of the shares. 

I removed one computer from the Domain to try to rejoin it. When I do try to rejoin from windows I get an error "The request is not supported." smbd and nmbd are runningon the DC.

I can apparently log in to the domain users on other machines, but not access the shares.

---

### Post by rsteinmetz70112 on 2021-07-22
I also posted this in the samba list server and got the answer. I'm posting it here in case anyone else needs it.
This is an NT4 style domain and with the version of Samba shipped in 20.04 (Version 4.11.6-Ubuntu)
you need to as the following line to the smb.conf file and restart samba.service

```
client min protocol = NT1
server min protocol = NT1
```
Also NT4 styles domains are going away and I'm planning to convert mine as soon as I clear out some other issues.
I also want to than the Samba mailing list for responding promptly and knowledgeably.

---

