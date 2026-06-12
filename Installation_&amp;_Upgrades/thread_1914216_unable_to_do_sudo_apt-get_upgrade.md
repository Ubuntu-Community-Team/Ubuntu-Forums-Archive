---
title: "unable to do sudo apt-get upgrade"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by gsadikin on 2012-01-23
I get the following error message when doing upgrade.

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/dpkg_1.14.16.6ubuntu4.2_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `dnsutils': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.14.16.6ubuntu4.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried apt-get clean, apt-get update, apt-get upgrade again, but i still get the same error message.

I have also tried to do apt-get -f upgrade.

How can I fix this?

---

### Post by WthIteh on 2012-01-24
Run in terminal "aptitude" or open "synaptic".
Without trying to upgrade anything, fix all broken packages (in aptitude read red messages in bottom of page and in synaptic there is a menu entry for doing that).
When there was no broken packages at all, update and then upgrade.

---

### Post by raja.genupula on 2012-01-24
> **gsadikin said:**
> I get the following error message when doing upgrade.

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/dpkg_1.14.16.6ubuntu4.2_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `dnsutils': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.14.16.6ubuntu4.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried apt-get clean, apt-get update, apt-get upgrade again, but i still get the same error message.

I have also tried to do apt-get -f upgrade.

How can I fix this?
First do this things one by one in your terminal

```
sudo dpkg --configure -a
sudo apt-get install -f
```

if the problem still there then Remove that file from the archives and try again.
I hope that gonna be fine .

---

### Post by gsadikin on 2012-01-24
There is no red message in bottom of my aptitude page.

I have run
sudo dpkg --configure -a
sudo apt-get install -f
and I still get the same error when I do upgrade

removing everything in /var/cache/apt/archives/ folder, then update and upgrade doesn't fix it either..

I should also mention that I removed the files in /var/lib/dpkg/updates/ folder as it was giving me error messages when I do sudo apt-get update. I couldn't remember the message but I read from a forum that I should remove the files in that folder to fix it.

---

### Post by raja.genupula on 2012-01-24
we need terminal output of **sudo apt-get update** , could you please provide ?

---

### Post by gsadikin on 2012-01-24
sudo apt-get update:
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy Release.gpg
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/main Translation-en_AU                    
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/restricted Translation-en_AU              
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/universe Translation-en_AU                
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/multiverse Translation-en_AU              
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates Release.gpg                       
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/main Translation-en_AU            
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/restricted Translation-en_AU      
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/universe Translation-en_AU        
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/multiverse Translation-en_AU      
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy Release                                   
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates Release                           
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/main Packages                             
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/restricted Packages                       
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/main Sources                              
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/restricted Sources                        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/universe Packages                         
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/universe Sources                          
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/multiverse Packages                       
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy/multiverse Sources                        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/main Packages                     
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/restricted Packages               
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/main Sources                      
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/restricted Sources                
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/universe Packages                 
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/universe Sources                  
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/multiverse Packages               
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) hardy-updates/multiverse Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_AU        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_AU  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_AU                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_AU    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_AU  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                  
Ign ssh://twrepo@rc-gloucesterpark.dyndns.org hardy/ Release.gpg            
Ign ssh://twrepo@rc-gloucesterpark.dyndns.org hardy/ Translation-en_AU      
Ign ssh://twrepo@rc-gloucesterpark.dyndns.org alpha/ Release.gpg            
Ign ssh://twrepo@rc-gloucesterpark.dyndns.org alpha/ Translation-en_AU
Ign ssh://twrepo@rc-gloucesterpark.dyndns.org hardy/ Release
Ign ssh://twrepo@rc-gloucesterpark.dyndns.org alpha/ Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                            
Ign ssh://twrepo@rc-gloucesterpark.dyndns.org hardy/ Packages               
Ign ssh://twrepo@rc-gloucesterpark.dyndns.org alpha/ Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                             
Hit ssh://twrepo@rc-gloucesterpark.dyndns.org hardy/ Packages               
Hit ssh://twrepo@rc-gloucesterpark.dyndns.org alpha/ Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Reading package lists... Done

---

### Post by raja.genupula on 2012-01-24
now try to do upgrade and if any error again occurs post the out put here .

---

### Post by gsadikin on 2012-01-31
I have this fixed by running
sudo touch /forcefsck
then after reboot, I run fsck

I was referring to this post:
[http://ubuntuforums.org/showthread.php?t=352766](http://ubuntuforums.org/showthread.php?t=352766)

---

### Post by bilor on 2012-05-18
None of this worked until I found this thread:
[http://ubuntuforums.org/archive/index.php/t-1625789.html](http://ubuntuforums.org/archive/index.php/t-1625789.html)
**sudo dpkg --clear-avail**
Now I am happy again.

---

