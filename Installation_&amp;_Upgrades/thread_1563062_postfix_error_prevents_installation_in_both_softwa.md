---
title: "postfix error prevents installation in both software centre and in synaptic"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by brandenmikal on 2010-08-28
installArchives() failed: Selecting previously deselected package pq. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 189294 files and directories currently installed.) 
Unpacking pq (from .../pq_6.2-0ubuntu3_all.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for shared-mime-info ... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up postfix (2.7.0-1) ... 
 
Postfix configuration was not changed.  If you need to make changes, edit 
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration 
values, see postconf(1). 
 
After modifying main.cf, be sure to run '/etc/init.d/postfix reload'. 
 
Running newaliases 
newaliases: fatal: myorigin parameter setting must not contain multiple values: B. Mikal 
dpkg: error processing postfix (--configure): 
 subprocess installed post-installation script returned error exit status 75 
Setting up pq (6.2-0ubuntu3) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 postfix 
Setting up postfix (2.7.0-1) ... 
 
Postfix configuration was not changed.  If you need to make changes, edit 
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration 
values, see postconf(1). 
 
After modifying main.cf, be sure to run '/etc/init.d/postfix reload'. 
 
Running newaliases 
newaliases: fatal: myorigin parameter setting must not contain multiple values: B. Mikal 
dpkg: error processing postfix (--configure): 
 subprocess installed post-installation script returned error exit status 75 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place



[B]The above error message is given to me every time I try to install any form of software via the Software Center client and the Synaptic Manager.

Please help; I really don't want to go as far as re-installing Ubuntu to have this ability.

If you could post sudo commands or know of anything that could help solve this problem; feel free to contact me here via private message or simply post here.
[/B]

---

