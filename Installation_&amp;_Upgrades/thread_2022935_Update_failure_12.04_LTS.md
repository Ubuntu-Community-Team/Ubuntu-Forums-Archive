---
title: "Update failure 12.04 LTS"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by jlapinski4 on 2012-07-11
Errors were encountered while processing: 
 qmail 
 qmail-run 
Error in function:  
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
dpkg: error processing qmail-run (--configure): 
 dependency problems - leaving unconfigured 

I get this error message every time I attempt to install updates regardless of using software manager or terminal.

Any ideas?

Thank you!

---

### Post by jlapinski4 on 2012-07-11
Actually I fixed the update error by unlocking the packages in the terminal.  I am trying to install a program named Moneydance and each time I get the following error:

Unpacking moneydance (from /tmp/moneydance.deb) ... 
Setting up moneydance (2011.803) ... 
Preparing JRE ... 
/var/lib/dpkg/info/moneydance.postinst: 22: /var/lib/dpkg/info/moneydance.postinst: bin/unpack200: not found 
Error unpacking jar files. Aborting. 
dpkg: error processing moneydance (--install): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 moneydance

Any suggestions are appreciated!

---

### Post by Cheesehead on 2012-07-11
> **jlapinski4 said:**
> 
/var/lib/dpkg/info/moneydance.postinst: 22: /var/lib/dpkg/info/moneydance.postinst: bin/unpack200: not found

The Moneydance postinstall script seems to be looking for a file bin/unpack200 but cannot find it.
Normally that file is provided by your Java Runtime Environment (JRE)
Do you have a JRE installed?

---

### Post by jlapinski4 on 2012-07-11
> **Cheesehead said:**
> The Moneydance postinstall script seems to be looking for a file bin/unpack200 but cannot find it.
Normally that file is provided by your Java Runtime Environment (JRE)
Do you have a JRE installed?


I followed the steps to install java 7 but it is entirely possible that I made an error doing that.

---

