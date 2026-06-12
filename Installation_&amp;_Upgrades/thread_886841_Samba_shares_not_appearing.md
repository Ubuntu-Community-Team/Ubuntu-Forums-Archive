---
title: "Samba shares not appearing"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by bikeman1 on 2008-08-11
I am running kernel 2.6.20 with Samba 3.0.  The machine is configured as a Samba server.  

The samba.conf file I have is a tried and true one.  The security is user level connecting with a series of Windows 2K workstations. all users have  corresponding smbpasswords.  The shares all can be invoked by valid users, but the shares (nor the server itself) appears in any of the Network Neighborhoods.  This is despite the fact that all the shares are browseable = Yes.  The NT machines have the IP address of the server correctly listed in their hosts files in /system32.  The server shows up neither in "computers near me" nor in its workgroup.  All the workstations see each other fine.  The server can ping workstations and vice versa.  

What debugging can be done to figure out why the server is not being resolved (either on the server side or Win box side).  Is there a way to "force" windows net neighborhood to recognize an IP address ??  

here is a shortened version of the CONF file

[global]
workgroup = HRC1
server string = Heckle
hosts allow = 999.999.999.  127.
browseable = Yes
log file = /mnt/SambaLog/%m.log
max log size = 500
security = user
encrypt passwords = no
passwd program = /usr/bin/passwd %u
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = Yes
preferred master = Yes
dns proxy = no
guest account = nobody
kernel oplocks = yes

[bob]
comment = Annies's share
path = /mnt/Carol/bob
valid users = bob, dick
write list = bob, dick
read only = no
browseable = Yes
create mask = 0775
force group = users

any help or resources appreciated.  The keys to me were the /etc/hosts file server name and the hosts file on the PCs matching servername and address.

---

