---
title: "Flash player problem."
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by Steinway05 on 2009-11-18
I am new to linux (installed Ubuntu 9.10 two days  to get flash player 10. So I went to the flash site and downloaded the .deb file for flash. When I run this file I get this message. > Error: Dependency is not satisfiable: libnspr4-devI have tryed using terminal to fix this using suggestions on your forums with no luck. Examples: ```
alex@alex-laptop:~$ sudo aptitude install libnspr4-dev libnss3-dev ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No candidate version found for libnspr4-dev
No candidate version found for libnss3-dev
Couldn't find any package whose name or description matched "ubuntu-restricted-extras"
No candidate version found for libnspr4-dev
No candidate version found for libnss3-dev
Couldn't find any package whose name or description matched "ubuntu-restricted-extras"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

``````

alex@alex-laptop:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
``````
alex@alex-laptop:~$ sudo aptitude update
Err http://au.archive.ubuntu.com karmic Release.gpg                             
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://au.archive.ubuntu.com karmic/main Translation-en_AU                  
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://au.archive.ubuntu.com karmic/restricted Translation-en_AU            
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://au.archive.ubuntu.com karmic/universe Translation-en_AU              
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://au.archive.ubuntu.com karmic/multiverse Translation-en_AU            
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://au.archive.ubuntu.com karmic-updates Release.gpg                     
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://au.archive.ubuntu.com karmic-updates/main Translation-en_AU          
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://au.archive.ubuntu.com karmic-updates/restricted Translation-en_AU    
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://au.archive.ubuntu.com karmic-updates/universe Translation-en_AU      
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://au.archive.ubuntu.com karmic-updates/multiverse Translation-en_AU    
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err http://security.ubuntu.com karmic-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (32.1.3.136), connection timed out
Err http://security.ubuntu.com karmic-security/main Translation-en_AU           
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com karmic-security/restricted Translation-en_AU     
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com karmic-security/universe Translation-en_AU       
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com karmic-security/multiverse Translation-en_AU     
  Unable to connect to security.ubuntu.com http:
Err http://switch.dl.sourceforge.net all Release.gpg                            
  Cannot initiate the connection to switch.dl.sourceforge.net:80 (2001:620:0:1b::21). - connect (101: Network is unreachable) [IP: 2001:620:0:1b::21 80]
Err http://switch.dl.sourceforge.net all/main Translation-en_AU                 
  Cannot initiate the connection to switch.dl.sourceforge.net:80 (2001:620:0:1b::21). - connect (101: Network is unreachable) [IP: 2001:620:0:1b::21 80]
Reading package lists... Done  
``````
alex@alex-laptop:~$ sudo aptitude dist-upgrade
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
``````
alex@alex-laptop:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin
``````

alex@alex-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``````
alex@alex-laptop:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin
alex@alex-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alex@alex-laptop:~$ sudo dpkg --force-all -r adobe-flashplugin
dpkg: warning: ignoring request to remove adobe-flashplugin which isn't installed.
alex@alex-laptop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin
alex@alex-laptop:~$ 
``````
alex@alex-laptop:~$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
rm: cannot remove `/var/lib/dpkg/info/adobe-flashplugin.prerm': No such file or directory
``````

alex@alex-laptop:~$ sudo dpkg-reconfigure adobe-flashplugin --force
Package `adobe-flashplugin' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

``````

alex@alex-laptop:~$ sudo dpkg --purge --force-all adobe-flashplugin
dpkg: warning: ignoring request to remove adobe-flashplugin which isn't installed.
```
So yea...????

---

### Post by bmelendy on 2009-11-18
I have the same problem, can't install flash.  I did manually install the first dependency for libnspr4-dev, but then a second one for libnss3-dev says it doesn't exist??  Totally lost.  Would love to be able to see flash under Linux.

---

### Post by Steinway05 on 2009-11-19
I can't fix this, I've read so many posts and nothing has worked. =[.

---

### Post by bmelendy on 2009-11-19
Just found this bug reference, hoping it fixes the situation:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/444145](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/444145)

---

### Post by Steinway05 on 2009-11-19
> **bmelendy said:**
> Just found this bug reference, hoping it fixes the situation:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/444145](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/444145)


Thanks but it didn't help =[ could it be caused by installing 9.10 on a oldish laptop??

---

### Post by Steinway05 on 2009-11-19
Ok I just fixed it by playing with random settings =/ I wish I new what I did. It might have to do with using my partners internet.

---

### Post by bmelendy on 2009-11-19
Hmm...  you know my issues are running on an 'oldish' laptop as well.  I've got other issues like trying to install software and Ubuntu telling me that the software in question is not available for my architecture??  Maybe I'll try SUSE.  ;-)

---

