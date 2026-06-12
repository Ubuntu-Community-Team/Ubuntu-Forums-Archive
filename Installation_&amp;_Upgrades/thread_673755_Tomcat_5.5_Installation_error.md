---
title: "Tomcat 5.5 Installation error"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by aravinda_sh on 2008-01-21
Hi,
I tried installing Tomcat 5.5 and I am getting the following errors.
Errors were encountered while processing:
 tomcat5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can any one help how to resolve this issue.

I tried deleting 
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure --a
sudo dpkg --configure --pending

Then I got the following errors


Setting up tomcat5.5 (5.5.25-1ubuntu1) ...
 * Starting Tomcat servlet engine tomcat5.5                                     cat: /etc/tomcat5.5/policy.d/*.policy: No such file or directory
invoke-rc.d: initscript tomcat5.5, action "start" failed.
dpkg: error processing tomcat5.5 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tomcat5.5-webapps:
 tomcat5.5-webapps depends on tomcat5.5 (>= 5.5.25-1ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-webapps (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tomcat5.5

Please can any one guide me to resolve this. 

Thank you
Aravinda

---

