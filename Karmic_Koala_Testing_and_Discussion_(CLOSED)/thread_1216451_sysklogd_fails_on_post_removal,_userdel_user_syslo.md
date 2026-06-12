---
title: "sysklogd fails on post removal, userdel: user syslog is currently logged in"
date: 2009-07-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-07-18
sysklogd fails on postrm during purge since it tries to delete the user syslog, but the replacement rsyslogd is logged in in as that user now.can workaround just by removing the line
 deluser --system --quiet syslog
from /var/lib/dpkg/info/sysklogd.postrm 

D000002: fork/exec /var/lib/dpkg/info/sysklogd.postrm ( purge )
userdel: user syslog is currently logged in
/usr/sbin/deluser: `/usr/sbin/userdel syslog' returned error code 8. Exiting.
dpkg: error processing sysklogd (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 sysklogd

{EDIT] [https://bugs.launchpad.net/ubuntu/+source/sysklogd/+bug/401056](https://bugs.launchpad.net/ubuntu/+source/sysklogd/+bug/401056)

---

### Post by taavikko on 2009-07-18
didn't notice this during upgrades, but when tried to
```
sudo aptitude purge `dpkg -l | grep "^rc" | awk '{print $2}'`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  gnome-volume-control-pulse{p} klogd{p} sysklogd{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 131338 files and directories currently installed.)
Removing gnome-volume-control-pulse ...
Purging configuration files for gnome-volume-control-pulse ...
Removing klogd ...
Purging configuration files for klogd ...
Removing sysklogd ...
Purging configuration files for sysklogd ...
userdel: user syslog is currently logged in
/usr/sbin/deluser: `/usr/sbin/userdel syslog' returned error code 8. Exiting.
dpkg: error processing sysklogd (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 sysklogd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```

---

### Post by pferraro on 2009-07-18
> **taavikko said:**
> didn't notice this during upgrades, but when tried to
```
sudo aptitude purge `dpkg -l | grep "^rc" | awk '{print $2}'`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  gnome-volume-control-pulse{p} klogd{p} sysklogd{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 131338 files and directories currently installed.)
Removing gnome-volume-control-pulse ...
Purging configuration files for gnome-volume-control-pulse ...
Removing klogd ...
Purging configuration files for klogd ...
Removing sysklogd ...
Purging configuration files for sysklogd ...
userdel: user syslog is currently logged in
/usr/sbin/deluser: `/usr/sbin/userdel syslog' returned error code 8. Exiting.
dpkg: error processing sysklogd (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 sysklogd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```

The problem is, rsyslog, which replaces klogd and sysklogd also runs as the syslog user.
Quick fix:
1. Remove rsyslog, allow removal of ubuntu-minimal
2. Remove/Purge sysklogd - this should succeed now
3. Re-install ubuntu-minimal, forcing rsyslog to re-install.

---

### Post by phoogkamer on 2009-07-23
ah, this fixed the issue.

Thanks

---

### Post by useResa on 2009-07-26
Finally had time to investigate (Google ;-)) this issue.
Thanks for the tip, worked like a charm

---

### Post by Totzo on 2009-08-04
thanks + 1

---

