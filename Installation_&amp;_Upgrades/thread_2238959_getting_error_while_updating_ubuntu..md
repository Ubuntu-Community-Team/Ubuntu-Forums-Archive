---
title: "getting error while updating ubuntu."
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by jagannath2 on 2014-08-11
Hi I'm using ubuntu 12.04

getting these error while updating. 

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.5) but 2.15-0ubuntu10.6 is installed
             Depends: libc-dev-bin (= 2.15-0ubuntu10.5)
E: Unmet dependencies. Try using -f.

sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kubuntu-debug-installer python-pyudev libkresources4 qapt-batch libqrencode3 libkprintutils4 libnet-daemon-perl libguess1 libkldap4 virtuoso-minimal libqca2
  libkcalcore4 libpolkit-qt-1-1 libprison0 tumbler libkholidays4 libknewstuff2-4 libtumbler-1-0 libknewstuff3-4 libqapt-runtime libvirtodbc0 libqca2-plugin-ossl
  libxfce4ui-1-0 libnepomuksync4 libkdeclarative5 libnepomukquery4a libfluidsynth1 linux-headers-3.2.0-61 libxfconf-0-2 xfce4-panel libthreadweaver4 libkdecore5
  libdbi-perl libnepomukutils4 libktexteditor4 libkmediaplayer4 oxygen-icon-theme libakonadi-kmime4 plasma-scriptengine-javascript libakonadiprotocolinternals1
  libkrosscore4 libbs2b0 libhtml-template-perl xfce-keyboard-shortcuts virtuoso-opensource-6.1-bin libkmbox4 libsolid4 libdlrestrictions1 libnepomuk4 libkcalutils4
  libcue1 libsoprano4 libmicroblog4 libbinio1ldbl libattica0.3 virtuoso-opensource-6.1-common libkdnssd4 libkparts4 kde-runtime-data libclucene0ldbl libqapt1 libkabc4
  shared-desktop-ontologies kdoctools libaudclient2 tumbler-common libnepomukdatamanagement4 icoutils libkidletime4 katepart libkcmutils4 libkcal4
  linux-headers-3.2.0-61-generic libntrack0 soprano-daemon libkalarmcal2 libakonadi-calendar4 libkfile4 libkpty4 libkimap4 libmowgli2 libmailtransport4 libkntlm4
  libplasma3 libplrpc-perl libkemoticons4 libkpimtextedit4 libgarcon-1-0 libaudcore1 libkmime4 gtk2-engines-pixbuf ntrack-module-libnl-0 kdelibs-bin libkdewebkit5
  indicator-status-provider-pidgin kdepimlibs-kio-plugins kde-runtime libkjsembed4 libmpg123-0 libkio5 libakonadi-kabc4 libkjsapi4 libstreams0 libntrack-qt4-1
  kdelibs5-data libkpimidentities4 libkpimutils4 xfconf libkde3support4 libknotifyconfig4 kdelibs5-plugins libkhtml5 libkdeui5 libakonadi-kcal4 libkdesu5
  libakonadi-notes4 libkatepartinterfaces4 kate-data libakonadi-contact4 libakonadi-kde4 libstreamanalyzer0 libdmtx0a
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6-dev
1 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0 B/2,946 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue [Y/n]? 

