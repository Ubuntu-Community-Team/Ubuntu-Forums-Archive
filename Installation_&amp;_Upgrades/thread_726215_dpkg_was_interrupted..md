---
title: "dpkg was interrupted."
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by Kevin Jones on 2008-03-16
Hello all
I recently downloaded, fresh install on a clean partition, Xubuntu 7.10

the install went well.
I tried to install some extra packages and this was returned:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I ran:
sudo dpkg--configure -a
This was returned:
   A new version of configuration file /etc/samba/smb.conf is available,   
  &#9474; but the version installed currently has been locally modified.          
  &#9474;                                                                         
  &#9474; What would you like to do about smb.conf?                               
  &#9474;                                                                        
  &#9474;           install the package maintainer's version                      
  &#9474;           keep the local version currently installed                   
  &#9474;           show the differences between the versions                     
  &#9474;           show a side-by-side difference between the versions           
  &#9474;           start a new shell to examine the situation                    
  &#9474;                                                                         
  I chose     option 'C; and this was returned:

      Line by line differences between versions                                 &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; --- /etc/samba/smb.conf 2008-03-16 12:20:38.000000000 -0500               &#9618; 
 &#9474; +++ /var/run/samba/upgrades/smb.conf 2008-03-16 12:20:38.362097348 -0500  &#9618; 
 &#9474; @@ -66,7 +66,7 @@                                                         &#9618; 
 &#9474;  # that connects                                                          &#9618; 
 &#9474;  log file = /var/log/samba/log.%m                                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; -# Cap the size of the individual log files (in KiB).                     &#9618; 
 &#9474; +# Put a capping on the size of the log files (in Kb).                    &#9618; 
 &#9474;  max log size = 1000                                                      &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474;  # If you want Samba to only log through syslog then set the following    &#9618; 
 &#9474; @@ -169,6 +169,12 @@                


At this point I am totally out of my deptth. I have read previous postings on this subject and I know one possible solution is to run this command:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

Given the above information can any tell me if this is my option?
This was a fresh install, I am bit confoosed about the two packages being different.
If all else fails I will run this:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

Kevin

---

### Post by Pumalite on 2008-03-16
B.-Keep the version currently installed.

---

### Post by Kevin Jones on 2008-03-16
HI alll
thanks to you pumalite
I chose option to keep local version and the process is running.
Problem solved
Close case
Thanks

Kevin Jones

---

### Post by Pumalite on 2008-03-16
You are welcome. Good luck.

---

