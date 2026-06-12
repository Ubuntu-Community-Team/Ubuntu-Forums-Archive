---
title: "Upgrade to 13.10 failed on squid3 install"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by graham45 on 2013-10-18
Hi  - the upgrade fell over on squid3 - the error was fatal and the upgrade exit'ed.  I tried running the update tool but it just told me that 13.10 was installed.  I rebooted the system and after quite a few errors on boot it started and seems to be going ok. I probably need a manual method to complete the upgrade.  Obviously some packages will be not set up and the cleanup was not run !  Any ideas would be appreciated.  I will be checking for manual update commands also, but I am not greatly familiar with its capabilities.  Thanks.  Oh, I have run apt-get update  and apt-get dist-upgrade with no effect.

---

### Post by heir4c on 2013-10-18
What is the output of the sudo apt-get update and sudo apt-get dist-upgrade?

---

### Post by graham45 on 2013-10-19
Hi    output from apt-get update follows....

root@graham-desktop:~# apt-get update
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy InRelease
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates InRelease                                       
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security InRelease                                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy Release.gpg                                             
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates Release.gpg [933 B]                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security Release.gpg                                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy Release                                                 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                      
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates Release [49.6 kB]                             
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security Release                                     
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/main i386 Packages                                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/restricted i386 Packages       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/universe i386 Packages         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/multiverse i386 Packages       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/main Translation-en_AU         
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                           
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/main Translation-en            
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/multiverse Translation-en_AU                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/multiverse Translation-en      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/restricted Translation-en_AU   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/restricted Translation-en                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/universe Translation-en_AU     
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages          
Hit [http://dl.google.com](http://dl.google.com) stable Release                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy/universe Translation-en                               
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/main i386 Packages [5,477 B]                
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]               
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/universe i386 Packages [1,301 B]              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                                          
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [14 B]            
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                        
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/main Translation-en [2,396 B]                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/multiverse Translation-en                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/restricted Translation-en                    
Get:9 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/universe Translation-en [482 B]            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/main i386 Packages                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/restricted i386 Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/universe i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/multiverse i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/main Translation-en   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/multiverse Translation-en
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/restricted Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en_AU                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_AU                                   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/main Translation-en_AU 
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/multiverse Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/restricted Translation-en_AU
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/multiverse Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) saucy-security/universe Translation-en_AU
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                            
Fetched 60.3 kB in 7s (7,806 B/s)                                                              
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) saucy/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_saucy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


and output from apt-get dist-upgrade follows....

wait  - that command is doing something more substantial than yesterday....i will get back
it is loading and setting up a dozen or two packages  ie

root@graham-desktop:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  google-chrome-stable
The following packages will be upgraded:
  gir1.2-gudev-1.0 gir1.2-unity-5.0 libgudev-1.0-0 libpam-systemd libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libudev1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 systemd-services udev unity-scopes-runner
