---
title: "cifs error when upgrading to 15.04"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by pingaan on 2015-05-23
Hi,

I recently upgraded to 15.04 and for some reason one of my cifs mounts stopped working I keep getting this message: 
```
mount: //192.168.1.111/Samsung is write-protected, mounting read-only
mount: cannot mount //192.168.1.111/Samsung read-only
```

I'll start from the top..
fstab on the server:
```
UUID=93042e4b-e587-44b1-b30e-61d099121e75 /media/Seagate_2 ext4 defaults 1 1
UUID=7845395c-2e13-434a-8ee9-68d72d8eca02 /media/Samsung ext4 ext4 defaults 1 1
UUID=3C14BEAA14BE6694 /mnt/windows7 ntfs-3g uid=1000,gid=1000,umask=000,auto 0 0
```

smb.conf:
```
[Seagate_2]
comment = Seagate, disk 2
path = /media/Seagate_2
browsable = yes
valid users = x
read only = no
writeable = yes
create mask = 0755


[Samsung]
comment = Samsung
path = /media/Samsung
browsable = yes
valid users = x
read only = no
writeable = yes
creat mask = 0755


[Windows_7]
comment = Windows 7, server
path = /mnt/windows7
browsable = yes
valid users = x
read only = no
writeable = yes
create mask 0755
```

And finally fstab on client computer:
```
//192.168.1.111/Samsung  /media/Samsung  cifs  username=x,password=x,iocharset=utf8,sec=ntlm  0  0
//192.168.1.111/Seagate_2  /media/Seagate_2  cifs  username=x,password=x,iocharset=utf8,sec=ntlm  0  0
//192.168.1.111/Windows_7  /media/Windows_7  cifs  username=x,password=x,iocharset=utf8,sec=ntlm  0  0
```

I am clueless...
Everything worked just fine before upgrading.

---

### Post by pingaan on 2015-05-24
Maybe I should add that I did format the drive but updated the UUID.

---

### Post by pingaan on 2015-05-30
No one?

---

### Post by pingaan on 2015-05-30
Sorted it out by changing users.

---

