---
title: "upgrading server from 7.10 to latest LTS"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2013-05-08
I have been running a server for the past 5 years (?) using 7.10 Server without GUI. I haven't had any real issues, except that web crawlers are bogging my system down to a crawl. I found through searching that I can install the bw module for apache2 to limit bandwidth, but I need a higher version Ubuntu to do that. 

Since this is a webserver with forums, a fresh install really isn't an option. I cannot upgrade using 'apt-get dist-upgrade' - it says the system IS up to date.  I tried downloading the 8.04LTS server alternate CD, but there is no option to upgrade, only to install. I dropped to the command line (ESC since ALT-F2 does nothing) and tried to run 'gksu "sh /cdrom/cdromupgrade"' as directed here - [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades) - but that results in the error message "could not find kernel image: gksu". Actually, it tells me that for EVERY command I try, including ls. 

I assume that I can't upgrade from 7.10 to 12.10LTS directly, so can someone please help? I would really appreciate it - as would my network!

---

### Post by Frogs Hair on 2013-05-08
The following is from Ask Ubuntu and may give some direction. Manually adding the 12.04 repository software sources maybe  possible, but have no idea if it would work. Installing 12.04 server on a different partition come to mind but would still require a change over. 

Ask Ubuntu


[http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)




[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)




f you want to continue using an outdated release then edit /etc/apt/sources.list and change archive.ubuntu.com to old-releases.ubuntu.com


You can do this with sed


sudo sed -i -e 's/archive.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
then update with


sudo apt-get update && sudo apt-get dist-upgrade source


See also:


[https://help.ubuntu.com/community/EOLUpgrades/](https://help.ubuntu.com/community/EOLUpgrades/)
shareimp

---

### Post by rebeltaz on 2013-05-08
My sources.list is already set to old-releases.ubuntu.com ... 'apt-get update' tells me that it is ignoring those packages as they have failed to download.

---

### Post by rebeltaz on 2013-05-09
I figured out to try to run the cdromupgrade script from within my old terminal (I had been trying to boot from the CD then run the upgrade). I mounted the CDROM, ran the cdromupgrade script and was presented with a "Could not calculate the upgrade" error. The image that I am trying to upgrade to is 8.04LTS. I have tried both the Server as well as the Alternate versions. I figured I needed to upgrade in steps, but I tried running the upgrade script on the 10.04LTS disc anyway and that failed just because it isn't supported.

I really need help here guys!!! Please and thanks...

---

### Post by rebeltaz on 2013-05-10
After much fiddling, I finally got the online upgrade to work. It happily upgraded 7.10 to 8.04LTS and then from 8.04LTS to 10.04LTS. That is when the problems started.

After rebooting following the 10.04LTS upgrade, the system failed to boot, complaining that one of the drives being requested for mount in fstab was unavailable. I did a little digging and found that the UUID for the swap drive (sda5) had for some reason changed during the upgrade. I found that and edited the fstab file and all seemed happy. apache is running, ssh is running, mysql seems to be running and entact (since the forums still work), but...

proftpd was removed as was ispconfig. 

I reinstalled proftpd, but I have no clue how ispconfig had set it up to access the different directories. I also tried starting proftpd with it's default configuration, but it complained that "Fatal: LoadModule: error loading module 'mod_ldap.c': Permission denied on line 18 of '/etc/proftpd/modules.conf'"

I am scared to try to reinstall ispsconfig because I am afraid that it will screw up the servers that are for the moment working. 

Can someone help me figure out how to reinstall proftpd to at least one of the websites and I can figure the rest out myself? As usual, I would really appreciate any help anyone can offer. Thanks...

---

### Post by rebeltaz on 2013-05-10
Never mind... I uninstalled proftpd AGAIN with purge this time and the reinstalled it. Everything seems to be working... so... Thanks.

---

