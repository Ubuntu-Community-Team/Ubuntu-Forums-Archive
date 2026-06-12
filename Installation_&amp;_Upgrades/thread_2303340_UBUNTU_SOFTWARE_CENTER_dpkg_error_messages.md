---
title: "UBUNTU SOFTWARE CENTER dpkg error messages"
date: 2015-11-18
forum: Installation &amp; Upgrades
---

### Post by juliancyh on 2015-11-18
Hi. 
I have this error message from UBUNTU SOFTWARE CENTER that does not go away and affects my ability to install other applications.
I tried manually purging the application installation but the error msg still persist.     
How do I resolved these dpkg errors?

Thanks.

> installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 230449 files and directories currently installed.)
Preparing to unpack .../libfreetype6-dev_2.5.2-4ubuntu2_amd64.deb ...
Unpacking libfreetype6-dev:amd64 (2.5.2-4ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/libfreetype6-dev_2.5.2-4ubuntu2_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/man/man1/freetype-config.1.gz', which is different from other instances of package libfreetype6-dev:amd64
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for doc-base (0.10.6) ...
Processing triggers for man-db (2.7.4-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libfreetype6-dev_2.5.2-4ubuntu2_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of libfontconfig1-dev:amd64:
 libfontconfig1-dev:amd64 depends on libfreetype6-dev (>= 2.1.7); however:
  Package libfreetype6-dev:amd64 is not installed.


dpkg: error processing package libfontconfig1-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libfontconfig1-dev (>= 2.2.95); however:
  Package libfontconfig1-dev:amd64 is not configured yet.
 libcairo2-dev depends on libfreetype6-dev (>= 2.1.10); however:
  Package libfreetype6-dev:amd64 is not installed.


dpkg: error processing package libcairo2-dev (--configure):
 dependency problems - leaving unconfigured


---

### Post by ajgreeny on 2015-11-18
Try deleting the package that is apparently causing the problem you are seeing with ```
sudo rm /var/cache/apt/archives/libfreetype6-dev_2.5.2-4ubuntu2_amd64.deb
``` or even close software-centre and  run command ```
sudo apt-get clean
``` to remove all packages from the cache.

You may then need to run ```
sudo apt-get install -f
sudo dpkg --configure -a
```to fix any broken packages and configure anything left unconfigured as a result of the errors.

---

### Post by juliancyh on 2015-11-18
Thanks ajgreeny.

I ran "sudo apt-get clean" and "sudo apt-get install -f".
The latter command listed the packages that were automatically installed and are no longer required and suggest I use "apt-get autoremove" to remove them. 
I did that and finished off with "sudo dpkg --configure -a".
I am able to install other applications.

---

### Post by ajgreeny on 2015-11-18
Brilliant!

Please mark as SOLVED from the Thread Tools menu at the top.

Marked as SOLVED on your behalf.

---

