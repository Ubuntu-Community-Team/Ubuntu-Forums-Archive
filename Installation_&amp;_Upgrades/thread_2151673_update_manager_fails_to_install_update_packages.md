---
title: "update manager fails to install update packages"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by Hobo4bob on 2013-06-05
everytime I try to use the update manager I always get a package installation fail. I clicked the details tab and got this:

installArchives() failed:  Extracting templates from packages: 53%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 53%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 53%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 53%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 190359 files and directories currently installed.) 
Unpacking sysvutils (from .../sysvutils_2.86.ds1-14.1ubuntu45.1_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/sysvutils_2.86.ds1-14.1ubuntu45.1_amd64.deb (--unpack): 
 trying to overwrite '/usr/share/man/man1/mesg.1.gz', which is also in package sysvinit-utils 2.88dsf-13.10ubuntu11.1 
Processing triggers for man-db ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/sysvutils_2.86.ds1-14.1ubuntu45.1_amd64.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

so is it something wrong with my computer? or packages i need to find and delete? 
Btw: pretty new to ubuntu so i don't know what this means.....yet

---

### Post by fantab on 2013-06-05
Try this from TERMINAL [ctrl+alt+T]: Run the commands one by one
```
sudo -i
dpkg --purge sysvutils
apt-get remove --purge sysvutils
apt-get clean
apt-get autoremove
apt-get -f install
apt-get update
apt-get dist-upgrade
apt-get install sysvutils
exit

```
If you still get errors post the output of '*sudo apt-get update*' here.

---

### Post by Hobo4bob on 2013-06-05
> **fantab said:**
> Try this from TERMINAL [ctrl+alt+T]: Run the commands one by one
```
sudo -i
dpkg --purge sysvutils
apt-get remove --purge sysvutils
apt-get clean
apt-get autoremove
apt-get -f install
apt-get update
apt-get dist-upgrade
apt-get install sysvutils
exit

```
If you still get errors post the output of '*sudo apt-get update*' here.
Did all of this when i used update manager again still gave me the same error Btw: while i was in the root accout when i ran the depackage command and the purge on the sysvutils it said it was never installed even when i reran this whole entire command line again

here is what came up when i did sudo apt-get update:
slashdot@shuttle:~$ sudo apt-get update
[sudo] password for slashdot: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main amd64 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse i386 Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main TranslationIndex                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse TranslationIndex                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner amd64 Packages                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse amd64 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse TranslationIndex        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_US               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en                  
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Reading package lists... Done

---

### Post by fantab on 2013-06-05
You have LUCID and HARDY repos in the sources.list. How did you manage that? You should not have them. Thats the problem.

You have to edit /etc/apt/sources.list file:

sudo gedit /etc/apt/sources.list

Sources file will open with gedit. DELETE all the line that contain terms. 'hardy' and/or 'lucid'. Save the file an run 'sudo apt-get update'...

---

### Post by Hobo4bob on 2013-06-06
Thanks for all the help fantab it worked.

P.S. do you know a place where i can learn more about linux (distro: ubuntu) so i don't have to worry about problems like these again?

---

