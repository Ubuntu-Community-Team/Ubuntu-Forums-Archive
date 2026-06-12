---
title: "Non-selectable entries in update manager"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by Sale on 2010-10-23
I've done online upgrade to 10.10 without any particular problems. After setting up the 3rd part repositories again I now have  a list of non-selectable entries in Update manager - please see the attached image. 

What can I do to remove those from the Update manager (or install what they suggest)?

Thanks

---

### Post by sikander3786 on 2010-10-23
A dumb question at first, but did you tried to refresh the package information by click the "Check" button and see if they go away?

---

### Post by Sale on 2010-10-23
Yes, I tried that :)

Actually, several other packages updater regularly since I noticed these that I can't select (and that won't go away).

---

### Post by sikander3786 on 2010-10-23
From terminal, what is the output of

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

---

### Post by Frogs Hair on 2010-10-23
I have had this happen and the packages became available a short time later . If they have been there for a day or more I would be curious too.

---

### Post by Sale on 2010-10-24
> **Frogs Hair said:**
> I have had this happen and the packages became available a short time later . If they have been there for a day or more I would be curious too.

I think I had a case like that before too. But this time, the packages have been in this "non-selectable" state for about a week now.

---

### Post by Sale on 2010-10-24
Here is the output of sudo apt-get update:

```
sale@sale-at-home:~$ sudo apt-get update
[sudo] password for sale: 
Hit http://rs.archive.ubuntu.com maverick-backports Release.gpg
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ maverick/main Translation-en   
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.ubuntu.com maverick Release.gpg                             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US          
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US      
Hit http://archive.ubuntu.com maverick-updates Release.gpg                     
Get:1 http://dl.google.com stable Release.gpg [191B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://download.virtualbox.org maverick Release.gpg                        
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ maverick/main Translation-en_US
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://archive.canonical.com maverick Release                              
Ign http://rs.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US  
Hit http://mirrors.ucr.ac.cr maverick Release.gpg                              
Ign http://mirrors.ucr.ac.cr/medibuntu/ maverick/free Translation-en           
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://download.bitdefender.com bitdefender Release.gpg                    
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-security Release.gpg                    
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Get:2 http://dl.google.com stable Release [1,310B]                             
Ign http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://mirrors.ucr.ac.cr/medibuntu/ maverick/free Translation-en_US        
Ign http://mirrors.ucr.ac.cr/medibuntu/ maverick/non-free Translation-en       
Ign http://mirrors.ucr.ac.cr/medibuntu/ maverick/non-free Translation-en_US    
Ign http://ppa.launchpad.net/cdemu/ppa/ubuntu/ maverick/main Translation-en    
Ign http://ppa.launchpad.net/cdemu/ppa/ubuntu/ maverick/main Translation-en_US 
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/ maverick/main Translation-en
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en    
Hit http://download.virtualbox.org maverick Release                            
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US 
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Get:3 http://dl.google.com stable/main amd64 Packages [969B]                   
Hit http://mirrors.ucr.ac.cr maverick Release                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://rs.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Hit http://archive.canonical.com maverick/partner amd64 Packages               
Hit http://archive.ubuntu.com maverick Release                                 
Hit http://archive.ubuntu.com maverick-updates Release                         
Ign http://download.bitdefender.com/repos/deb/ bitdefender/non-free Translation-en
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://download.virtualbox.org maverick/non-free amd64 Packages            
Hit http://archive.ubuntu.com maverick-security Release                        
Hit http://mirrors.ucr.ac.cr maverick/free Sources                             
Ign http://rs.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://archive.ubuntu.com maverick/restricted Sources                      
Hit http://archive.ubuntu.com maverick/main Sources                            
Hit http://archive.ubuntu.com maverick/universe Sources                        
Hit http://archive.ubuntu.com maverick/multiverse Sources                      
Hit http://archive.ubuntu.com maverick/restricted amd64 Packages               
Ign http://download.bitdefender.com/repos/deb/ bitdefender/non-free Translation-en_US
Hit http://download.bitdefender.com bitdefender Release                        
Hit http://archive.ubuntu.com maverick/main amd64 Packages                     
Hit http://archive.ubuntu.com maverick/universe amd64 Packages                 
Hit http://archive.ubuntu.com maverick/multiverse amd64 Packages               
Hit http://archive.ubuntu.com maverick-updates/restricted Sources              
Hit http://archive.ubuntu.com maverick-updates/main Sources                    
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://mirrors.ucr.ac.cr maverick/non-free Sources                         
Hit http://mirrors.ucr.ac.cr maverick/free amd64 Packages                      
Hit http://mirrors.ucr.ac.cr maverick/non-free amd64 Packages                  
Hit http://archive.ubuntu.com maverick-updates/universe Sources                
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources              
Hit http://archive.ubuntu.com maverick-updates/restricted amd64 Packages       
Hit http://archive.ubuntu.com maverick-updates/main amd64 Packages             
Hit http://archive.ubuntu.com maverick-updates/universe amd64 Packages         
Ign http://rs.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://archive.ubuntu.com maverick-updates/multiverse amd64 Packages       
Hit http://archive.ubuntu.com maverick-security/restricted Sources             
Hit http://archive.ubuntu.com maverick-security/main Sources         
Hit http://archive.ubuntu.com maverick-security/universe Sources     
Hit http://archive.ubuntu.com maverick-security/multiverse Sources   
Ign http://rs.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Hit http://archive.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://archive.ubuntu.com maverick-security/main amd64 Packages
Hit http://archive.ubuntu.com maverick-security/universe amd64 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse amd64 Packages
Ign http://rs.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://rs.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://rs.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://rs.archive.ubuntu.com maverick-backports Release                  
Ign http://download.bitdefender.com bitdefender/non-free amd64 Packages      
Hit http://rs.archive.ubuntu.com maverick-backports/main Sources
Hit http://rs.archive.ubuntu.com maverick-backports/restricted Sources
Hit http://rs.archive.ubuntu.com maverick-backports/universe Sources
Ign http://download.bitdefender.com bitdefender/non-free amd64 Packages
Hit http://download.bitdefender.com bitdefender/non-free amd64 Packages
Hit http://rs.archive.ubuntu.com maverick-backports/multiverse Sources         
Hit http://rs.archive.ubuntu.com maverick-backports/main amd64 Packages        
Hit http://rs.archive.ubuntu.com maverick-backports/restricted amd64 Packages  
Hit http://rs.archive.ubuntu.com maverick-backports/universe amd64 Packages    
Hit http://rs.archive.ubuntu.com maverick-backports/multiverse amd64 Packages  
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/ maverick/restricted Translation-en_US
Fetched 2,470B in 1min 13s (34B/s)
Reading package lists... Done

```

