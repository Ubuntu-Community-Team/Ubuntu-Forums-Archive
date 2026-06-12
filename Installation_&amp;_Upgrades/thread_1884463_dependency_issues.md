---
title: "dependency issues"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by mynameissagarbhatt on 2011-11-21
my software center was not working so i tried to remove and reinstall it.
it got removed.....but now when i try to install it using:
```
sudo apt-get install software-center
```

this happens:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-center : Depends: gir1.2-glib-2.0 (>= 1.31) but 1.30.0-0ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.

```

i have tried everything........even reinstalled  gir1.2-glib-2.0    but nothing works........

any clue?

---

### Post by mynameissagarbhatt on 2011-11-22
anyone?

---

### Post by mikewhatever on 2011-11-22
Have you been playing with repositories? Have you added any PPAs?
Can you post the output of **sudo apt-get update**.

---

### Post by mynameissagarbhatt on 2011-11-22
it  gets updated fine!
```
Fetched 683 kB in 41s (16.4 kB/s)
Reading package lists... Done
```

---

### Post by |{urse on 2011-11-22
sudo apt-get install -f 

?

---

### Post by mikewhatever on 2011-11-22
> **mynameissagarbhatt said:**
> it  gets updated fine!
```
Fetched 683 kB in 41s (16.4 kB/s)
Reading package lists... Done
```

Well, thanks, but I really wanted to see the repositories. Whether it updates fine or not is irrelevant.

---

### Post by mynameissagarbhatt on 2011-11-22
oh....
here:
```
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://in.archive.ubuntu.com oneiric InRelease                             
Ign http://in.archive.ubuntu.com oneiric-updates InRelease           
Ign http://in.archive.ubuntu.com oneiric-security InRelease          
Ign http://ppa.launchpad.net oneiric InRelease                       
Ign http://ppa.launchpad.net oneiric InRelease                       
Hit http://archive.canonical.com oneiric Release.gpg                 
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://in.archive.ubuntu.com oneiric Release.gpg                           
Hit http://in.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Get:3 http://dl.google.com stable Release [1,347 B]                            
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://in.archive.ubuntu.com oneiric-security Release.gpg                  
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://in.archive.ubuntu.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release                                   
Get:4 http://dl.google.com stable/main i386 Packages [1,220 B]                 
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://in.archive.ubuntu.com oneiric-updates Release                       
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://in.archive.ubuntu.com oneiric-security Release                      
Hit http://in.archive.ubuntu.com oneiric/main Sources                          
Hit http://in.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://in.archive.ubuntu.com oneiric/universe Sources                      
Hit http://in.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://in.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://in.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://in.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://in.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://in.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://in.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://in.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://in.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://in.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://in.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://in.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://in.archive.ubuntu.com oneiric-updates/main i386 Packages  
Hit http://in.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://in.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://in.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://in.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://in.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://in.archive.ubuntu.com oneiric-security/main Sources                 
Hit http://in.archive.ubuntu.com oneiric-security/restricted Sources           
Hit http://in.archive.ubuntu.com oneiric-security/universe Sources             
Hit http://in.archive.ubuntu.com oneiric-security/multiverse Sources           
Hit http://in.archive.ubuntu.com oneiric-security/main i386 Packages           
Hit http://in.archive.ubuntu.com oneiric-security/restricted i386 Packages     
Hit http://in.archive.ubuntu.com oneiric-security/universe i386 Packages       
Hit http://in.archive.ubuntu.com oneiric-security/multiverse i386 Packages     
Hit http://in.archive.ubuntu.com oneiric-security/main TranslationIndex        
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Hit http://in.archive.ubuntu.com oneiric-security/multiverse TranslationIndex  
Ign http://archive.canonical.com oneiric/partner Translation-en                
Hit http://in.archive.ubuntu.com oneiric-security/restricted TranslationIndex  
Hit http://in.archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://in.archive.ubuntu.com oneiric/main Translation-en         
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://dl.google.com stable/main Translation-en                  
Hit http://in.archive.ubuntu.com oneiric/multiverse Translation-en   
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Hit http://in.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://in.archive.ubuntu.com oneiric/universe Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Hit http://in.archive.ubuntu.com oneiric-updates/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Hit http://in.archive.ubuntu.com oneiric-updates/restricted Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://in.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://in.archive.ubuntu.com oneiric-security/main Translation-en
Hit http://in.archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://in.archive.ubuntu.com oneiric-security/restricted Translation-en
Hit http://in.archive.ubuntu.com oneiric-security/universe Translation-en
Fetched 2,837 B in 1min 18s (36 B/s)
Reading package lists... Done

```

---

### Post by mynameissagarbhatt on 2011-11-22
> **|{urse said:**
> sudo apt-get install -f 

?

did that already....

heres what i get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.

```

it doesn't help...

---

### Post by raja.genupula on 2011-11-22
> **mynameissagarbhatt said:**
> my software center was not working so i tried to remove and reinstall it.
it got removed.....but now when i try to install it using:
```
sudo apt-get install software-center
```this happens:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-center : Depends: gir1.2-glib-2.0 (>= 1.31) but 1.30.0-0ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.

```i have tried everything........even reinstalled  gir1.2-glib-2.0    but nothing works........

any clue?
open synaptic and from there fix broken packages or 
do this 

sudo dpkg --configure -a

in your terminal.


I am sure that gonna help you.

---

### Post by mikewhatever on 2011-11-22
The repositories look OK, so its really odd. It seems to be trying to install the Software Center for Precise Pangolin, which depends on gir1.2-glib-2.0 (>= 1.31).

---

### Post by mynameissagarbhatt on 2011-11-22
nothing happens! here:
```
sagar@sagar-Satellite-A200:~$ sudo dpkg --configure -a
sagar@sagar-Satellite-A200:~$

```

and apparently 11.10 does not have synaptic!

---

### Post by raja.genupula on 2011-11-23
install synaptic 
that will help us to fix the issue.

```
sudo apt-get install synaptic
```

---

### Post by mynameissagarbhatt on 2011-11-23
did that........synaptic dissapears before u can blink an eye........

---

### Post by raja.genupula on 2011-11-24
Well this is final i can give you , I am sure about this.

get the packages from the [http://packages.ubuntu.com/oneiric/gir1.2-glib-2.0](http://packages.ubuntu.com/oneiric/gir1.2-glib-2.0)

and install them with 
sudo dpkg -i <filename>.deb

and then again make a try to install software center

---

### Post by mynameissagarbhatt on 2011-11-24
thnx man!.....well i managed to get the synaptic manager to work.......
i removed all the repository lists and then i did ´apt-get update' .....that added them again.....and synaptic started working......
as for software center, i got frustrated and reinstalled ubuntu!

---