14 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 1,955 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main udev i386 204-0ubuntu19 [1,046 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main libudev1 i386 204-0ubuntu19 [37.2 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main libsystemd-daemon0 i386 204-0ubuntu19 [8,742 B]
Get:4 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main libpam-systemd i386 204-0ubuntu19 [25.7 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main systemd-services i386 204-0ubuntu19 [344 kB]
Get:6 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main libsystemd-login0 i386 204-0ubuntu19 [27.8 kB]
Get:7 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main libgudev-1.0-0 i386 1:204-0ubuntu19 [14.2 kB]
Get:8 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main libunity-scopes-json-def-desktop all 7.1.2+13.10.20131010-0ubuntu2 [3,792 B]
Get:9 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main libunity-protocol-private0 i386 7.1.2+13.10.20131010-0ubuntu2 [98.7 kB]
Get:10 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main libunity9 i386 7.1.2+13.10.20131010-0ubuntu2 [259 kB]
Get:11 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main libsystemd-journal0 i386 204-0ubuntu19 [59.8 kB]
Get:12 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main gir1.2-gudev-1.0 i386 204-0ubuntu19 [3,622 B]
Get:13 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main gir1.2-unity-5.0 i386 7.1.2+13.10.20131010-0ubuntu2 [21.4 kB]
Get:14 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) saucy-updates/main unity-scopes-runner all 7.1.2+13.10.20131010-0ubuntu2 [4,296 B]
Fetched 1,955 kB in 6s (300 kB/s)                                                              
(Reading database ... 679812 files and directories currently installed.)
Preparing to replace udev 204-0ubuntu18 (using .../udev_204-0ubuntu19_i386.deb) ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Preparing to replace libudev1:i386 204-0ubuntu18 (using .../libudev1_204-0ubuntu19_i386.deb) ...
Unpacking replacement libudev1:i386 ...
Preparing to replace libsystemd-daemon0:i386 204-0ubuntu18 (using .../libsystemd-daemon0_204-0ubuntu19_i386.deb) ...
Unpacking replacement libsystemd-daemon0:i386 ...
Preparing to replace libpam-systemd:i386 204-0ubuntu18 (using .../libpam-systemd_204-0ubuntu19_i386.deb) ...
Unpacking replacement libpam-systemd:i386 ...
Preparing to replace systemd-services 204-0ubuntu18 (using .../systemd-services_204-0ubuntu19_i386.deb) ...
Unpacking replacement systemd-services ...
Preparing to replace libsystemd-login0:i386 204-0ubuntu18 (using .../libsystemd-login0_204-0ubuntu19_i386.deb) ...
Unpacking replacement libsystemd-login0:i386 ...
Preparing to replace libgudev-1.0-0:i386 1:204-0ubuntu18 (using .../libgudev-1.0-0_1%3a204-0ubuntu19_i386.deb) ...
Unpacking replacement libgudev-1.0-0:i386 ...
Preparing to replace libunity-scopes-json-def-desktop 7.1.2+13.10.20131010-0ubuntu1 (using .../libunity-scopes-json-def-desktop_7.1.2+13.10.20131010-0ubuntu2_all.deb) ...
Unpacking replacement libunity-scopes-json-def-desktop ...
Preparing to replace libunity-protocol-private0:i386 7.1.2+13.10.20131010-0ubuntu1 (using .../libunity-protocol-private0_7.1.2+13.10.20131010-0ubuntu2_i386.deb) ...
Unpacking replacement libunity-protocol-private0:i386 ...
Preparing to replace libunity9:i386 7.1.2+13.10.20131010-0ubuntu1 (using .../libunity9_7.1.2+13.10.20131010-0ubuntu2_i386.deb) ...
Unpacking replacement libunity9:i386 ...
Preparing to replace libsystemd-journal0:i386 204-0ubuntu18 (using .../libsystemd-journal0_204-0ubuntu19_i386.deb) ...
Unpacking replacement libsystemd-journal0:i386 ...
Preparing to replace gir1.2-gudev-1.0 204-0ubuntu18 (using .../gir1.2-gudev-1.0_204-0ubuntu19_i386.deb) ...
Unpacking replacement gir1.2-gudev-1.0 ...
Preparing to replace gir1.2-unity-5.0:i386 7.1.2+13.10.20131010-0ubuntu1 (using .../gir1.2-unity-5.0_7.1.2+13.10.20131010-0ubuntu2_i386.deb) ...
Unpacking replacement gir1.2-unity-5.0:i386 ...
Preparing to replace unity-scopes-runner 7.1.2+13.10.20131010-0ubuntu1 (using .../unity-scopes-runner_7.1.2+13.10.20131010-0ubuntu2_all.deb) ...
Unpacking replacement unity-scopes-runner ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libglib2.0-0:i386 ...
Setting up libudev1:i386 (204-0ubuntu19) ...
Setting up udev (204-0ubuntu19) ...
udev stop/waiting
udev start/running, process 6184
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up libsystemd-daemon0:i386 (204-0ubuntu19) ...
Setting up systemd-services (204-0ubuntu19) ...
Setting up libpam-systemd:i386 (204-0ubuntu19) ...
Setting up libsystemd-login0:i386 (204-0ubuntu19) ...
Setting up libgudev-1.0-0:i386 (1:204-0ubuntu19) ...
Setting up libunity-scopes-json-def-desktop (7.1.2+13.10.20131010-0ubuntu2) ...
Setting up libunity-protocol-private0:i386 (7.1.2+13.10.20131010-0ubuntu2) ...
Setting up libunity9:i386 (7.1.2+13.10.20131010-0ubuntu2) ...
Setting up libsystemd-journal0:i386 (204-0ubuntu19) ...
Setting up gir1.2-gudev-1.0 (204-0ubuntu19) ...
Setting up gir1.2-unity-5.0:i386 (7.1.2+13.10.20131010-0ubuntu2) ...
Setting up unity-scopes-runner (7.1.2+13.10.20131010-0ubuntu2) ...
Processing triggers for libc-bin ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-12-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

looks promising...

---

### Post by heir4c on 2013-10-19
Now it must be full upgraded, so it's resolved the problem.
Only google-chrome is not upgraded but that will be done in the future I think:

> The following packages have been kept back:
google-chrome-stable

---

### Post by graham45 on 2013-10-19
Problem is on reboot there is quite a number of errors - it appears as though some packages near the end of the upgrade didnt get set up correctly.  Well it is working ok in general - I cant see any problems once its up - except for squid3 of course - tried installing it with apt-get and came up with errors so http caching isnt working but I have switched that off anyway.   Thanks for your input.  I will sweep the net for similar problems.   I dont really want to do a fresh install !

---

### Post by graham45 on 2013-10-20
For those that may be interested the upgrade may have failed because install of  squid failed.....I have tried reinstalling/removing squid etc sev times with no result.
I checked the /etc/squid dir for squid.conf  and found 2 versions.    The upgrade asked me whether to keep the existing script or not.  
I had asked for the existing script to be retained. So i manually swapped the new version in place of the old.  Squid(3) installed perfectly following that.  
That appears to be the cause of the upgrade failure.

---

### Post by graham45 on 2013-10-22
Problem tracked down - looks as though nothing wrong with the system as such except for a problem with udev package, which caused several pages of errors on bootup.  The service giving the problem was  systemd-udevd  and I found a reference to this issue on the net suggesting that purging package  hal  would fix the issue.  ie  no more errors on bootup so    apt-get purge hal    and no more errors.  I am not convinced everything is 100% however but cant be too much wrong now. Anyway no more errors on bootup. :-)

---

