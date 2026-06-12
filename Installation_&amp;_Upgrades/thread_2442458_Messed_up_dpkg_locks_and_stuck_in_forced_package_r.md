---
title: "Messed up dpkg locks and stuck in forced package reconfiguration loop. Help!"
date: 2020-05-04
forum: Installation &amp; Upgrades
---

### Post by rabic on 2020-05-04
While trying to get out of a dpkg lock issue, 
[https://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process](https://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)
I manually removed these locks (unwisely)
```
sudo rm /var/lib/apt/lists/lock
sudo rm /var/lib/dpkg/lock 
sudo rm /var/cache/apt/archives/lock
sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock
sudo fuser -cuk /var/cache/apt/archives/lock; sudo rm -f /var/cache/apt/archives/lock
```

Now forced package reconfiguration hangs with the following :
```
sudo dpkg --configure -a 
Configuring postgresql-common &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; &#9474; 
&#9474; Obsolete major version 9.5 
&#9474; 
&#9474; The PostgreSQL version 9.5 is obsolete, but the server or client 
&#9474; packages are still installed. Please install the latest packages 
&#9474; (postgresql-12 and postgresql-client-12) and upgrade the existing 
&#9474; clusters with pg_upgradecluster (see manpage). 
&#9474; 
&#9474; Please be aware that the installation of postgresql-12 will 
&#9474; automatically create a default cluster 12/main. If you want to upgrade 
&#9474; the 9.5/main cluster, you need to remove the already existing 12 cluster 
&#9474; (pg_dropcluster --stop 12 main, see manpage for details). 
&#9474; 
&#9474; The old server and client packages are no longer supported. After the 
&#9474; existing clusters are upgraded, the postgresql-9.5 and 
&#9474; 
&#9474; <Ok> 
```



It hangs here, and the only way out seems to be reboot.
I could pg_upgrade to pg12
But trying to remove these pg9.5 packages, again throws this reconfiguration error:

```
sudo apt remove postgresql-9.5 postgresql-client-9.5
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
``` 

I am stuck in a loop. Help!

---

### Post by Impavidus on 2020-05-04
This may sound obvious, but some users seem to have problems with it. This is a regular, text-based menu. Can you select the OK button with tab, then hit enter to proceed? You may be able to scroll the text with the arrow keys, page up/down etc.

I don't know about postgresql.

---

