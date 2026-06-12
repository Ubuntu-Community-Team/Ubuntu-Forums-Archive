---
title: "linux-image-3.0.0-16-generic partial install?"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by twiistedkaos on 2012-02-04
**Ubuntu 11.10**
```

0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.0.0-16-generic (3.0.0-16.28) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.0.0-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.0.0-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I tried to clean/autoclean packages. Also tried the force switch(-f) and still have no success. Afraid to restart my computer because of this. Any help appreciated

---

### Post by raja.genupula on 2012-02-05
```
sudo apt-get remove -f
```

try that

---

### Post by twiistedkaos on 2012-02-05
Well at first you had me thinking "Oh ****... the one thing I did not try", However same error as above. :-(

---

### Post by raja.genupula on 2012-02-05
open your terminal and do this 

```
sudo rm -rf /var/cache/apt/*

sudo apt-get remove -f

sudo apt-get update
```

let us know what you got .
All the best,.

---

### Post by twiistedkaos on 2012-02-05
Still get the same error at the remove -f line. :(

---

### Post by raja.genupula on 2012-02-06
please post the terminal out put here . 
Thank you .

---

### Post by twiistedkaos on 2012-02-06
Well since it's the same error I didn't bother posting the output, but here you go:

**sudo rm -rf /var/cache/apt/* && sudo apt-get remove -f**
```

sudo rm -rf /var/cache/apt/*
[sudo] password for default: 
$ sudo apt-get remove -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libircclient1 libjs-mootools libjpeg-progs
  libindicator-messages-status-provider1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.0.0-16-generic (3.0.0-16.28) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.0.0-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.0.0-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**sudo apt-get update**
```

Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-proposed InRelease                    
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:1 http://repo.evolonline.org oneiric InRelease [4,907 B]                   
Hit http://archive.canonical.com oneiric Release                               
Get:2 http://us.archive.ubuntu.com oneiric-proposed Release.gpg [198 B]        
Hit http://security.ubuntu.com oneiric-security Release                        
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://us.archive.ubuntu.com oneiric Release                               
Ign http://ppa.launchpad.net oneiric InRelease                        
Ign http://ppa.launchpad.net oneiric InRelease                        
Ign http://ppa.launchpad.net oneiric InRelease                        
Ign http://ppa.launchpad.net oneiric InRelease                        
Hit http://ppa.launchpad.net oneiric Release.gpg                      
Hit http://ppa.launchpad.net oneiric Release.gpg                      
Hit http://us.archive.ubuntu.com oneiric-updates Release              
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                      
Get:3 http://us.archive.ubuntu.com oneiric-proposed Release [40.8 kB]          
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:4 http://repo.evolonline.org oneiric/main i386 Packages [2,134 B]          
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://repo.evolonline.org oneiric/main TranslationIndex                   
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en     
Get:5 http://us.archive.ubuntu.com oneiric-proposed/restricted i386 Packages [2,384 B]
Get:6 http://us.archive.ubuntu.com oneiric-proposed/main i386 Packages [171 kB]
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Get:7 http://us.archive.ubuntu.com oneiric-proposed/multiverse i386 Packages [14 B]
Get:8 http://us.archive.ubuntu.com oneiric-proposed/universe i386 Packages [17.4 kB]
Ign http://archive.canonical.com oneiric/partner Translation-en                
Get:9 http://us.archive.ubuntu.com oneiric-proposed/main TranslationIndex [73 B]
Get:10 http://us.archive.ubuntu.com oneiric-proposed/multiverse TranslationIndex [70 B]
Get:11 http://us.archive.ubuntu.com oneiric-proposed/restricted TranslationIndex [71 B]
Get:12 http://us.archive.ubuntu.com oneiric-proposed/universe TranslationIndex [73 B]
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Ign http://repo.evolonline.org oneiric/main Translation-en_US                  
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Get:13 http://us.archive.ubuntu.com oneiric-proposed/main Translation-en [53.9 kB]
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://repo.evolonline.org oneiric/main Translation-en                     
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Translation-en    
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Translation-en    
Hit http://us.archive.ubuntu.com oneiric-proposed/universe Translation-en      
Ign http://ppa.launchpad.net oneiric/main Translation-en_US           
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign https://private-ppa.launchpad.net oneiric InRelease
Hit https://private-ppa.launchpad.net oneiric Release.gpg
Hit https://private-ppa.launchpad.net oneiric Release
Hit https://private-ppa.launchpad.net oneiric/main i386 Packages
Ign https://private-ppa.launchpad.net oneiric/main TranslationIndex
Ign https://private-ppa.launchpad.net oneiric/main Translation-en_US           
Ign https://private-ppa.launchpad.net oneiric/main Translation-en
Fetched 293 kB in 19s (15.0 kB/s)

```

---

### Post by raja.genupula on 2012-02-06
Hi same issue i have faced in the 10.04 LTS when i am using that . 

OK now regarding this issue 

..report this thing to launchpad as a bug.

now please open your synaptic and search for Linux-image and then choose that error kernel and if it found then remove it from there . 

let me know what you got .

---

### Post by twiistedkaos on 2012-02-06
I have a question before I remove this kernel.

**uname -r**
```
3.0.0-16-generic
```

Would not removing this kernel corrupt my install, Since according to uname it's the one in use.

---

### Post by raja.genupula on 2012-02-07
we can use old kernel i think , i hope you still have them on your system .

---

### Post by twiistedkaos on 2012-02-07
Yeah the who "I think" part of your reply has me a tad bit worried. I've already restarted my computer, so everything seems to be working fine. I just still get that error, I'll wait for a few weeks and see if an update fixes this. I really don't want to remove a kernel and "hope" that it doesn't corrupt my install. I'll post back if anything changes. 

Thanks for your help!

---

### Post by raja.genupula on 2012-02-07
hmm its a word sounds like (how can i say man , i am not expert or even not good  in this english ) ok i mean its a habit word i used generally . 

man do you have faced any difficulty or problem if you're booting from old kernels .nothing . so what i am saying also like that .even though your system is running from old kernels its not going to give you any problem . 

after releasing of fix to that kernel  you can get that from update manager . 

or 

choose your decision .

choice is yours 

cheers

with best wishes
raju

---

### Post by twiistedkaos on 2012-02-07
I had no issues what so ever with the old kernels. And I still seem to have a few of the older kernels still installed. What steps do I take to revert back to the old kernel? Just use the update-grub program?

---

### Post by raja.genupula on 2012-02-08
first remove this kernel and then do sudo update-grub . so your grub will set to that old kernel .

---

### Post by Tuxi on 2012-03-11
I had a similar error.  I have /boot on a separate partition, and a "df -h" showed /boot at 96% usage.  I removed a couple of old kernel images, and successfully installed the new kernel image.

---

