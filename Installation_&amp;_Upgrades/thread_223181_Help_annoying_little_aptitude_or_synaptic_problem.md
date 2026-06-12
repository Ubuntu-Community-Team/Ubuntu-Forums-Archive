---
title: "Help annoying little aptitude or synaptic problem"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by iammeagain on 2006-07-26
If I try to update through the notifier or try installing new packages it won't let me. For some reason my computer thinks that im still running adpitude, synaptic, or some other install program. Which I'm not, i have tried restarting and it keeps doin this. Please help, no rush tho i dont really need the updates, but  i will eventually.

This is probably an easy fix. that could explain why i can't find any other forums on it. I feel stupid even asking for help. ](*,)

---

### Post by aysiu on 2006-07-26
Have you tried this? ```
sudo killall dpkg
sudo killall aptitude
sudo killall synaptic
```

---

### Post by iammeagain on 2006-07-26
yea, tried that already. It just tells me there is no process killed, for each one.

---

### Post by iammeagain on 2006-07-26
any one else out there got any ideas? 

thanx anyways aysiu

---

### Post by iammeagain on 2006-07-27
its working now so nvm. The only thing i did that i think would make a diff is: 

taylor@taylor-desktop:~$ sudo dpkg --configure -a
Password:
Setting up libgsmme1c2a (1.10-9ubuntu1) ...

Setting up gforge-db-postgresql (3.1-31) ...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 25.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 31.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 31.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 42.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 42.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 42.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 56.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 56.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 56.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 63.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 69.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 75.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 81.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 87.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 92.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 92.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 92.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 97.
Configuring for PostgreSQL 7.3 or later
cp: cannot stat `/etc/postgresql/pg_hba.conf': No such file or directory
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
dpkg: error processing gforge-db-postgresql (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gforge-web-apache:
 gforge-web-apache depends on gforge-db-postgresql | gforge-db; however:
  Package gforge-db-postgresql is not configured yet.
  Package gforge-db is not installed.
  Package gforge-db-postgresql which provides gforge-db is not configured yet.
dpkg: error processing gforge-web-apache (--configure):
 dependency problems - leaving unconfigured
Setting up multisync (0.82-5.2build1) ...

Setting up gsm-utils (1.10-9ubuntu1) ...
Adding group `gsmsms' (1001)...
Done.
Adding system user `gsmsms'...
Adding new user `gsmsms' (107) with group `gsmsms'.
Not creating home directory `/var/spool/sms'.
Adding user `gsmsms' to group `dialout'...
Done.
chown: cannot access `/var/run/gsm-utils': No such file or directory
dpkg: error processing gsm-utils (--configure):
 subprocess post-installation script returned error exit status 1
Setting up xgsmlib (0.2-4ubuntu2) ...

dpkg: dependency problems prevent configuration of gforge-theme-starterpack:
 gforge-theme-starterpack depends on gforge-web-apache | gforge-web; however:
  Package gforge-web-apache is not configured yet.
  Package gforge-web is not installed.
  Package gforge-web-apache which provides gforge-web is not configured yet.
 gforge-theme-starterpack depends on gforge-db-postgresql | gforge-db; however:
  Package gforge-db-postgresql is not configured yet.
  Package gforge-db is not installed.
  Package gforge-db-postgresql which provides gforge-db is not configured yet.
dpkg: error processing gforge-theme-starterpack (--configure):
 dependency problems - leaving unconfigured
Setting up libmultisync-plugin-irmc (0.82-5.2build1) ...
Errors were encountered while processing:
 gforge-db-postgresql
 gforge-web-apache
 gsm-utils
 gforge-theme-starterpack
taylor@taylor-desktop:~$

not too sure what that even is doing, maybe someone can explain incase i have the same problem?

---

