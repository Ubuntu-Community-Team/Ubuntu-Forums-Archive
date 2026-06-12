---
title: "samab auto autheticate in windows"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by cosmofrog on 2007-11-11
my samba shares will not auto mount in xp pro. im looking to have the files register by the user login and pass of the windows box. i have set up my /etc/samba/smbusers to reflect the usernames needed. i have also used 

'sudo smbpasswd -a username'     

to add user's pass. 

as well as the general

'sudo adduser username'

to get the user on the linux box.

im running feisty.

whenever i type in the samba address in windows \\server\share\ it prompts me for a password. i would like it to automatically register with the windows account i am using so i am not prompted for a password or authentication.

here is my smb.conf file

____________________________________________________

[global]
workgroup = workgroup
netbios name = server
encrypt passwords = yes

socket options = TCP_NODELAY SO_RCVBUF=4096 SO_SNDBUF=4096

security = user
username map = /etc/samba/smbusers


[Toast]
comment = hells yes?
path = /media/toast
#writable = yes
read only = no
valid users = user1, user2
#invalid users =
force user = nobody
force group  = nogroup
browseable = yes
public = yes
write list = user1, user2, user3

________________________________________________



any help would really be appreciated. thanks in advance.

---

