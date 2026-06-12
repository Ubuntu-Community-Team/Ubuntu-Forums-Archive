---
title: "problem with update manager"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by sandy0594 on 2011-05-20
Hey all,i am having problem with package manager..even after updating it shows "The package information was updated 20 days back" and sometimes a warning message on the top of the panel comes indicating the same.

Can someone kindly suggest me what to do in order to get rid of this problem.BTW mine is Ubuntu 10.10

---

### Post by kostkon on 2011-05-20
It means that the update manager has a problem fetching info from some of the repositories in your sources list.

Open a terminal, give
```
sudo apt-get update
```
and post the output here.

---

### Post by sandy0594 on 2011-05-20
I did as u said 

```

sandy@ubuntu:~$ sudo apt-get update
[sudo] password for sandy: 
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en                 
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Get:2 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/konstigt/evolution/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/konstigt/evolution/ubuntu/ maverick/main Translation-en_US
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en             
Hit http://packages.medibuntu.org maverick Release.gpg                         
Ign http://download.skype.com stable Release.gpg                               
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Hit http://extras.ubuntu.com maverick/main Sources                             
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com maverick-backports Release.gpg                
Ign http://archive.canonical.com/ubuntu/ maverick-backports/partner Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Hit http://fi.archive.ubuntu.com maverick Release.gpg                          
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US             
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:3 http://security.ubuntu.com maverick-proposed Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US         
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US
Ign http://archive.canonical.com/ubuntu/ maverick-backports/partner Translation-en_US
Hit http://archive.canonical.com maverick-updates Release.gpg                  
Ign http://archive.canonical.com/ubuntu/ maverick-updates/partner Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick-updates/partner Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_US
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/telepathy/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/telepathy/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://packages.medibuntu.org maverick Release
Ign http://security.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://fi.archive.ubuntu.com maverick-backports Release.gpg      
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Get:4 http://dl.google.com stable Release.gpg [197B]                           
Hit http://archive.canonical.com maverick-security Release.gpg                 
Ign http://archive.canonical.com/ubuntu/ maverick-security/partner Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick-security/partner Translation-en_US
Hit http://archive.canonical.com maverick-proposed Release.gpg                 
Ign http://archive.canonical.com/ubuntu/ maverick-proposed/partner Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick-proposed/partner Translation-en_US
Hit http://packages.medibuntu.org maverick/free Sources                        
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Hit http://fi.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Hit http://packages.medibuntu.org maverick/non-free Sources                    
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en_US
Hit http://packages.medibuntu.org maverick/free i386 Packages                  
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Hit http://security.ubuntu.com maverick-security Release                       
Get:5 http://security.ubuntu.com maverick-proposed Release [31.4kB]            
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://fi.archive.ubuntu.com maverick-proposed Release.gpg                 
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Hit http://packages.medibuntu.org maverick/non-free i386 Packages              
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en 
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ maverick/partner Translation-en            
Ign http://archive.canonical.com/ maverick/partner Translation-en_US         
Hit http://archive.canonical.com maverick Release                            
Hit http://archive.canonical.com maverick-backports Release                  
Hit http://archive.canonical.com maverick-updates Release                    
Hit http://archive.canonical.com maverick-security Release                   
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://archive.canonical.com maverick-proposed Release                   
Hit http://archive.canonical.com maverick Release                              
Get:6 http://dl.google.com stable Release [2,544B]                             
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://archive.canonical.com maverick/partner Sources                      
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://archive.canonical.com maverick-backports/partner Sources            
Get:7 http://dl.google.com stable Release [1,347B]                             
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_US
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_US
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://fi.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Hit http://fi.archive.ubuntu.com maverick Release                              
Hit http://fi.archive.ubuntu.com maverick-backports Release                    
Get:8 http://dl.google.com stable/non-free i386 Packages [1,010B]              
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://archive.canonical.com maverick-backports/partner i386 Packages      
Hit http://archive.canonical.com maverick-updates/partner Sources              
Hit http://archive.canonical.com maverick-updates/partner i386 Packages        
Hit http://archive.canonical.com maverick-security/partner Sources             
Hit http://archive.canonical.com maverick-security/partner i386 Packages       
Get:9 http://dl.google.com stable/main i386 Packages [1,082B]                  
Hit http://archive.canonical.com maverick-proposed/partner Sources             
Hit http://archive.canonical.com maverick-proposed/partner i386 Packages       
Ign http://download.skype.com stable Release                                   
Get:10 http://dl.google.com stable/main i386 Packages [764B]                   
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Hit http://fi.archive.ubuntu.com maverick-updates Release                      
Hit http://fi.archive.ubuntu.com maverick-proposed Release                   
Hit http://archive.canonical.com maverick/partner i386 Packages                
Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
Hit http://fi.archive.ubuntu.com maverick/main Sources                       
Hit http://fi.archive.ubuntu.com maverick/restricted Sources
Hit http://fi.archive.ubuntu.com maverick/multiverse Sources
Hit http://fi.archive.ubuntu.com maverick/universe Sources
Hit http://fi.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://fi.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://fi.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://fi.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://fi.archive.ubuntu.com maverick-backports/main Sources               
Hit http://fi.archive.ubuntu.com maverick-backports/restricted Sources       
Ign http://download.skype.com stable/non-free i386 Packages/DiffIndex        
Hit http://fi.archive.ubuntu.com maverick-backports/universe Sources           
Hit http://fi.archive.ubuntu.com maverick-backports/multiverse Sources         
Hit http://fi.archive.ubuntu.com maverick-backports/main i386 Packages         
Hit http://download.skype.com stable/non-free i386 Packages                    
Hit http://fi.archive.ubuntu.com maverick-backports/restricted i386 Packages   
Hit http://fi.archive.ubuntu.com maverick-backports/universe i386 Packages     
Hit http://fi.archive.ubuntu.com maverick-backports/multiverse i386 Packages   
Hit http://fi.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://fi.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://fi.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://fi.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://fi.archive.ubuntu.com maverick-updates/main i386 Packages           
Hit http://fi.archive.ubuntu.com maverick-updates/restricted i386 Packages     
Hit http://fi.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Hit http://fi.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://fi.archive.ubuntu.com maverick-proposed/restricted Sources          
Hit http://fi.archive.ubuntu.com maverick-proposed/main Sources                
Hit http://fi.archive.ubuntu.com maverick-proposed/multiverse Sources          
Hit http://fi.archive.ubuntu.com maverick-proposed/universe Sources            
Hit http://fi.archive.ubuntu.com maverick-proposed/restricted i386 Packages    
Hit http://fi.archive.ubuntu.com maverick-proposed/main i386 Packages          
Get:11 http://security.ubuntu.com maverick-proposed/main Sources [52.3kB]      
Hit http://fi.archive.ubuntu.com maverick-proposed/multiverse i386 Packages    
Hit http://fi.archive.ubuntu.com maverick-proposed/universe i386 Packages      
Get:12 http://security.ubuntu.com maverick-proposed/restricted Sources [14B]   
Get:13 http://security.ubuntu.com maverick-proposed/universe Sources [5,231B]  
Get:14 http://security.ubuntu.com maverick-proposed/multiverse Sources [640B]  
Get:15 http://security.ubuntu.com maverick-proposed/main i386 Packages [135kB] 
Get:16 http://security.ubuntu.com maverick-proposed/restricted i386 Packages [14B]
Get:17 http://security.ubuntu.com maverick-proposed/universe i386 Packages [15.5kB]
Get:18 http://security.ubuntu.com maverick-proposed/multiverse i386 Packages [1,124B]
Fetched 248kB in 14s (17.6kB/s)                                                
W: Failed to fetch http://ppa.launchpad.net/konstigt/evolution/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/konstigt/evolution/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
sandy@ubuntu:~$ 


```

