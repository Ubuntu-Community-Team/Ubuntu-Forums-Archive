---
title: "Upgrading to 10.04- problems"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cest42 on 2010-03-27
I have a dual boot XP/Ubuntu machine courtesy of Wubi (Wonderful prog !). Current version of Ubuntu is 9.10 and I'd like to upgrade to 10.04 but this doesn't seem to be working. I use the Update Manager to start the process, it downloads 2 files (don't know names) and then reverts back to the desktop. There are no error messages or invitations to download other files. have done this twice now with the the same result. Does anyone have any ideas of what is going wrong ?

Steve

---

### Post by stlsaint on 2010-03-27
Technically you are not running a true dual boot considering that wubi is installed  "inside" of xp". 
In the terminal run this:
```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by cest42 on 2010-03-27
Thanks for that. I tried it and don't think I made much progress. 

Session finished like this:

steve@ubuntu:~$ sudo aptitude update &&& sudo aptitude safe-upgrade
bash: syntax error near unexpected token `&'
steve@ubuntu:~$ sudo aptitude update && sudo aptitude safe-upgrade
[sudo] password for steve: 
Writing extended state information... Done
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg                         
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB [63.7kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                    
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB [3,402B] 
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB [33.2kB]   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB [43.8kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Translation-en_GB     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Packages              
Fetched 144kB in 8s (17.0kB/s)                                                  
Reading package lists... Done             

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
The following packages will be REMOVED:
  binutils-static{u} linux-headers-2.6.31-16{u} 
  linux-headers-2.6.31-16-generic{u} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 83.5MB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 168571 files and directories currently installed.)
Removing binutils-static ...
Removing linux-headers-2.6.31-16-generic ...
Removing linux-headers-2.6.31-16 ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

and then back to a command prompt

Should I / Do I need to  upgrade Wubi first ?

---

### Post by stlsaint on 2010-03-27
Based off your output you have nothing to update. Are you wanting to do a upgrade to lucid?

---

### Post by cest42 on 2010-03-27
If Lucid is the name for 10.04 then yes. I currently have 9.10

Steve

---

### Post by fchaffin on 2010-03-27
I am trying to do the same thing as crest42 and I am having the same issues...

---

### Post by cest42 on 2010-03-30
I found another thread on here that lead me to another site with a solution that worked for me.

Link [http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html](http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html)

---

### Post by Slim Odds on 2010-03-30
Moving to a NEW pre-release is not an upgrade, but a dist-upgrade.

That's why you have to force the "-d" when using the update-manager application.

Once it's an official release, the update manager will automatically show it as an option at the top (unless you've specifically changed the settings for that).

---

