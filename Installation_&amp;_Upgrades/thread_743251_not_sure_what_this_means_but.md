---
title: "not sure what this means but"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by benjaminjames on 2008-04-02
got this message  whilst installing ubuntu any help much appreciated thank you

An error occurred while installing packages:

E:Sub-process /usr/bin/dpkg returned an error code (1)

The following packages are in a broken state:



This may be due to using an old installer image, or it may be due to a bug in some of the packages listed above. More details may be found in /var/log/syslog. The installer will try to continue anyway, but may fail at a later point, and will not be able to install or remove other packages (possibly including itself) from the installed system. You should first look for newer versions of your installer image, or failing that report the problem to your distributor.forgot something

---

### Post by Pumalite on 2008-04-02
Sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
Post output here.

---

### Post by benjaminjames on 2008-04-02
thanks for the quick reply im having some over issues aswell at the moment being a noob means im not sure if they are related could you perhaps take a look at this aswell sorry for being a pain
[http://ubuntuforums.org/showthread.php?p=4638869#post4638869](http://ubuntuforums.org/showthread.php?p=4638869#post4638869)
ill type those commands that you asked me into the terminal just as soon as envy has finished updating my nvidia drivers

---

### Post by benjaminjames on 2008-04-02
ok so here is the output from the commands that you asked me to type into the terminal
benj@benj-linux:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libggi2 libgii1 libgii1-target-x
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up kubuntu-docs (7.10-5) ...
Using `/usr/share/ubuntu-artwork/home/kfirefox-index.html' to provide `firefox-homepage'.
ln: `/usr/share/ubuntu-artwork/home/images': cannot overwrite directory
dpkg: error processing kubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)
benj@benj-linux:~$ sudo apt-get update
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Get: 3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_GB          
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB      
Get: 5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Translation-en_GB   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Translation-en_GB         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_GB   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Translation-en_GB     
Get: 6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_GB            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_GB              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Packages
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty Release.gpg
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Translation-en_GB
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty Release
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Packages
Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) gusty/all Packages
Fetched 6B in 1s (5B/s)
Reading package lists... Done
benj@benj-linux:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up kubuntu-docs (7.10-5) ...
Using `/usr/share/ubuntu-artwork/home/kfirefox-index.html' to provide `firefox-homepage'.
ln: `/usr/share/ubuntu-artwork/home/images': cannot overwrite directory
dpkg: error processing kubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)
benj@benj-linux:~$

---

### Post by Pumalite on 2008-04-02
Try sudo dpkg --configure -a

---

### Post by benjaminjames on 2008-04-02
ok will try it now btw what will it do if it works?
done it i got the following
benj@benj-linux:~$ sudo dpkg --configure -a
[sudo] password for benj:
Setting up kubuntu-docs (7.10-5) ...
Using `/usr/share/ubuntu-artwork/home/kfirefox-index.html' to provide `firefox-homepage'.
ln: `/usr/share/ubuntu-artwork/home/images': cannot overwrite directory
dpkg: error processing kubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kubuntu-docs
benj@benj-linux:~$

---

### Post by Pumalite on 2008-04-02
Try:
sudo dpkg --remove --force-remove-reinstreq kubuntu-docs
Then reinstall

---

### Post by benjaminjames on 2008-04-02
reinstall what?

---

### Post by Pumalite on 2008-04-02
Post the output of the command I gave you.

---

### Post by benjaminjames on 2008-04-03
ok sorry for the wait i had to go to bed :) here is the output from the command
benj@benj-linux:~$ sudo dpkg --remove --force-remove-reinstreq kubuntu-docs
[sudo] password for benj:
Sorry, try again.
[sudo] password for benj:
(Reading database ... 192977 files and directories currently installed.)
Removing kubuntu-docs ...

---

### Post by benjaminjames on 2008-04-03
bump

---

### Post by Pumalite on 2008-04-03
That-s not the full output. Please copy and paste the output here.

---

### Post by Pumalite on 2008-04-03
Got your PM.

---

### Post by benjaminjames on 2008-04-04
ok so i logged in just 5 mins ago and nothing seems to be broken at the mo :) no warning messages and that so i opened a terminal and typed what you wanted me to and got the following 
dpkg - warning: ignoring request to remove kubuntu-docs which isn't installed.
i must say im a tad confused but thats quite a common thing when im using ubuntu :), so what is your professional opinion????

---

### Post by Pumalite on 2008-04-04
Try to install something with aptitude and post the output here.

---

### Post by benjaminjames on 2008-04-05
ok will do but what is aptitude????

---

