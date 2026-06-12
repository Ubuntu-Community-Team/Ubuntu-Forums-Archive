---
title: "Fatal error while upgrading from 12.10 to 13.10"
date: 2014-02-21
forum: Installation &amp; Upgrades
---

### Post by Prama on 2014-02-21
I tried upgrading today and this is what i got. 

Errors were encountered while processing:

 python3-plainbox  
 python3-checkbox-ng  
 checkbox-ng  
 checkbox-ng-service  
 checkbox-gui   
 checkbox-qt  
 ubuntu-desktop  
Error in function:   

A fatal error occurred 

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade has aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 


			
(apport-gtk:18799): IBUS-WARNING **: The owner of /home/panand200/.config/ibus/bus is not root!
													
I am not sure how to fix this. 
Can I just remove the packages mentioned above? Ubuntu-desktop! 
I don't know what state my machine is in, I am sort of scared about rebooting. 
What happens when your upgrade fails midway? Can i start again??


The errors messages  

got an error from dpkg for pkg: 'python3-plainbox': 'subprocess installed post-installation script returned error exit status 3'

2014-02-21 08:28:42,282 WARNING Failed to determine apport version (No module named pyexpat)  
2014-02-21 08:28:42,982 ERROR got an error from dpkg for pkg: 'python3-checkbox-ng': 'dependency problems - leaving unconfigured'  
2014-02-21 08:28:43,024 DEBUG running apport_pkgfailure() python3-checkbox-ng: dependency problems - leaving unconfigured  
2014-02-21 08:28:43,125 ERROR got an error from dpkg for pkg: 'checkbox-ng': 'dependency problems - leaving unconfigured'  
2014-02-21 08:28:43,125 DEBUG running apport_pkgfailure() checkbox-ng: dependency problems - leaving unconfigured  
2014-02-21 08:28:43,225 ERROR got an error from dpkg for pkg: 'checkbox-ng-service': 'dependency problems - leaving unconfigured'  
2014-02-21 08:28:43,225 DEBUG running apport_pkgfailure() checkbox-ng-service: dependency problems - leaving unconfigured  
2014-02-21 08:28:53,185 ERROR got an error from dpkg for pkg: 'checkbox-gui': 'dependency problems - leaving unconfigured'  
2014-02-21 08:28:53,186 DEBUG running apport_pkgfailure() checkbox-gui: dependency problems - leaving unconfigured  
2014-02-21 08:28:53,286 ERROR got an error from dpkg for pkg: 'checkbox-qt': 'dependency problems - leaving unconfigured'  
2014-02-21 08:28:53,286 DEBUG running apport_pkgfailure() checkbox-qt: dependency problems - leaving unconfigured  
2014-02-21 08:37:26,894 ERROR got an error from dpkg for pkg: 'ubuntu-desktop': 'dependency problems - leaving unconfigured'  
2014-02-21 08:37:27,000 DEBUG running apport_pkgfailure() ubuntu-desktop: dependency problems - leaving unconfigured  
2014-02-21 08:50:37,970 ERROR not handled exception:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)  

2014-02-21 08:50:39,045 DEBUG enabling apt cron job  
2014-02-21 08:50:50,000 ERROR SystemError from cache.commit(): installArchives() failed


Any help would be appreciated!!
Thanks!

---

### Post by frank18 on 2014-02-21
You can't upgrade from 12.10 to 13.10 you have to go to 1304 first

---

### Post by Bucky Ball on 2014-02-21
> **frank18 said:**
> You can't upgrade from 12.10 to 13.10 you have to go to 1304 first

Yes. Please explain how you did the upgrade. Do you mean you did a clean install of 13.10?

---