and this is the output of sudo apt-get upgrade

```
sale@sale-at-home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libboost-date-time-dev libboost-dev libboost-filesystem-dev
  libboost-graph-dev libboost-iostreams-dev libboost-program-options-dev
  libboost-regex-dev libboost-serialization-dev libboost-signals-dev
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

---

### Post by efflandt on 2010-10-24
Were you using libboost for anything in 10.04?  You might open Synaptic, put **boost** in quick search, and see if anything there is marked **installed**, but maybe isn't completely.  My Maverick installed from beta and updated to release has nothing there marked as installed.

I needed libboost to compile some small program on one system, but I forget what that was for.

When I recently upgraded system from 32-bit 9.10 to 10.04 on one system before Maverick was released, Synaptic made it appear that most recent flashplugin-installer was installed, but it did not work in Firefox and was not listed in its Add-ons.  ubuntu-restricted-extras also became uninstalled by the upgrade, but installing that did not restore flash.  I had to mark flashplugin-installer for Reinstallation before it would work.

---

### Post by Sale on 2010-10-24
Thanks efflandt, you called it out right. It seems that a number of libboost libraries needed to be upgraded/installed/removed. So the problem is solved now :)

Funny thing is that sudo apt-get upgrade didn't do it, and not even the "mark all upgrades" in Synaptic. After I did quick search for "boost" in Synaptic, I had to manually select one of the libraries marked with "!", right-click on it and select "mark for upgrade". After that, Synaptic did the rest of the work.

Even funnier thing is that I have no idea what "libboost" is, or what I might have used it for :-D

Thanks again

---

