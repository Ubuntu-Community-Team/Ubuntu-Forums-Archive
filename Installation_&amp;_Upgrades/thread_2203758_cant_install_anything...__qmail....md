---
title: "cant install anything...?  qmail...?"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by tasman35 on 2014-02-04
Evey time i try to install anything  i get this.....notsure how to fix it....?

installArchives() failed: Selecting previously unselected package dynamips. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 264284 files and directories currently installed.) 
Unpacking dynamips (from .../dynamips_0.2.7-0.2.8RC2-5ubuntu1_i386.deb) ... 
Selecting previously unselected package gns3. 
Unpacking gns3 (from .../archives/gns3_0.7.4-1_all.deb) ... 
Processing triggers for man-db ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Setting up qmail (1.06-4) ... 
 
The hostname -f command returned: $1 
 
Your system needs to have a fully qualified domain name (fqdn) in 
order to install the var-qmail packages. 
 
Installation aborted. 
 
dpkg: error processing qmail (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of qmail-run: 
 qmail-run depends on qmail (>= 1.06-2.1); however: 
  Package qmail is not configured yet. 
dpkg: error processing qmail-run (--configure): 
 dependency problems - leaving unconfigured 
Setting up dynamips (0.2.7-0.2.8RC2-5ubuntu1) ... 
No apport report written because MaxReports is reached already
Setting up gns3 (0.7.4-1) ... 
 
Creating config file /etc/gns3/gns3.ini with new version 
Errors were encountered while processing: 
 qmail 
 qmail-run 
Setting up qmail (1.06-4) ... 
 
The hostname -f command returned: $1 
 
Your system needs to have a fully qualified domain name (fqdn) in 
order to install the var-qmail packages. 
 
Installation aborted. 
 
dpkg: error processing qmail (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of qmail-run: 
 qmail-run depends on qmail (>= 1.06-2.1); however: 
  Package qmail is not configured yet.

---

### Post by Ubi_one_2014 on 2014-02-04
as is says, [COLOR=#000000]Your system needs to have a fully qualified domain name (fqdn) in [/COLOR]
[COLOR=#000000]order to install the var-qmail packages. [/COLOR]

---

### Post by tasman35 on 2014-02-05
BUt the thing is im not trying to set up a email server...IS unbuntu useing qmail as some kind of handler to get-apt or something

---

### Post by Ubi_one_2014 on 2014-02-05
it seems so...

did you recently remove postfix and or sendmail.

for some reasons linux always wants a mailserver installed

try:
sudo apt-get install ssmtp

that will install an very simple smtp server, handy to use for localmails in order to know what happend on your system

---

### Post by tasman35 on 2014-02-05
thanks i tried to install ssmtp but it wont let me install it keeps coming back to qmail....? os i rm -rf qmail...done...I thinklol

---

### Post by tasman35 on 2014-02-05
Now after reboot it wont load anything....wth.....I cant keep unbuntu running on this box to save my life.....all the updates keeps messing with my install....I just dont getit...
:-k Now it wont even see that bootload....

---

### Post by Ubi_one_2014 on 2014-02-06
any updates regarding this problem?

---

