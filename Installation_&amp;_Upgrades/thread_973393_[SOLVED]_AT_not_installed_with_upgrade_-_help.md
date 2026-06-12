---
title: "[SOLVED] AT not installed with upgrade - help"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by socngill on 2008-11-06
When I was upgrading from 8.04 to 8.10 it came up saying it couldn't install AT  -I had never come across it before so just skipped it and carried on with the install.

Since the upgrade I have been unable to install any packages, and i think AT is to blame.  I get the following error message:

> root@Kubuntu:~# dpkg --configure -a
Setting up at (3.1.10.1ubuntu3) ...
 * Starting deferred execution scheduler atd                                    invoke-rc.d: initscript atd, action "start" failed.                             
dpkg: error processing at (--configure):                                        
 subprocess post-installation script returned error exit status 1               
dpkg: dependency problems prevent configuration of ubuntu-standard:             
 ubuntu-standard depends on at; however:                                        
  Package at is not configured yet.                                             
dpkg: error processing ubuntu-standard (--configure):                           
 dependency problems - leaving unconfigured                                     
Errors were encountered while processing:                                       
 at                                                                             
 ubuntu-standard      

So i tried to install AT and got the following:

> root@Kubuntu:~# sudo apt-get install at                                         
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
at is already the newest version.                                               
The following packages were automatically installed and are no longer required: 
  libopencdk10-dev gstreamer0.10-alsa libopenal0a libgnutlsxx13 python-pexpect  
  libdc1394-13 python-twisted-web libwxgtk2.6-0 libgfortran2 g++-4.2            
  python-pycurl libmp4v2-0 gfortran-4.2-multilib libamrnb3 lib64gfortran2       
  libxosd2 libx264-57 libvlc0 libamrwb3 g++-4.2-multilib gfortran-4.2           
  gcc-4.2-multilib libwxbase2.6-0 xmms2-plugin-asf libswscale1d                 
  libstdc++6-4.2-dev liblzo2-dev vlc-plugin-pulse python-smartpm libg2c0        
  gcc-3.3-base                                                                  
Use 'apt-get autoremove' to remove them.                                        
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.                  
2 not fully installed or removed.                                               
After this operation, 0B of additional disk space will be used.                 
Setting up at (3.1.10.1ubuntu3) ...                                             
 * Starting deferred execution scheduler atd                                    invoke-rc.d: initscript atd, action "start" failed.                             
dpkg: error processing at (--configure):                                        
 subprocess post-installation script returned error exit status 1               
dpkg: dependency problems prevent configuration of ubuntu-standard:             
 ubuntu-standard depends on at; however:                                        
  Package at is not configured yet.                                             
dpkg: error processing ubuntu-standard (--configure):                           
 dependency problems - leaving unconfigured                                     
No apport report written because the error message indicates its a followup error from a previous failure.                                                      
                          Errors were encountered while processing:             
 at                                                                             
 ubuntu-standard                                                                
E: Sub-process /usr/bin/dpkg returned an error code (1)       

Every time I try to install something I get these error messages.  What should I do???

---

### Post by socngill on 2008-11-07
Anybody able to help with this problem?

---

### Post by socngill on 2008-11-07
I have had a quick google and it looks like this problem is quite common with upgrading from one version to the next, but I have not found any fix for it.

Am I going to have to reinstall 8.10 from scratch?  Or would deleting the /usr/bin/dpkg solve the problem (or compound it :D).  

Would really like some advice on this please and it is stopping me from installing or removing anything.

---

### Post by socngill on 2008-11-07
Bump

---

### Post by B34ST1Y on 2008-11-07
make sure you have your headers installed properly

---

### Post by socngill on 2008-11-08
> **B34ST1Y said:**
> make sure you have your headers installed properly

I'm going to sound like a simpleton, but how do I check that?  Or configure, reinstall them?

I know it tried doing an update yesterday which tried to install updated headers, but because of the AT problem I don't think it wa ssuccessful - it came up with an "error committing" message.

---

