---
title: "upgrade problem"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by garymc1 on 2007-05-01
when i open terminal and type apt-get update i get 

root@garymc-desktop:/home/garymc# apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_GB                   
Get: 2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_GB                
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_GB             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_GB               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Translation-en_GB             
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_GB           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_GB     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Translation-en_GB     
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports Release.gpg [191B]          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Translation-en_GB     
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Translation-en_GB           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Translation-en_GB             
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/multiverse Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/universe Translation-en_GB     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports Release                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_GB            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_GB        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_GB      
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release                        
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/multiverse Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/universe Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages               
Get: 9 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]                 
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_GB
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages
Fetched 199B in 3s (56B/s)
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
root@garymc-desktop:/home/garymc# 

how can i fix this thanks gary

---

### Post by bulldog on 2007-05-01
Yes,well,which ubuntu do you have installed?
Your sources.list has Dapper and Edgy repositories mixed up.

You should use the Edgy lines and remove the Dapper entries if you're running Edgy.

---

### Post by garymc1 on 2007-05-01
i am using ubuntu edgy 6.10

this is my source list 
i get that error when i try to update 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main

##Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main multiverse restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy avant-window-navigator

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

---

### Post by bulldog on 2007-05-01
That looks better.
try ```
sudo aptitude update && sudo aptitude dist-upgrade
```

I,m not really an expert in this,so try and see what happens :(

---

### Post by garymc1 on 2007-05-01
when i open Synaptic Package Manager i get this error message 
: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

---

### Post by bulldog on 2007-05-01
Try the command from my previous post in a terminal,it can give us useful output.

---

### Post by garymc1 on 2007-05-01
when i try the command 
sudo aptitude update && sudo aptitude dist-upgrade
i get 
root@garymc-desktop:/home/garymc# sudo aptitude update && sudo aptitude dist-upgrade
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
root@garymc-desktop:/home/garymc# #

---

### Post by bulldog on 2007-05-01
There seem something wrong with the listed packages,not the sources.list.

I think you'll have to wait till someone comes around with knowledge about this.
I have not,sorry.

---

### Post by garybrlow on 2007-05-01
The Universe Repositories are currently broken/off line/unavailable. They are probably being updated, It is not advisable to upgrade anything (forced or otherwise) especially if certain packages are needed from universe as it will result to broken installations. The safe thing to do is just wait until universe becomes available again.

If you really need to install software right now and unfortunately it belongs to universe, you have to obtain the debs from [http://packages.ubuntu.com](http://packages.ubuntu.com).  You have to download the particular deb packages including its dependencies (if the dependencies are from universe as well) manually. Open filemanager as root by running the command "gksu filemanger" (filenamager = nautilus, konqueror, thunar or whatever you're using) and copy the debs to /var/cache/apt/archives. After copying, install the software by running the command sudo apt-get install softwarepackage, using synaptic, or whatever install method you're comfortable with.

Cheers!!! :)


GaryBrlow :biggrin:

---

### Post by Chazall1 on 2007-05-02
I have a question about Synaptic Pkg Mgr? In Settings - Repositories - Ubuntu Software to Download, It gives you a Download From option. Mine is listing Custom Servers. I have not changed this setting, is the Custom Servers OK or should I chose Main Server or the US Server Option? Does it matter?

---

### Post by garymc1 on 2007-05-03
OK now I have got it fixed so I can download updates but when I try to install then I get 

garymc@garymc-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libcurl3 libcurl3-gnutls python-pam synaptic
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1396kB of archives.
After unpacking 65.5kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `libgpg-error0' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/libcurl3_7.15.4-1ubuntu2.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `hicolor-icon-theme': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libcurl3_7.15.4-1ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

