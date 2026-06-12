---
title: "Samba"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by apamix on 2011-06-10
Hello i have SquareOne ( [www.myitian.com]("http://www.myitian.com") ) for little network NAS server but when i try to log in with admin or guest account i get failed :) 

Take a look what he have in the smb.conf
```

[global]
follow symlinks=yes
dead time=5
preserve case=yes
map to guest=bad user
mangled names=yes
unix password sync=false
unix charset=UTF-8 
dos filetimes=yes
short preserve case=yes
domain logons=no
encrypt passwords=yes
log file=/var/log/log.smbd
delete readonly=yes
workgroup=WERKGROEP
directory security mask=777
use sendfile=no
null passwords=yes
wide links=yes
wins support=no
load printers=yes
max log size=1000
server string=Square One
guest account=guest-share
use receivefile=no
delete veto files=yes
default case=upper
browseable=yes
name resolve order=lmhosts host wins bcast
case sensitive=no
pid directory=/var/run
security=user
dos charset=UTF-8
interfaces=br0
printing=lprng
printcap name=/etc/printcap
security mask=777
display charset=UTF-8
share modes=yes
veto files=/lost+found/Network Trash Folder/.AppleDouble/.AppleDesktop/Icon^M/
dns proxy=no
socket options=IPTOS_LOWDELAY TCP_NODELAY SO_SNDBUF=65535 SO_RCVBUF=65535
[admin]
use receivefile=yes
create mask=0775
write list=admin
path=/mnt/ide3/admin/
directory mask=0775
writeable=no
available=1
valid users=admin
use sendfile=yes
[public]
use receivefile=yes
create mask=0777
comment=Folder Share for public
write list=admin
path=/mnt/ide3/public
public=yes
directory mask=0777
writeable=no
available=1
use sendfile=yes
[printers]
comment=Square One Printer Server
browsable=no
use client driver=yes
path=/var/spool/samba
printable=yes
lpresume command=/usr/hddapp/bin/lpc release %p %j
public=no
create mode=0777
print command=/usr/hddapp/bin/lpr -P%p -r %s
lpq command=/usr/hddapp/bin/lpq -P%p
lprm command=/usr/hddapp/bin/lprm -P%p %j
queueresume command=/usr/hddapp/bin/lpc -P%p start
queuepause command=/usr/hddapp/bin/lpc -P%p stop
writable=no
lppause command=/usr/hddapp/bin/lpc hold %p %j
[client]
use receivefile=yes
create mask=0775
write list=client,admin
path=/mnt/ide3/client/
directory mask=0775
writeable=no
available=1
valid users=client,admin
use sendfile=yes
[software]
use receivefile=yes
create mask=0777
write list=admin
path=/mnt/ide3/software
directory mask=0777
writeable=no
available=1
valid users=guest-share,admin
use sendfile=yesthen
```smbpasswd

```
guest:1025:AAD3B435B51404EEAAD3B435B51404EE:31D6CFE0D16AE931B73C59D7E0C089C0:[U
admin:0:F0D412BD764FFE81AAD3B435B51404EE:209C6174DA490CAEB422F3FA5A7AE634:[U
guest-share:7797:AAD3B435B51404EEAAD3B435B51404EE:31D6CFE0D16AE931B73C59D7E0C089
```And not matter what i do i can't log in folders :( If anybody have some idea will be nice to have some help ;)

---