y
(Reading database ... 360102 files and directories currently installed.)
Preparing to replace libc6-dev 2.15-0ubuntu10.5 (using .../libc6-dev_2.15-0ubuntu10.6_amd64.deb) ...
Unpacking replacement libc6-dev ...
dpkg: error processing /var/cache/apt/archives/libc6-dev_2.15-0ubuntu10.6_amd64.deb (--unpack):
 unable to stat `./usr/include/rpcsvc' (which I was about to install): Input/output error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev_2.15-0ubuntu10.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help me

---

### Post by TheFu on 2014-08-11
You have entered "APT Hell" - that is a technical term.  It happens when the dependencies for installed programs cannot be resolved ... or if something fails during an install - like running out of storage or other corruption.

So - first, verify there is enough storage -
* df -h
* df -i
Is there plenty of storage and inode?
Fix that, as necessary.

I'd probably run an fsck on the partition (unmounted) too.

apt-get isn't as smart as some other tools that work with the APT DB. Try using **aptitude** - sometimes it can resolve issues.

After validating those simple things - hopefully, it will be corrected. If not, then we need to go deeper and try some manual fixes. I hope that isn't necessary.

---

### Post by kc1di on 2014-08-11
Please try the following in a terminal

```
sudo dpkg --configure -a
```
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
```
sudo apt-get update
```

see if that fixed the problem.

---

### Post by jagannath2 on 2014-08-11
Hi I tried these commands. it's not fixed

jagannath@jagannath:~$ sudo dpkg --configure -a
[sudo] password for jagannath: 
jagannath@jagannath:~$ 


sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.5) but 2.15-0ubuntu10.6 is installed
             Depends: libc-dev-bin (= 2.15-0ubuntu10.5)
E: Unmet dependencies. Try using -f.
jagannath@jagannath:~$ 



 sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del update-manager 1:0.156.14.15 [609 kB]
Del youtube-dl 2014.07.15-0~webupd8~precise [393 kB]
Del update-manager-core 1:0.156.14.15 [185 kB]
Del skype-bin 4.3.0.37-0ubuntu0.12.04.1 [20.1 MB]
jagannath@jagannath:~$ 



jagannath@jagannath:~$ sudo apt-get update
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                                                                                        
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                                                                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg                                                                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg                                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg                                                                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                                                                                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release                                                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                                                                       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg                                                                                                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                                                                                                                
Get:1 [http://nginx.org](http://nginx.org) precise Release.gpg [287 B]                                                                                                                      
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release                                                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                                                                                                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                                                                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                                                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                                                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                                                                                       
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release                                                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources                                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources                                                                                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Sources                                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Sources                                                                                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main amd64 Packages                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                                                       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                                                                                
Hit [http://nginx.org](http://nginx.org) precise Release                                                                                                                                    
Ign [http://nginx.org](http://nginx.org) precise Release                                                                                                                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted amd64 Packages                                                                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe amd64 Packages                                                                                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse amd64 Packages                                                                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main i386 Packages                                                                                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages                                                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages                                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages                                                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex                                                                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                                                                                
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex                                                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex                                                                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources                                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Sources                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Sources                                                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Sources                                                                                                     
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                                                                              
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise/main amd64 Packages                                                                                                                
Ign [http://nginx.org](http://nginx.org) precise/nginx Sources/DiffIndex                                                                                                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main amd64 Packages                                                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted amd64 Packages                                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe amd64 Packages                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse amd64 Packages                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main i386 Packages                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted i386 Packages                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe i386 Packages                                                                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse i386 Packages                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex                                                                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                                                                                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                                                 
Ign [http://nginx.org](http://nginx.org) precise/nginx amd64 Packages/DiffIndex                                                                                                             
Ign [http://nginx.org](http://nginx.org) precise/nginx i386 Packages/DiffIndex                                                                                                              
Ign [http://nginx.org](http://nginx.org) precise/nginx TranslationIndex                                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources                                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Sources                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources                                                                                                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages                                                                                                                 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                                                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                                                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main amd64 Packages                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted amd64 Packages                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe amd64 Packages                                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse amd64 Packages                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted i386 Packages                                                                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                                                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main TranslationIndex                                                                                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en                                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en                                                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Translation-en                                                                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Translation-en                                                                                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en                                                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Translation-en                                                                                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Translation-en                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Translation-en                                                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN                                                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources                                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages                                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages                                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages                                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages                                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages                                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages                                                                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_IN                                                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_IN                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [http://nginx.org](http://nginx.org) precise/nginx Sources     
Hit [http://nginx.org](http://nginx.org) precise/nginx amd64 Packages
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_IN
Hit [http://nginx.org](http://nginx.org) precise/nginx i386 Packages
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en
Ign [http://nginx.org](http://nginx.org) precise/nginx Translation-en_IN
Ign [http://nginx.org](http://nginx.org) precise/nginx Translation-en
Fetched 287 B in 5s (53 B/s)
Reading package lists... Done
W: GPG error: [http://nginx.org](http://nginx.org) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ABF5BD827BD9BF62
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)

---

### Post by jagannath2 on 2014-08-11
i already run fsck, its clean
getting input/output error 

jagannath@jagannath:~$ ls -l /usr/include/
ls: cannot access /usr/include/rpcsvc: Input/output error
total 1512


d?????????  ? ?    ?         ?            ? rpcsvc

---

### Post by kc1di on 2014-08-11
you can try this see if it clears the problem:
```

sudo rm /var/lib/apt/lists/* 
sudo apt-get update 
```

---

### Post by jagannath2 on 2014-08-11
getting this error 

sudo rm /var/lib/apt/lists/*
[sudo] password for jagannath: 
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
jagannath@jagannath:~$

---

### Post by jagannath2 on 2014-08-11
please tell me how to remove this input/output error 

jagannath@jagannath:~$ ls -l /usr/include/
ls: cannot access /usr/include/rpcsvc: Input/output error
total 1512


d?????????  ? ?    ?         ?            ? rpcsvc

the permission is showing questiion mark

---

### Post by Bashing-om on 2014-08-11
jagannath2; Hello;

As you know there are more than 1 issue at play here.
The place to start - in my opinion - is to clean up the index files:
> 
W: GPG error: [http://nginx.org](http://nginx.org) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ABF5BD827BD9BF62
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_b inary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_b inary-i386_Packages)

Post back the outputs - Please, Between code tags - of terminal commands:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
We get the index files straight, then look at a general house cleaning to reduce the overhead.
Then, finally, we can look at the specific issue.

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by TheFu on 2014-08-11
Input/output errors are bad. THAT is the most important issue, IMHO.

Time to run **badblocks**. But you can't get it installed via the package until that is corrected.  Fun fun.  Boot off a liveCD/flash, install it and run against the unmounted partition.

Did you check for out-of-storage issues too? We still need to knwo that too.

---

