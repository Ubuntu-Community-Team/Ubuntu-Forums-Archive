---
title: "Samba Help Please (Yes. I'm an idiot)"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by mdk1967 on 2006-12-04
Been using dapper for several months and had a perfectly functional samba set up to share my files on my home network.

After I installed  edgy I tried to set up my Samba shares again but I'm obviously missing something because although I can see the samba server from my windows machine, and connect, I cannotsee my drives. Only the printers and fax

I modified the samba conf file as follows:

workgroup = MSHOME (example)
netbios name = samba_server_name (example)

security = user

writable = yes
browsable = yes

create mask = 0664

create mask = 0664

directory mask = 775

sudo smbpasswd -a username


I know i'm leaving out something simple so I'd appreciate it if you went easy on me ;)

---

