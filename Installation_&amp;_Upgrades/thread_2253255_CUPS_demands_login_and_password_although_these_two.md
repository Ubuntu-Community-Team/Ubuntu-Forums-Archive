---
title: "CUPS demands login and password although these two were added"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by lan1967 on 2014-11-18
Hello, dear forum users.
I bought printer Samsung SCX 3400.
My system is Lubuntu 14.10
CUPS system is not working quite well. Added root and user to lp and lpadmin groups.
I used lppasswd to put password but still CUPS doesn't take root or user password. 
Thank you for your attention.

sudo lppasswd -g sys -a root
Enter password: 
Enter password again:


lsb_release -a; uname -a; groups
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic
Linux rootkit 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
rootkit adm lp cdrom sudo audio dip video plugdev users netdev lpadmin sambashare pulse

cat /etc/group | grep root
root :0:
adm :4:syslog,rootkit
lp :7:rootkit,root
cdrom :24:rootkit
sudo :27:rootkit
audio :29:rootkit,pulse
dip :30:rootkit
shadow :42:root
video :44:rootkit,vdr
plugdev :46:rootkit
users :100:rootkit
netdev :102:rootkit
lpadmin :113:rootkit,root
rootkit :1000:
sambashare :119:rootkit
pulse :123:rootkit

---

### Post by cariboo on 2014-11-19
I'm not sure why you seem to think why you need to add a root user, to use the CUPS web interface. but using the regular user and sudo works just fine for me. Hopefully you documented all the changes you made, so you can revert back to the default setup. Then run the CUPS web interface:

```
http://localhost:631
```

and enter your regular user name and password when asked.

---

