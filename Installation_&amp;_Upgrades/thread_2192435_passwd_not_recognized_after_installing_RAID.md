---
title: "passwd not recognized after installing RAID"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by eugener on 2013-12-07
Ub 12.04, amd64 hp.  I installed RAID 1 on my desktop system using the alternative CD.  I had saved a copy of my previous /home on a pen drive.  When the RAID system seemed to be working OK, I copied the old /home onto the new system, but when I tried to reboot, I found that my passwd was not recognized.  I had used the same user name and passwd for the RAID install and I had used on my previous system.  When I tried to use the instructions in [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) to reset the passwd, I found that no users are listed in /home!
Any help appreciated.

---

### Post by Bashing-om on 2013-12-08
eugener; Hi !

All I can come up with is maybe the "home" directory did not exist, and thus the copy failed ??
What doees this show:
```

cd /
ls -la /home

```
Is a directory <your_user_name> in existence ?
As in my output, my username "sysop"
> 
sysop@1304mini:~$ ls -la /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 23 root  root   4096 Dec  4 17:25 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 22 sysop sysop  4096 Dec  8 14:24 sysop
sysop@1304mini:~$


Is the "/home" directory owned by you and are "you" listed as the group ?

Maybe create the directory and (re)copy the files ?

[INDENT][INDENT]strange things can happen
[/INDENT][/INDENT]

---

