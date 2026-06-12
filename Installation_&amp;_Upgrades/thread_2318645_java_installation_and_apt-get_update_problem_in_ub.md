---
title: "java installation and apt-get update problem in ubuntu"
date: 2016-03-28
forum: Installation &amp; Upgrades
---

### Post by mrityunjay23 on 2016-03-28
I am wanted to instal java on my ubuntu 12.04.
```
java ~version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: apt-get install <selected package>
```

```
apt-get install default-jre

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 default-jre : Depends: default-jre-headless (= 1:1.6-43ubuntu2) but it is not going to be installed
               Depends: openjdk-6-jre (>= 6b23~pre11-1ubuntu1~) but it is not going to be installed
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to correct problems, you have held broken packages.
```

apt-get update is also not working properly


```
apt-get update

Ign http://in.old-releases.ubuntu.com precise Release.gpg
Ign http://in.old-releases.ubuntu.com precise-updates Release.gpg              
Ign http://in.old-releases.ubuntu.com precise-backports Release.gpg            
Ign http://in.old-releases.ubuntu.com precise Release                          
Ign http://in.old-releases.ubuntu.com precise-updates Release                  
Ign http://in.old-releases.ubuntu.com precise-backports Release                
Ign http://in.old-releases.ubuntu.com precise/main TranslationIndex            
Ign http://in.old-releases.ubuntu.com precise/multiverse TranslationIndex      
Ign http://in.old-releases.ubuntu.com precise/restricted TranslationIndex      
Ign http://in.old-releases.ubuntu.com precise/universe TranslationIndex        
Ign http://in.old-releases.ubuntu.com precise-updates/main TranslationIndex    
Ign http://in.old-releases.ubuntu.com precise-updates/multiverse TranslationIndex
Ign http://in.old-releases.ubuntu.com precise-updates/restricted TranslationIndex
Ign http://in.old-releases.ubuntu.com precise-updates/universe TranslationIndex
Ign http://in.old-releases.ubuntu.com precise-backports/main TranslationIndex  
Ign http://in.old-releases.ubuntu.com precise-backports/multiverse TranslationIndex
Ign http://in.old-releases.ubuntu.com precise-backports/restricted TranslationIndex
Ign http://in.old-releases.ubuntu.com precise-backports/universe TranslationIndex
Hit http://dl.google.com stable Release.gpg                                    
Err http://in.old-releases.ubuntu.com precise/main Sources                     
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/restricted Sources               
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/universe Sources                 
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/multiverse Sources               
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/main amd64 Packages              
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/restricted amd64 Packages        
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/universe amd64 Packages          
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/multiverse amd64 Packages        
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/main i386 Packages               
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/restricted i386 Packages         
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/universe i386 Packages           
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise/multiverse i386 Packages         
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/main Sources             
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/restricted Sources       
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/universe Sources         
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/multiverse Sources       
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/main amd64 Packages      
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/restricted amd64 Packages
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/universe amd64 Packages  
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/multiverse amd64 Packages
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/main i386 Packages       
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/restricted i386 Packages 
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/universe i386 Packages   
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-updates/multiverse i386 Packages 
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/main Sources           
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/restricted Sources     
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/universe Sources       
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/multiverse Sources     
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/main amd64 Packages    
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/restricted amd64 Packages
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/universe amd64 Packages
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/multiverse amd64 Packages
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/main i386 Packages     
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/restricted i386 Packages
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/universe i386 Packages 
  503  Service Unavailable
Err http://in.old-releases.ubuntu.com precise-backports/multiverse i386 Packages
  503  Service Unavailable
Ign http://in.old-releases.ubuntu.com precise/main Translation-en_IN           
Ign http://in.old-releases.ubuntu.com precise/main Translation-en              
Ign http://in.old-releases.ubuntu.com precise/multiverse Translation-en_IN     
Ign http://in.old-releases.ubuntu.com precise/multiverse Translation-en        
Ign http://in.old-releases.ubuntu.com precise/restricted Translation-en_IN     
Ign http://in.old-releases.ubuntu.com precise/restricted Translation-en        
Ign http://in.old-releases.ubuntu.com precise/universe Translation-en_IN       
Ign http://in.old-releases.ubuntu.com precise/universe Translation-en          
Ign http://in.old-releases.ubuntu.com precise-updates/main Translation-en_IN   
Ign http://in.old-releases.ubuntu.com precise-updates/main Translation-en      
Ign http://in.old-releases.ubuntu.com precise-updates/multiverse Translation-en_IN
Ign http://in.old-releases.ubuntu.com precise-updates/multiverse Translation-en
Ign http://in.old-releases.ubuntu.com precise-updates/restricted Translation-en_IN
Ign http://in.old-releases.ubuntu.com precise-updates/restricted Translation-en
Ign http://in.old-releases.ubuntu.com precise-updates/universe Translation-en_IN
Ign http://in.old-releases.ubuntu.com precise-updates/universe Translation-en  
Ign http://in.old-releases.ubuntu.com precise-backports/main Translation-en_IN 
Ign http://in.old-releases.ubuntu.com precise-backports/main Translation-en    
Ign http://in.old-releases.ubuntu.com precise-backports/multiverse Translation-en_IN
Ign http://in.old-releases.ubuntu.com precise-backports/multiverse Translation-en
Ign http://in.old-releases.ubuntu.com precise-backports/restricted Translation-en_IN
Ign http://in.old-releases.ubuntu.com precise-backports/restricted Translation-en
Ign http://in.old-releases.ubuntu.com precise-backports/universe Translation-en_IN
Ign http://in.old-releases.ubuntu.com precise-backports/universe Translation-en
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.ubuntu.com precise Release.gpg                              
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://old-releases.ubuntu.com precise-security Release.gpg                
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://linux.dropbox.com precise Release.gpg                               
Hit http://archive.ubuntu.com precise Release                                  
Ign http://old-releases.ubuntu.com precise-security Release                    
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://archive.canonical.com precise Release                               
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://linux.dropbox.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://linux.dropbox.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Translation-en                       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://linux.dropbox.com precise/main i386 Packages                        
Hit http://archive.canonical.com precise/partner TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted Sources                       
Ign http://dl.google.com stable/main Translation-en_IN                         
Hit http://archive.canonical.com precise/partner Sources                       
Ign http://dl.google.com stable/main Translation-en                            
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.canonical.com precise/partner amd64 Packages                
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://archive.canonical.com precise/partner TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.canonical.com precise/partner Translation-en                
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://archive.canonical.com precise/partner Translation-en                
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Ign http://old-releases.ubuntu.com precise-security/main TranslationIndex      
Ign http://extras.ubuntu.com precise/main Translation-en_IN                    
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Ign http://old-releases.ubuntu.com precise-security/multiverse TranslationIndex
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://old-releases.ubuntu.com precise-security/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Ign http://old-releases.ubuntu.com precise-security/universe TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex       
Ign http://linux.dropbox.com precise/main Translation-en_IN           
Hit http://archive.ubuntu.com precise/main Translation-en
Ign http://linux.dropbox.com precise/main Translation-en                       
Hit http://archive.ubuntu.com precise/multiverse Translation-en       
Hit http://archive.ubuntu.com precise/restricted Translation-en         
Hit http://archive.ubuntu.com precise/universe Translation-en
Err http://old-releases.ubuntu.com precise-security/main Sources               
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/restricted Sources
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/universe Sources
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/multiverse Sources
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/main amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/restricted amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/universe amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/multiverse amd64 Packages
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/main i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/restricted i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/universe i386 Packages
  404  Not Found
Err http://old-releases.ubuntu.com precise-security/multiverse i386 Packages
  404  Not Found
Ign http://old-releases.ubuntu.com precise-security/main Translation-en_IN
Ign http://old-releases.ubuntu.com precise-security/main Translation-en
Ign http://old-releases.ubuntu.com precise-security/multiverse Translation-en_IN
Ign http://old-releases.ubuntu.com precise-security/multiverse Translation-en
Ign http://old-releases.ubuntu.com precise-security/restricted Translation-en_IN
Ign http://old-releases.ubuntu.com precise-security/restricted Translation-en
Ign http://old-releases.ubuntu.com precise-security/universe Translation-en_IN
Ign http://old-releases.ubuntu.com precise-security/universe Translation-en
W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://in.old-releases.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages  503  Service Unavailable

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
How to fix apt-get update?
How to fix broken packages for java?
I have tried apt-get autoclean, autoremove and purge command it has not worked for me.

---

### Post by ajgreeny on 2016-03-28
You seem to have a lot of **old-releases** repositories enabled for precise, which as far as I'm aware will not exist yet as precise is not yet end-of-life.
Why are they there; did you edit software-sources to add them manually?

I can't really help with your java problem, and I haven't used 12.04 for a long time so have no way to test your situation on a system here.

---