But when i open update manager..i still see that "The package manager was last updated  20 days ago"

---

### Post by Rubi1200 on 2011-05-20
Hi,
are you behind a firewall or do you use a proxy? There are some 404 errors in the output you posted.

I suggest you do the following:

System > Administration > Synaptic Package Manager > Settings > Repositories > and change the setting Download from to Main Server and then Reload.

Let us know if this helps.

---

### Post by sandy0594 on 2011-05-20
I changed the server to main..But,when reloaded some packages couldn't be downloaded..It gave me the following error

```

Failed to fetch http://ppa.launchpad.net/konstigt/evolution/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/konstigt/evolution/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

```

manually i didn't switch on any firewall and i am not using any proxy n/w

---

### Post by Rubi1200 on 2011-05-21
I wonder if their link is broken because I just tried to connect and also get a Not Found response.

You may have to wait a bit and see if the link comes back up.

---

### Post by sandy0594 on 2011-05-22
Can someone kindly explain what's going wrong with this update manager..why can't it update it's repositories..It still shows "The package manager was last updated 22 days ago"

How to get rid of this problem?

---

### Post by ivanovnegro on 2011-05-22
Maybe I would suggest you to remove the packages with the 404 errors then you should be able to update your system again.
You dont need a PPA for Evolution in my opinion, its default in Ubuntu.
Maybe you wanted a newer version as you are still on 10.10 but then I would change the PPA.

---

### Post by sandy0594 on 2011-05-22
Yeah,as u said the problem is with evolution..i removed it and the update is going well..
But,how will i get the updates for evolution mail when i removed the update source 
> 
[http://ppa.launchpad.net/konstigt/evolution/ubuntu/dists/maverick/main/source/](http://ppa.launchpad.net/konstigt/evolution/ubuntu/dists/maverick/main/source/)

Thanks for the reply

---

