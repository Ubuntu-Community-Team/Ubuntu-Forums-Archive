---
title: "Problem: package system is broken"
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2014-01-27
Hi,

I have a problem of unmet dependencies under Ubuntu 12.04 64 bit. I was trying to install an old version off gcc (4.2.3) downloaded from debian freeze.

```

The following packages have unmet dependencies:

build-essential: Depends: gcc (>= 4:4.4.3) but 4:4.2.3-2 is installed
                 Depends: g++ (>= 4:4.4.3) but 4:4.6.3-1ubuntu5 is installed
g++: Depends: cpp (>= 4:4.6.3-1ubuntu5) but 4:4.6.3-1ubuntu5 is installed
     Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is installed
gcc: Depends: cpp (>= 4:4.2.3-2) but 4:4.6.3-1ubuntu5 is installed
     Depends: gcc-4.2 (>= 4.2.3-1) but it is not installed
gcc-multilib: Depends: cpp (>= 4:4.6.3-1ubuntu5) but 4:4.6.3-1ubuntu5 is installed
              Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is installed

```

I read this [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies/142808#142808](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies/142808#142808) and I followed all the step up to sudo apt-get remove --dry-run package-name but it does not work. In my system I have installed gcc 4.4, 4.6 and 4.8 using this PPA ppa:ubuntu-toolchain-r/test.
The command apt-get install -f does not work and gives  

```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  openjdk-7-jre-lib libkms1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc
Suggested packages:
  gcc-multilib automake1.9 gcc-doc
The following packages will be upgraded:
  gcc
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/5,114 B of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of gcc:
 gcc depends on gcc-4.2 (>= 4.2.3-1); however:
  Package gcc-4.2 is not installed.
dpkg: error processing gcc (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 gcc
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Any suggestions?

---

### Post by Bucky Ball on 2014-01-27
Have your run:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

This will not upgrade your release to a newer one, only your current release and everything in it. 

Please post back any error messages you get from these commands.

---

### Post by erotavlas on 2014-01-27
The output of the command is this
```

 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 build-essential : Depends: gcc (>= 4:4.4.3) but 4:4.2.3-2 is installed
 g++ : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is installed
 gcc : Depends: gcc-4.2 (>= 4.2.3-1) but it is not installable
 gcc-multilib : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by Bucky Ball on 2014-01-27
You ran 'sudo apt-get update' first??? You should. You need to run that when you install a new PPA.

---

### Post by erotavlas on 2014-01-27
Yes I did.

```

sudo apt-get update
Hit http://it.archive.ubuntu.com precise Release.gpg
Hit http://it.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://it.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://it.archive.ubuntu.com precise Release                               
Hit http://it.archive.ubuntu.com precise-updates Release                       
Hit http://it.archive.ubuntu.com precise-backports Release                     
Hit http://it.archive.ubuntu.com precise/main Sources                          
Hit http://it.archive.ubuntu.com precise/restricted Sources                    
Hit http://it.archive.ubuntu.com precise/universe Sources                      
Hit http://it.archive.ubuntu.com precise/multiverse Sources                    
Hit http://it.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://it.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://it.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://it.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://it.archive.ubuntu.com precise/main i386 Packages                    
Hit http://it.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://it.archive.ubuntu.com precise/universe i386 Packages                
Hit http://it.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://it.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://it.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://it.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://it.archive.ubuntu.com precise/universe TranslationIndex             
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://it.archive.ubuntu.com precise-updates/main Sources                  
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:3 http://download.virtualbox.org precise Release.gpg [198 B]               
Hit http://it.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://download.virtualbox.org precise Release                             
Ign http://download.virtualbox.org precise Release                             
Hit http://it.archive.ubuntu.com precise-updates/universe Sources              
Ign http://download.virtualbox.org precise/contrib amd64 Packages/DiffIndex    
Get:4 http://security.ubuntu.com precise-security/main Sources [96.7 kB]       
Hit http://it.archive.ubuntu.com precise-updates/multiverse Sources            
Ign http://download.virtualbox.org precise/contrib i386 Packages/DiffIndex     
Hit http://it.archive.ubuntu.com precise-updates/main amd64 Packages           
Ign http://download.virtualbox.org precise/contrib TranslationIndex            
Hit http://it.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Hit http://download.virtualbox.org precise/contrib amd64 Packages              
Hit http://it.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://download.virtualbox.org precise/contrib i386 Packages               
Get:5 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:6 http://security.ubuntu.com precise-security/universe Sources [30.5 kB]   
Hit http://it.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Get:7 http://security.ubuntu.com precise-security/multiverse Sources [1,797 B] 
Hit http://it.archive.ubuntu.com precise-updates/main i386 Packages            
Get:8 http://security.ubuntu.com precise-security/main amd64 Packages [357 kB] 
Hit http://it.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://it.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://it.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://it.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://it.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Ign http://download.virtualbox.org precise/contrib Translation-en_GB           
Hit http://it.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Ign http://download.virtualbox.org precise/contrib Translation-en              
Hit http://it.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://it.archive.ubuntu.com precise-backports/main Sources                
Hit http://it.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://it.archive.ubuntu.com precise-backports/universe Sources            
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://it.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com lucid Release.gpg                             
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://archive.canonical.com precise Release                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://it.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com lucid Release                                 
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://it.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://archive.canonical.com lucid/partner amd64 Packages                  
Hit http://archive.canonical.com lucid/partner i386 Packages                   
Ign http://archive.canonical.com lucid/partner TranslationIndex                
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://it.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://it.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://it.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://it.archive.ubuntu.com precise-backports/restricted i386 Packages    
Get:9 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:10 http://security.ubuntu.com precise-security/universe amd64 Packages [90.2 kB]
Hit http://it.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://it.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Ign http://archive.canonical.com precise/partner Translation-en_GB             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://archive.canonical.com precise/partner Translation-en_GB             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://archive.canonical.com lucid/partner Translation-en_GB               
Hit http://it.archive.ubuntu.com precise-backports/main TranslationIndex       
Ign http://archive.canonical.com lucid/partner Translation-en                  
Hit http://it.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://it.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Get:11 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,454 B]
Get:12 http://security.ubuntu.com precise-security/main i386 Packages [377 kB] 
Hit http://it.archive.ubuntu.com precise-backports/universe TranslationIndex   
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Hit http://it.archive.ubuntu.com precise/main Translation-en_GB                
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://it.archive.ubuntu.com precise/main Translation-en                   
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://it.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://it.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://it.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://it.archive.ubuntu.com precise/restricted Translation-en    
Hit http://it.archive.ubuntu.com precise/universe Translation-en_GB   
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://it.archive.ubuntu.com precise/universe Translation-en               
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://it.archive.ubuntu.com precise-updates/main Translation-en_GB        
Hit http://it.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://it.archive.ubuntu.com precise-updates/multiverse Translation-en_GB  
Hit http://it.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://it.archive.ubuntu.com precise-updates/restricted Translation-en_GB  
Hit http://it.archive.ubuntu.com precise-updates/restricted Translation-en     
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Hit http://it.archive.ubuntu.com precise-updates/universe Translation-en_GB    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://it.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://it.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://it.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://it.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://it.archive.ubuntu.com precise-backports/universe Translation-en     
Get:13 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:14 http://security.ubuntu.com precise-security/universe i386 Packages [94.4 kB]
Get:15 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,650 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Fetched 1,114 kB in 20s (55.5 kB/s)                                            
Reading package lists... Done
W: GPG error: http://download.virtualbox.org precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
tore@tore-notebook:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 build-essential : Depends: gcc (>= 4:4.4.3) but 4:4.2.3-2 is installed
 g++ : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is installed
 gcc : Depends: gcc-4.2 (>= 4.2.3-1) but it is not installable
 gcc-multilib : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by erotavlas on 2014-01-27
Before today I have gcc 4.4, 4-6 and 4.8 working together. Today I tried to install the old 4.2.3 and it broke all.

---

### Post by ian-weisser on 2014-01-27
You can have multiple gcc versions installed...but only one can be a packaged version.
Multiple installed versions of any package is not supported, and may result in unexpected behavior.
The extra versions must be manually installed from source or tarball.

Use the command [FONT=courier new]rmadison -u ubuntu gcc[/FONT] to determine the appropriate version of gcc for your version of Ubuntu.
Use [FONT=courier new]dpkg --remove <package>[/FONT] to remove the inappropriate version packages.

---

### Post by erotavlas on 2014-01-28
It does not work

```

rmadison -u ubuntu gcc
The program 'rmadison' is currently not installed.  You can install it by typing:
sudo apt-get install devscripts

sudo apt-get install devscripts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 build-essential : Depends: gcc (>= 4:4.4.3) but 4:4.2.3-2 is to be installed
 g++ : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is to be installed
 gcc : Depends: gcc-4.2 (>= 4.2.3-1) but it is not installable
 gcc-multilib : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

The standard version of gcc of Ubuntu 12.04 is the 4.6.x

---

### Post by Ubi_one_2014 on 2014-01-28
did you do 
apt-get -f install  ?

---

### Post by erotavlas on 2014-01-28
Yes, you can look at my first post. I report here the result

```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  openjdk-7-jre-lib libkms1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc
Suggested packages:
  gcc-multilib automake1.9 gcc-doc
The following packages will be upgraded:
  gcc
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/5,114 B of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of gcc:
 gcc depends on gcc-4.2 (>= 4.2.3-1); however:
  Package gcc-4.2 is not installed.
dpkg: error processing gcc (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 gcc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Ubi_one_2014 on 2014-01-28
apt-get remove gcc-4.2.3.1

show output first. before you press yess

---

### Post by erotavlas on 2014-01-28
```

sudo apt-get remove gcc-4.2.3.1
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Unable to locate package gcc-4.2.3.1
E: Couldn't find any package by regex 'gcc-4.2.3.1'

```

and

```

locate gcc | grep ".deb"
/home/user/.local/share/Trash/files/gcc_4.2.3-2_amd64.deb
/home/user/.local/share/Trash/files/llvm-gcc-4.2_2.7-0ubuntu1_amd64.deb
/home/user/.local/share/Trash/info/gcc_4.2.3-2_amd64.deb.trashinfo
/home/user/.local/share/Trash/info/llvm-gcc-4.2_2.7-0ubuntu1_amd64.deb.trashinfo
/usr/lib/debug/lib/x86_64-linux-gnu/libgcc_s.so.1
/usr/share/doc/gcc-4.8-base/libstdc++/html/manual/debug.html
/usr/share/doc/gcc-4.8-base/libstdc++/html/manual/debug_mode.html
/usr/share/doc/gcc-4.8-base/libstdc++/html/manual/debug_mode_design.html
/usr/share/doc/gcc-4.8-base/libstdc++/html/manual/debug_mode_semantics.html
/usr/share/doc/gcc-4.8-base/libstdc++/html/manual/debug_mode_using.html
/var/cache/apt/archives/gcc_4%3a4.6.3-1ubuntu5_amd64.deb

```

---

### Post by Ubi_one_2014 on 2014-01-28
am i correct that gcc-4.2.3.1 broke your system ?
otherwise, pls post exactly what package you have download in order to install

---

### Post by erotavlas on 2014-01-28
I have downloaded first this llvm-gcc-4.2_2.7-0ubuntu1_amd64.deb from ubuntu packets manager 
and then this gcc_4.2.3-2_amd64.deb from debian freeze.

---

### Post by Ubi_one_2014 on 2014-01-28
apt-get remove [COLOR=#000000]gcc_4.2.3-2_amd64.deb[/COLOR]

---

### Post by erotavlas on 2014-01-28
```

sudo apt-get remove gcc_4.2.3-2_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gcc_4.2.3-2_amd64.deb
E: Couldn't find any package by regex 'gcc_4.2.3-2_amd64.deb'

```

Now the command apt-get -f install produce

```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  openjdk-7-jre-lib libkms1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc
Suggested packages:
  gcc-multilib automake1.9 gcc-doc
The following packages will be upgraded:
  gcc
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/5,114 B of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of gcc:
 gcc depends on gcc-4.2 (>= 4.2.3-1); however:
  Package gcc-4.2 is not installed.
dpkg: error processing gcc (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 gcc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Ubi_one_2014 on 2014-01-28
sudo apt-get remove llvm-gcc

followed by apt-get -f install

---

### Post by erotavlas on 2014-01-28
I get the same result
```

sudo apt-get remove llvm-gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'llvm-gcc-4.6' instead of 'llvm-gcc'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 build-essential : Depends: gcc (>= 4:4.4.3) but 4:4.2.3-2 is to be installed
 g++ : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is to be installed
 gcc : Depends: gcc-4.2 (>= 4.2.3-1) but it is not installable
 gcc-multilib : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  openjdk-7-jre-lib libkms1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc
Suggested packages:
  gcc-multilib automake1.9 gcc-doc
The following packages will be upgraded:
  gcc
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/5,114 B of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of gcc:
 gcc depends on gcc-4.2 (>= 4.2.3-1); however:
  Package gcc-4.2 is not installed.
dpkg: error processing gcc (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 gcc
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Ubi_one_2014 on 2014-01-28
apt-get autoclean

followed by apt-get -f install

---

### Post by Bucky Ball on 2014-01-28
Be careful with autoclean. Just plain 'sudo apt-get clean' might be a better option so you can see what is going to be removed.

---

### Post by Ubi_one_2014 on 2014-01-28
i see,

i am running out of options, regarding this topic.

some else is able to help erotavlas out?

---

### Post by erotavlas on 2014-01-28
I have tried with both commands, but the result is the same as before. As you can read in my first post I tried the very long procedure posted in Ubuntu ask

```

sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  openjdk-7-jre-lib libkms1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc
Suggested packages:
  gcc-multilib automake1.9 gcc-doc
The following packages will be upgraded:
  gcc
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/5,114 B of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of gcc:
 gcc depends on gcc-4.2 (>= 4.2.3-1); however:
  Package gcc-4.2 is not installed.
dpkg: error processing gcc (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 gcc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Ubi_one_2014 on 2014-01-28
a last attempt:

sudo apt-get remove [COLOR=#000000][FONT=verdana]gcc g++

apt-get -f install[/FONT][/COLOR]

---

### Post by erotavlas on 2014-01-28
The same
```

sudo apt-get remove gcc g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 build-essential : Depends: gcc (>= 4:4.4.3) but it is not going to be installed
                   Depends: g++ (>= 4:4.4.3) but it is not going to be installed
 dkms : Depends: gcc but it is not going to be installed
 g++-multilib : Depends: g++ (>= 4:4.6.3-1ubuntu5) but it is not going to be installed
 gcc-multilib : Depends: gcc (>= 4:4.6.3-1ubuntu5) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

The PPA used are the following
```

bumblebee-stable-precise.list
bumblebee-stable-precise.list.save
danielrichter2007-grub-customizer-precise.list
danielrichter2007-grub-customizer-precise.list.save
darxus-sensors-applet-precise.list
darxus-sensors-applet-precise.list.save
firmware-testing-team-ppa-fwts-stable-precise.list
firmware-testing-team-ppa-fwts-stable-precise.list.save
linrunner-tlp-precise.list
linrunner-tlp-precise.list.save
ubuntu-clamav-ppa-precise.list
ubuntu-clamav-ppa-precise.list.save
ubuntu-toolchain-r-test-precise.list
ubuntu-toolchain-r-test-precise.list.save
webupd8team-java-precise.list
webupd8team-java-precise.list.save
w-rouesnel-openssh-hpn-precise.list
w-rouesnel-openssh-hpn-precise.list.save
xorg-edgers-ppa-precise.list
xorg-edgers-ppa-precise.list.save

```

---

### Post by nothingspecial on 2014-01-28
> **erotavlas said:**
> 

I read this [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies/142808#142808](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies/142808#142808) and I followed all the step up to sudo apt-get remove --dry-run package-name but it does not work. In my system I have installed gcc 4.4, 4.6 and 4.8 using this PPA ppa:ubuntu-toolchain-r/test.


You ought to try the bit about purging 3rd party ppas underneath.

---

### Post by erotavlas on 2014-01-28
I cannot install ppa-purge before I have repaired my package system. However I tried to remove the PPA manually **add-apt-repository -r** ppa:ubuntu-toolchain-r/test the apt-get update && apt-get upgrade and the result is the same.

---

### Post by westie457 on 2014-01-28
```
gksudo gedit /etc/apt/sources.list
``` find the PPA and put a # at the front of each line. Then ```
sudo apt-get update
sudo apt-get upgrade
``` any errors ```
sudo apt-get install -f
```

If the gksudo command fails because gksu is not installed using sudo instead should work.

Let us know how it goes.

Thank you.

---

### Post by erotavlas on 2014-01-28
> **westie457 said:**
> ```
gksudo gedit /etc/apt/sources.list
``` find the PPA and put a # at the front of each line. Then ```
sudo apt-get update
sudo apt-get upgrade
``` any errors ```
sudo apt-get install -f
```

If the gksudo command fails because gksu is not installed using sudo instead should work.

Let us know how it goes.

Thank you.

The PPA are inside the folder /etc/apt/sources.list.d. Inside the /etc/apt/sources.list there are not PPA. This is the content of sources.list:

```

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://it.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://it.archive.ubuntu.com/ubuntu/ precise universe
deb http://it.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://it.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner

## virtual box
deb http://download.virtualbox.org/virtualbox/debian precise contrib

```

To avoid problem I moved all the files inside the folder /etc/apt/sources.list.d/ in another folder. So at the moment I don't have any PPA.
Nothing is changed.

---

### Post by westie457 on 2014-01-28
Did you run the other commands?

If not, please run them and post the output.

Thank you.

---

### Post by erotavlas on 2014-01-28
```

sudo apt-get update
Hit http://archive.canonical.com precise Release.gpg
Hit http://archive.canonical.com precise Release.gpg                                               
Hit http://extras.ubuntu.com precise Release.gpg                                                   
Hit http://it.archive.ubuntu.com precise Release.gpg                                               
Hit http://security.ubuntu.com precise-security Release.gpg          
Hit http://archive.canonical.com precise Release                                                      
Hit http://extras.ubuntu.com precise Release                                                          
Hit http://it.archive.ubuntu.com precise-updates Release.gpg                                
Hit http://security.ubuntu.com precise-security Release              
Hit http://archive.canonical.com precise Release                                                                             
Hit http://extras.ubuntu.com precise/main Sources                                                                            
Hit http://security.ubuntu.com precise-security/main Sources                                                                
Hit http://archive.canonical.com precise/partner amd64 Packages                                       
Hit http://archive.canonical.com precise/partner i386 Packages                             
Ign http://archive.canonical.com precise/partner TranslationIndex                          
Hit http://it.archive.ubuntu.com precise-backports Release.gpg                             
Hit http://extras.ubuntu.com precise/main amd64 Packages             
Hit http://extras.ubuntu.com precise/main i386 Packages                                               
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                  
Hit http://security.ubuntu.com precise-security/restricted Sources                                                          
Hit http://security.ubuntu.com precise-security/universe Sources                                      
Hit http://security.ubuntu.com precise-security/multiverse Sources                                                          
Hit http://security.ubuntu.com precise-security/main amd64 Packages                                                         
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages                                                   
Hit http://security.ubuntu.com precise-security/universe amd64 Packages                                                     
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages                                                   
Hit http://security.ubuntu.com precise-security/main i386 Packages                                                          
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                                                    
Hit http://security.ubuntu.com precise-security/universe i386 Packages                                                      
Hit http://archive.canonical.com precise/partner Sources                                                                    
Hit http://archive.canonical.com precise/partner amd64 Packages                                                             
Hit http://archive.canonical.com precise/partner i386 Packages                             
Ign http://archive.canonical.com precise/partner TranslationIndex                          
Hit http://it.archive.ubuntu.com precise Release                                           
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                                                                           
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                                              
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                                        
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                                        
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                          
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                                
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                   
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://it.archive.ubuntu.com precise-updates Release             
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                            
Hit http://it.archive.ubuntu.com precise-backports Release                                                                  
Hit http://it.archive.ubuntu.com precise/main Sources                                                                        
Hit http://it.archive.ubuntu.com precise/restricted Sources                                           
Ign http://extras.ubuntu.com precise/main Translation-en_GB
Hit http://it.archive.ubuntu.com precise/universe Sources
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://it.archive.ubuntu.com precise/multiverse Sources                     
Ign http://archive.canonical.com precise/partner Translation-en_GB              
Hit http://it.archive.ubuntu.com precise/main amd64 Packages
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_GB
Ign http://archive.canonical.com precise/partner Translation-en
Hit http://it.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://it.archive.ubuntu.com precise/universe amd64 Packages
Hit http://it.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://it.archive.ubuntu.com precise/main i386 Packages
Hit http://it.archive.ubuntu.com precise/restricted i386 Packages
Hit http://it.archive.ubuntu.com precise/universe i386 Packages
Hit http://it.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://it.archive.ubuntu.com precise/main TranslationIndex
Hit http://it.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://it.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://it.archive.ubuntu.com precise/universe TranslationIndex
Hit http://it.archive.ubuntu.com precise-updates/main Sources
Hit http://it.archive.ubuntu.com precise-updates/restricted Sources
Hit http://it.archive.ubuntu.com precise-updates/universe Sources
Hit http://it.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://it.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://it.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://it.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://it.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://it.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://it.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://it.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://it.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://it.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://it.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://it.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://it.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://it.archive.ubuntu.com precise-backports/main Sources
Hit http://it.archive.ubuntu.com precise-backports/restricted Sources
Hit http://it.archive.ubuntu.com precise-backports/universe Sources
Hit http://it.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://it.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://it.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://it.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://it.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://it.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://it.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://it.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://it.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://it.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://it.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://it.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://it.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://it.archive.ubuntu.com precise/main Translation-en_GB
Hit http://it.archive.ubuntu.com precise/main Translation-en
Hit http://it.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://it.archive.ubuntu.com precise/multiverse Translation-en
Hit http://it.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://it.archive.ubuntu.com precise/restricted Translation-en
Hit http://it.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://it.archive.ubuntu.com precise/universe Translation-en
Hit http://it.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://it.archive.ubuntu.com precise-updates/main Translation-en
Hit http://it.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://it.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://it.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://it.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://it.archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://it.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://it.archive.ubuntu.com precise-backports/main Translation-en
Hit http://it.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://it.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://it.archive.ubuntu.com precise-backports/universe Translation-en
Reading package lists... Done
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 build-essential : Depends: gcc (>= 4:4.4.3) but 4:4.2.3-2 is installed
 g++ : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is installed
 gcc : Depends: gcc-4.2 (>= 4.2.3-1) but it is not installable
 gcc-multilib : Depends: gcc (>= 4:4.6.3-1ubuntu5) but 4:4.2.3-2 is installed
E: Unmet dependencies. Try using -f.
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  openjdk-7-jre-lib libkms1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc
Suggested packages:
  gcc-multilib automake1.9 gcc-doc
The following packages will be upgraded:
  gcc
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/5,114 B of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of gcc:
 gcc depends on gcc-4.2 (>= 4.2.3-1); however:
  Package gcc-4.2 is not installed.
dpkg: error processing gcc (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 gcc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2014-01-28
Please post the output of:
```
dpkg -l | grep gcc
```

---

### Post by erotavlas on 2014-01-28
```

dpkg -l | grep gcc
rU  gcc                                               4:4.2.3-2                                                               The GNU C compiler
ri  gcc-4.4                                           4.4.7-1ubuntu2                                                          GNU C compiler
ri  gcc-4.4-base                                      4.4.7-1ubuntu2                                                          GCC, the GNU Compiler Collection (base package)
ri  gcc-4.6                                           4.6.4-1ubuntu1~12.04                                                    GNU C compiler
ri  gcc-4.6-base                                      4.6.4-1ubuntu1~12.04                                                    GCC, the GNU Compiler Collection (base package)
ri  gcc-4.6-multilib                                  4.6.4-1ubuntu1~12.04                                                    GNU C compiler (multilib files)
ri  gcc-4.8                                           4.8.1-2ubuntu1~12.04                                                    GNU C compiler
ri  gcc-4.8-base                                      4.8.1-2ubuntu1~12.04                                                    GCC, the GNU Compiler Collection (base package)
ii  gcc-4.8-base:i386                                 4.8.1-2ubuntu1~12.04                                                    GCC, the GNU Compiler Collection (base package)
ri  gcc-4.8-multilib                                  4.8.1-2ubuntu1~12.04                                                    GNU C compiler (multilib files)
ri  gcc-multilib                                      4:4.6.3-1ubuntu5                                                        GNU C compiler (multilib files)
ii  lib32gcc-4.8-dev                                  4.8.1-2ubuntu1~12.04                                                    GCC support library (32 bit development files)
ii  lib32gcc1                                         1:4.8.1-2ubuntu1~12.04                                                  GCC support library (32 bit Version)
ii  libgcc-4.8-dev                                    4.8.1-2ubuntu1~12.04                                                    GCC support library (development files)
ii  libgcc1                                           1:4.8.1-2ubuntu1~12.04                                                  GCC support library
ii  libgcc1:i386                                      1:4.8.1-2ubuntu1~12.04                                                  GCC support library
ii  libgcc1-dbg                                       1:4.8.1-2ubuntu1~12.04                                                  GCC support library (debug symbols)

```

The problem is the first and it is the only one taken from debia freeze.

---

### Post by ian-weisser on 2014-01-28
> **erotavlas said:**
> ```

dpkg -l | grep gcc
rU  gcc                                               4:4.2.3-2                                                                The GNU C compiler
ri  gcc-4.4                                           4.4.7-1ubuntu2                                                           GNU C compiler
ri  gcc-4.4-base                                      4.4.7-1ubuntu2                                                           GCC, the GNU  Compiler Collection (base package)

```

Sorry about the rmadison command not working: Since you had gcc, I erroneously assumed you had build-essential installed.

Clarification: You CAN have more than one version of gcc installed...but the package names cannot be similar. You can have a 'gcc-4.6' package installed alongside a 'gcc-4.7' package. But you cannot have two 'gcc' packages installed - one will overwrite the other.

And that's exactly what seems to have happened here. The old version was 'gcc' instead of 'gcc-4.2', and it replaced the original version:
```
$ rmadison -u ubuntu gcc
 gcc | 4:4.4.3-1ubuntu1  | lucid   | amd64, armel, i386, ia64, powerpc, sparc
 gcc | 4:4.6.3-1ubuntu5  | precise | amd64, armel, armhf, i386, powerpc
 gcc | 4:4.7.2-1ubuntu2  | quantal | amd64, armel, armhf, i386, powerpc
 gcc | 4:4.7.3-1ubuntu10 | raring  | amd64, armhf, i386, powerpc
 gcc | 4:4.8.1-2ubuntu3  | saucy   | amd64, arm64, armhf, i386, powerpc
 gcc | 4:4.8.2-1ubuntu3  | trusty  | amd64, arm64, armhf, i386, powerpc, ppc64el
```

Have you tried:
```
sudo dpkg --purge gcc                              # Try this first
sudo dpkg --purge --force-depends gcc              # Try this ONLY if the previous line fails
sudo apt-get clean gcc                             # Remove gcc 4.2 from the cache
sudo apt-get install gcc                           # Download and install the appropriate version of gcc
```

Alternative: You can manually download your appropriate gcc package to /var/cache/apt/archive and try:
```
sudo apt-get install --reinstall gcc
```

---

### Post by erotavlas on 2014-01-28
Thank you very much :) this command solved my trouble
sudo dpkg --purge --force-depends gcc

now I have these gcc:
```

ii  gcc                                               4:4.6.3-1ubuntu5                                                        GNU C compiler
ri  gcc-4.4                                           4.4.7-1ubuntu2                                                          GNU C compiler
ri  gcc-4.4-base                                      4.4.7-1ubuntu2                                                          GCC, the GNU Compiler Collection (base package)
ri  gcc-4.6                                           4.6.4-1ubuntu1~12.04                                                    GNU C compiler
ri  gcc-4.6-base                                      4.6.4-1ubuntu1~12.04                                                    GCC, the GNU Compiler Collection (base package)
ri  gcc-4.6-multilib                                  4.6.4-1ubuntu1~12.04                                                    GNU C compiler (multilib files)
ri  gcc-4.8                                           4.8.1-2ubuntu1~12.04                                                    GNU C compiler
ri  gcc-4.8-base                                      4.8.1-2ubuntu1~12.04                                                    GCC, the GNU Compiler Collection (base package)
ii  gcc-4.8-base:i386                                 4.8.1-2ubuntu1~12.04                                                    GCC, the GNU Compiler Collection (base package)
ri  gcc-4.8-multilib                                  4.8.1-2ubuntu1~12.04                                                    GNU C compiler (multilib files)
ri  gcc-multilib                                      4:4.6.3-1ubuntu5                                                        GNU C compiler (multilib files)
ii  lib32gcc-4.8-dev                                  4.8.1-2ubuntu1~12.04                                                    GCC support library (32 bit development files)
ii  lib32gcc1                                         1:4.8.1-2ubuntu1~12.04                                                  GCC support library (32 bit Version)
ii  libgcc-4.8-dev                                    4.8.1-2ubuntu1~12.04                                                    GCC support library (development files)
ii  libgcc1                                           1:4.8.1-2ubuntu1~12.04                                                  GCC support library
ii  libgcc1:i386                                      1:4.8.1-2ubuntu1~12.04                                                  GCC support library
ii  libgcc1-dbg                                       1:4.8.1-2ubuntu1~12.04                                                  GCC support library (debug symbols)

```

Is it possible to install gcc-4.2 or llvm-gcc4.2?
Thank you

---

### Post by ian-weisser on 2014-01-28
Easily? No.

[http://packages.ubuntu.com](http://packages.ubuntu.com) has Lucid (10.04) packages for gcc-4.1 and gcc-4.3
You might poke around there a bit and see if something close is in your range.
Normally, I discourage mixing packages from different releases of Ubuntu, but you already know how to undo those conflicts.

It's also possible for you to take the debian gcc (4.2) package and alter the debian/control file to prevent it from overwriting gcc (new name, new install directories, etc). That requires a bit of involved knowledge about packaging.

Or, I suppose, you could install gcc 4.2 from tarball or source. Check the makefile carefully to ensure it's not going to overwrite your packaged gcc files. And you must *remember* that it's not a package someday when the time comes to uninstall 4.2.

---

### Post by erotavlas on 2014-01-28
Ok it seems not very simple. Thank you
Best Regards

---

