---
title: "Trouble Installing Wine, Skype, Playonlinux, etc."
date: 2015-07-19
forum: Installation &amp; Upgrades
---

### Post by Neesi on 2015-07-19
My attempt at installing Wine:
I tried adding this through the software center:


    ppa:ubuntu-wine/ppa 
and I get "Failed to download repository information"


    (precise)neesi@localhost:~$  sudo add-apt-repository ppa:ubuntu-wine/ppa
    You are about to add the following PPA to your system:
    Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
    More info: [https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa)
    Press [ENTER] to continue or ctrl-c to cancel adding it


    gpg: keyring `/tmp/tmptptvoq/secring.gpg' created
    gpg: keyring `/tmp/tmptptvoq/pubring.gpg' created
    gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
    gpg: /tmp/tmptptvoq/trustdb.gpg: trustdb created
    gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
    gpg: no ultimately trusted keys found
    gpg: Total number processed: 1
    gpg:               imported: 1  (RSA: 1)
    OK
Then I entered 


    sudo apt-get update 
And the output:


    (precise)neesi@localhost:~$ sudo apt-get update
    [sudo] password for neesi: 
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
    Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) saucy Release.gpg                               
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise Release.gpg                                
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates Release.gpg                        
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security Release.gpg                       
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
    Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
    Get:1 [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg [819 B]                 
    Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) saucy Release                                   
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise Release                                    
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates Release                            
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
    Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
    Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
    Ign [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security Release                           
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
    Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner armhf Packages                
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main armhf Packages                       
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/main Sources                               
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/restricted Sources                         
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/universe Sources                           
    Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
    Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free TranslationIndex             
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/multiverse Sources                         
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/main armhf Packages                        
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/restricted armhf Packages                  
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/universe armhf Packages                    
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/multiverse armhf Packages                  
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/main TranslationIndex                      
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/multiverse TranslationIndex                
    Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main armhf Packages                       
    Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/restricted TranslationIndex                
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/universe TranslationIndex                  
    Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
    Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main armhf Packages                      
    404  Not Found [IP: 91.189.91.23 80]
    Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe armhf Packages                  
    404  Not Found [IP: 91.189.91.23 80]
    Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted armhf Packages                
    404  Not Found [IP: 91.189.91.23 80]
    Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse armhf Packages                
    404  Not Found [IP: 91.189.91.23 80]
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main Sources                       
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/restricted Sources                 
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe Sources                   
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/multiverse Sources                 
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main armhf Packages   
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/restricted armhf Packages          
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe armhf Packages            
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/multiverse armhf Packages          
    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main TranslationIndex              
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/multiverse             TranslationIndex
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/restricted TranslationIndex        
     Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe TranslationIndex                                                       Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main Sources         
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/restricted Sources                
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe Sources                  
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/multiverse Sources                
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main armhf Packages               
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/restricted armhf Packages
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe armhf Packages
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/multiverse armhf Packages
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main TranslationIndex             
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/multiverse TranslationIndex       
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/restricted TranslationIndex
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe TranslationIndex
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/main Translation-en                        
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/multiverse Translation-en                  
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/restricted Translation-en     
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise/universe Translation-en                    
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main Translation-en                
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/multiverse Translation-en          
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/restricted Translation-en          
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe Translation-en            
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main Translation-en               
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/multiverse Translation-en         
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/restricted Translation-en         
    Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe Translation-en           
    Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
    Err [http://repository.spotify.com](http://repository.spotify.com) stable/non-free armhf Packages  
    404  Not Found [IP: 54.192.55.157 80]
    Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en
    Fetched 819 B in 8s (92 B/s)                                                   
    W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable Release: The     following signatures couldn't be verified because the public key is not   available: NO_PUBKEY 13B00F1FD2C19886
    W: Failed to fetch [http://deb.playonlinux.com/dists/saucy/Release](http://deb.playonlinux.com/dists/saucy/Release)    Unable to find expected entry 'main/binary-armhf/Packages' in Release file   (Wrong sources.list entry or malformed file)


    W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-armhf/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]


    W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-armhf/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]


    W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-armhf/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]


    W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-armhf/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-armhf/Packages)  404  Not Found [IP: 91.189.91.23 80]


    W: Failed to fetch [http://repository.spotify.com/dists/stable/non-free/binary-armhf/Packages](http://repository.spotify.com/dists/stable/non-free/binary-armhf/Packages)  404  Not Found [IP: 54.192.55.157 80]


    E: Some index files failed to download. They have been ignored, or old ones used instead.


Then I tried:


    sudo apt-get install -y wine1.7
And the output:
    
    [sudo] password for neesi: 
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    E: Unable to locate package wine1.7
    E: Couldn't find any package by regex 'wine1.7'
Can't install photoshop without Wine.
I try to install playonlinux from the software center but get this:


"Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."


I face similar issues when trying to install things like Skype.
Please help me resolve this issue, I have tried much more than what is above but nothing has worked.
(Also, my version won't upgrade)

---

### Post by Neesi on 2016-01-16
bump

---

### Post by ian-weisser on 2016-01-16
The simple answer to your question is that your system is being truthful: There is no package called "wine1.7"
1.6 is the latest in the Ubuntu repositories.
That PPA seems to max out at 1.6 for your version of Ubuntu (12.04). Other, newer versions of Ubuntu have up to 1.8...but not yours.


Do you really need playonlinux from Saucy (13.10)?
Mixing versions like that is usually a very bad idea, as you are discovering. You should be using their 12.04 sources.
Delete the source, uninstall *all* the software from that source, autoremove all the dependencies, and clean your package cache. Flush away everything 13.10-related.
That should fix your problem.
Then add the proper 12.04 source, and reinstall your favorite games from that source.
That should keep your problem fixed.

---

