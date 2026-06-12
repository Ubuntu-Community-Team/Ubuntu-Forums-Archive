---
title: "Software Installation problems after Maverick install. Help!"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by misssarahdee on 2011-03-23
I have just installed Maverick, and when I try to install software via the Software Manager, I get the following error message. (I do not have anything else running as far as I know. Earlier, before I tried installing software, I had a screen regarding the install of **tth-mscorefonts** which wouldn;t allow me to agree to the terms and conditions, and I think the problem may have started there.):

installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
Selecting previously deselected package wordnet-base. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 124123 files and directories currently installed.) 
Unpacking wordnet-base (from .../wordnet-base_1%3a3.0-23ubuntu1_all.deb) ... 
Selecting previously deselected package wordnet. 
Unpacking wordnet (from .../wordnet_1%3a3.0-23ubuntu1_i386.deb) ... 
Selecting previously deselected package artha. 
Unpacking artha (from .../artha_1.0.1-1_i386.deb) ... 
Selecting previously deselected package wordnet-sense-index. 
Unpacking wordnet-sense-index (from .../wordnet-sense-index_1%3a3.0-23ubuntu1_all.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_ZA.UTF8.cache... 
Processing triggers for python-support ... 
Setting up man-db (2.5.7-4) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up samba (2:3.5.4~dfsg-1ubuntu8.3) ... 
No apport report written because MaxReports is reached already
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing samba (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of system-config-samba: 
 system-config-samba depends on samba; however: 
  Package samba is not configured yet. 
dpkg: error processing system-config-samba (--configure): 
 dependency problems - leaving unconfigured 
Setting up wordnet-base (1:3.0-23ubuntu1) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Setting up wordnet (1:3.0-23ubuntu1) ... 
Setting up artha (1.0.1-1) ... 
Setting up wordnet-sense-index (1:3.0-23ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 man-db 
 samba 
 system-config-samba 
Setting up samba (2:3.5.4~dfsg-1ubuntu8.3) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing samba (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up man-db (2.5.7-4) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of system-config-samba: 
 system-config-samba depends on samba; however: 
  Package samba is not configured yet. 
dpkg: error processing system-config-samba (--configure): 
 dependency problems - leaving unconfigured 


Any ideas?

---

### Post by ajgreeny on 2011-03-23
Try using the command line ```
sudo apt-get install -f
```which may fix any broken packages you have.  If that is no good use ```
sudo dpkg --configure -a
```

---

### Post by misssarahdee on 2011-03-23
Thanks. After I read some other threads, I tried that a few times - didn't work. After you suggested it, I gave it one last go, and it WORKED! You must have the magic touch.

Thanks. :)

---

