---
title: "Un able to locate package"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by noni1 on 2012-06-03
Hi all 
I was trying to install   a non repository ubuntu  and I get This message > un able to locate a package  if I run The instruction to install the leibrary or the package
 here the Instructions and command , which I used  
 sudo apt-add-repository ppa:roblib/ppa 
sudo apt-get update
sudo apt-get install librl-examples
 ( after this command I get this Message 
E: Unable to locate package librl-examples
  then I did this command 

sudo apt-cache search librl and got >>
librlog-dev - flexible message logging library - development files
librlog5 - flexible message logging library

 Iam realy have no Idea about this problem and I am a new for  Ubuntu 
 How I can fix this Problem 
   HELP ME PLEASE 
 Thank you>

---

### Post by mikewhatever on 2012-06-03
I don't think adding the PPA worked. Do you see it amoung the output lines of 'apt-get update'?

Try the following instead:
```
sudo add-apt-repository ppa:roblib/ppa 
```

---

### Post by raja.genupula on 2012-06-03
gives us the terminal commands what you have entered and as well as the output you got after entering . copy and paste the terminal text and place it between code tags by clicking at Hash(#) in this window .

---

### Post by noni1 on 2012-06-04
Than for your answer
 I entered the command 
sudo add-apt-repository ppa:roblib/ppa 
but i got the same result
 >>>>>>>>>>
  I entered just 3 commands  and I could't complete  the other commands , because these depend on the Examples file , which is not installed
   ok ,  
[COLOR=Red]1.sudo add-apt-repository ppa:roblib/ppa[/COLOR]
the output is >>
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.o5qPoUsG4q --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 36050FC70315AE8A97425E1C6916B28701172DC4
gpg: requesting key 01172DC4 from hkp server keyserver.ubuntu.com
gpg: key 01172DC4: "Launchpad PPA for Robotics Library Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
[COLOR=Red]2.sudo apt-get update[/COLOR]
the output is >>>>
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise InRelease                             
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates Release                       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main Sources                          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe Sources                      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main i386 Packages                    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [13.7 kB]       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe i386 Packages       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main TranslationIndex        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe TranslationIndex    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main Sources         
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted Sources   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe Sources     
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [4,522 B]   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [696 B]   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [45.0 kB] 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [10.9 kB]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,393 B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse Translation-en    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Fetched 126 kB in 6s (20.3 kB/s)                                               
Reading package lists... Done
[COLOR=Red]3. sudo apt-get install librl-examples[/COLOR]
the output >>>>>
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package librl-examples
 >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
so I hope   to find a solution   :)

---

### Post by mikewhatever on 2012-06-04
I think I see the problem - there is no librl for precise in the PPA, not sure why. If you click "View package details" and then expand any of the librl ones, then librl-examples is there, but, as said, it hasn't been built for Precise.
For the sake of sanity check, what's the output of the following:

```
apt-cache search solid
```

(that package is available for Precise)


If I am right, you'll either need to contact the PPA maintainer about librl for 12.04, or use a different release.

---

