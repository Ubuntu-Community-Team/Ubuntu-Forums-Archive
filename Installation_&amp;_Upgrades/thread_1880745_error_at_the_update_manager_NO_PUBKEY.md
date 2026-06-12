---
title: "error at the update manager NO_PUBKEY"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2011-11-14
Hi!

I am getting the following error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBCxxxxxxxxxxxx

Thanks for your help!

---

### Post by subehsharma on 2011-11-14
Type this command into the terminal ("Applications > Accessories > Terminal")
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

And then add the hexadecimal numbers to the command (again, these are my keys from my error. Make sure to use your own):
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5

---

### Post by fantab on 2011-11-14
> **Peter2009 said:**
> Hi!

I am getting the following error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBCxxxxxxxxxxxx

Thanks for your help!

What kind of Ubuntu are you using? Medibuntu? what version?

---

### Post by Peter2009 on 2011-11-14
> **fantab said:**
> What kind of Ubuntu are you using? Medibuntu? what version?

I am using 10.04 (lucid) kernel 2.6.32-35-generic

---

### Post by Peter2009 on 2011-11-14
> **subehsharma said:**
> Type this command into the terminal ("Applications > Accessories > Terminal")
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys

And then add the hexadecimal numbers to the command (again, these are my keys from my error. Make sure to use your own):
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5

Hi! 

I did that!
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys + (my key on the error message)

Got a reply: 1 key imported 

and now there is not error message.

But every time I trying to run the Update Manager keep saying downloading 82 or 82 files and you look at the detail and its failing to get some package. Is there a log for this update manage?

---

### Post by subehsharma on 2011-11-14
pls paste the output sudo apt-get update

---

### Post by Peter2009 on 2011-11-21
> **subehsharma said:**
> pls paste the output sudo apt-get update

here its:

```
Hit http://packages.medibuntu.org lucid Release.gpg
Hit http://security.ubuntu.com lucid-security Release.gpg                                                       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB                                    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB                              
Hit http://gb.archive.ubuntu.com lucid Release.gpg                                                              
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB                                           
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB                                     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB                                
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB                              
Hit http://security.ubuntu.com lucid-security Release                                                           
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB                                       
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB                
Hit http://gb.archive.ubuntu.com lucid-updates Release.gpg                                 
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB              
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB        
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB          
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB        
Hit http://deb.opera.com stable Release.gpg                                                                     
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_GB                                               
Ign http://packages.medibuntu.org/ lucid/free Translation-en_GB                            
Hit http://gb.archive.ubuntu.com lucid Release                                                                  
Hit http://security.ubuntu.com lucid-security/main Packages                                                     
Hit http://gb.archive.ubuntu.com lucid-updates Release                                                          
Hit http://deb.opera.com stable Release                                                                         
Hit http://security.ubuntu.com lucid-security/restricted Packages                                               
Hit http://security.ubuntu.com lucid-security/main Sources                                                      
Hit http://security.ubuntu.com lucid-security/restricted Sources                                                
Hit http://security.ubuntu.com lucid-security/universe Packages                                                 
Hit http://security.ubuntu.com lucid-security/universe Sources                                                  
Hit http://security.ubuntu.com lucid-security/multiverse Packages                                               
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_GB                                             
Hit http://gb.archive.ubuntu.com lucid/main Packages                                                            
Hit http://gb.archive.ubuntu.com lucid/restricted Packages                                 
Hit http://gb.archive.ubuntu.com lucid/main Sources                                        
Hit http://gb.archive.ubuntu.com lucid/restricted Sources                                  
Hit http://security.ubuntu.com lucid-security/multiverse Sources                                                
Ign http://deb.opera.com stable/non-free Packages                                                               
Hit http://gb.archive.ubuntu.com lucid/universe Packages                                                        
Hit http://gb.archive.ubuntu.com lucid/universe Sources                                    
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages                                 
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources                                  
Hit http://gb.archive.ubuntu.com lucid-updates/main Packages                               
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Packages                         
Hit http://gb.archive.ubuntu.com lucid-updates/main Sources                                
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Sources                          
Hit http://gb.archive.ubuntu.com lucid-updates/universe Packages                           
Hit http://packages.medibuntu.org lucid Release                      
Hit http://gb.archive.ubuntu.com lucid-updates/universe Sources                            
Ign http://deb.opera.com stable/non-free Packages                                                               
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Packages                                              
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources                                     
Hit http://packages.medibuntu.org lucid/free Packages                                                 
Hit http://deb.opera.com stable/non-free Packages                    
Hit http://packages.medibuntu.org lucid/non-free Packages                       
Get: 1 http://dl.google.com stable Release.gpg [198B]                           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_GB
Get: 2 http://dl.google.com stable Release [1,347B]
Get: 3 http://dl.google.com stable/main Packages [765B]                                                         
Fetched 2,310B in 6s (346B/s)                                                                                   
Reading package lists... Done
```

---

### Post by subehsharma on 2011-11-21
looks good to me!

---

### Post by matt_symes on 2011-11-21
Hi

From the terminal type

```
sudo apt-get upgrade
```

Post back the text generated between code tags - use the # button above where you type your reply or use code tags like this

[noparse]```
text
```[/noparse]

Kind regards

---

### Post by Peter2009 on 2011-11-21
> **matt_symes said:**
> Hi

From the terminal type

```
sudo apt-get upgrade
```

Post back the text generated between code tags - use the # button above where you type your reply or use code tags like this

[noparse]```
text
```[/noparse]

Kind regards

I think that is what I did in my previous reply, right? Thanks

---

### Post by matt_symes on 2011-11-21
Hi

> **Peter2009 said:**
> I think that is what I did in my previous reply, right? Thanks

I wanted to look at

```
sudo apt-get **upgrade**
```

Kind regards

---

### Post by Peter2009 on 2011-11-21
> **matt_symes said:**
> Hi



I wanted to look at

```
sudo apt-get **upgrade**
```

Kind regards

Sorry my mistake!!! LOL

here is the code for upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

Thanks

---

### Post by matt_symes on 2011-11-21
Hi

That looks fine. :confused:

Can you take a screen shot of update manager when it's failing.

Kind regards

---

### Post by Peter2009 on 2011-11-21
> **matt_symes said:**
> Hi

That looks fine. :confused:

Can you take a screen shot of update manager when it's failing.

Kind regards

Bad news!!!!!! LOL

Lost my source.list file!!! LOL , I know!!!!

How I have another question about which I will create another Thread for it, which you can go on "[go here"]("http://ubuntuforums.org/showthread.php?p=11478267#post11478267") (how do I know if its saved the repository to update from)

Back to here, If may not be point to keep looking at this issue. Done Update and Upgrade and both are running fine

Have raised some issues (how do I know if its saved the repository to update from), like after the new source.list file "update" lot of files, "upgrate" more than 110 files and when I run the "Update Manage" Update some more files, even update me to new kernel (2.6.32-36-generic)

Here is the new update:

```
Hit http://packages.medibuntu.org lucid Release.gpg                                                                                                
Get: 1 http://dl.google.com stable Release.gpg [189B]                                                                                              
Hit http://debian.wgdd.de lucid Release.gpg                                                                                                        
Ign http://debian.wgdd.de/ubuntu/ lucid/main Translation-en_GB                                                                                     
Ign http://debian.wgdd.de/ubuntu/ lucid/restricted Translation-en_GB                                                                               
Hit http://uk.archive.ubuntu.com lucid Release.gpg                                                                                                 
Hit http://uk.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB                                                                              
Hit http://uk.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB                                                                        
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_GB                                                                              
Hit http://uk.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB                                                                          
Hit http://uk.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB                                                                        
Hit http://uk.archive.ubuntu.com lucid-security Release.gpg                                                                                        
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB                                                                     
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB                                                               
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB                                                                 
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB                                                               
Ign http://debian.wgdd.de/ubuntu/ lucid/universe Translation-en_GB                                                                                 
Ign http://debian.wgdd.de/ubuntu/ lucid/multiverse Translation-en_GB                                                                               
Hit http://debian.wgdd.de maverick Release.gpg                                                                                                     
Ign http://debian.wgdd.de/ubuntu/ maverick/main Translation-en_GB                                                                                  
Ign http://debian.wgdd.de/ubuntu/ maverick/restricted Translation-en_GB                                                                            
Ign http://debian.wgdd.de/ubuntu/ maverick/universe Translation-en_GB                                                                              
Ign http://debian.wgdd.de/ubuntu/ maverick/multiverse Translation-en_GB                                                                            
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                     
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                     
Hit http://archive.canonical.com lucid Release.gpg                                                                                                 
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB                                                                           
Get: 2 http://dl.google.com testing Release.gpg [189B]                                                                                             
Ign http://packages.medibuntu.org/ lucid/free Translation-en_GB                                                                                    
Hit http://uk.archive.ubuntu.com lucid-updates Release.gpg                                                                                         
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB                                                                      
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB                                                                
Ign http://dl.google.com/linux/deb/ testing/non-free Translation-en_GB                                                                             
Hit http://deb.opera.com lenny Release.gpg                                                                                                         
Ign http://deb.opera.com/opera/ lenny/non-free Translation-en_GB                                                                                   
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB                                                                  
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB                                                                
Hit http://uk.archive.ubuntu.com lucid-proposed Release.gpg                                                                                        
Hit http://uk.archive.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_GB                                                                     
Hit http://uk.archive.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_GB                                                               
Hit http://debian.wgdd.de sid Release.gpg                                                                                                          
Ign http://debian.wgdd.de/debian/ sid/main Translation-en_GB                                                                                       
Ign http://debian.wgdd.de/debian/ sid/contrib Translation-en_GB                                                                                    
Hit http://uk.archive.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_GB                                                                 
Hit http://uk.archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_GB                                                               
Get: 3 http://dl.google.com stable Release.gpg [198B]                                                                                              
Hit http://uk.archive.ubuntu.com lucid-backports Release.gpg                                                                                       
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_GB                                                                    
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_GB                                                              
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_GB                                                                
Ign http://uk.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_GB                                                              
Hit http://uk.archive.ubuntu.com lucid Release                                                                                                     
Hit http://archive.canonical.com lucid Release                                                                                                     
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_GB                                                                       
Hit http://ppa.launchpad.net lucid Release                                                                                                         
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_GB                                                                                
Hit http://uk.archive.ubuntu.com lucid-security Release                                                                                            
Hit http://uk.archive.ubuntu.com lucid-updates Release                                                                                             
Get: 4 http://dl.google.com stable Release [2,544B]                                                                                                
Hit http://deb.opera.com stable Release.gpg                                                                                                        
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_GB                                                                                  
Ign http://debian.wgdd.de/debian/ sid/non-free Translation-en_GB                                                                                   
Hit http://debian.wgdd.de lucid Release                                                                                                            
Hit http://debian.wgdd.de maverick Release                                                                                                         
Hit http://deb.opera.com lenny Release                                                                                                             
Hit http://uk.archive.ubuntu.com lucid-proposed Release                                                                                            
Hit http://uk.archive.ubuntu.com lucid-backports Release                                                                                           
Get: 5 http://dl.google.com testing Release [2,513B]                                                                                               
Hit http://debian.wgdd.de sid Release                                                                                                              
Hit http://packages.medibuntu.org lucid Release                                                                                                    
Get: 6 http://dl.google.com stable Release [1,347B]                                                                                                
Hit http://uk.archive.ubuntu.com lucid/main Packages                                                                                               
Hit http://uk.archive.ubuntu.com lucid/restricted Packages                                                                               
Hit http://uk.archive.ubuntu.com lucid/universe Packages                                                                                 
Hit http://uk.archive.ubuntu.com lucid/multiverse Packages                                                                               
Hit http://ppa.launchpad.net lucid Release                                                                                                         
Hit http://deb.opera.com stable Release                                                                                                            
Hit http://archive.canonical.com lucid/partner Packages                                                                                
Hit http://uk.archive.ubuntu.com lucid/main Sources                                                                                                
Hit http://uk.archive.ubuntu.com lucid/restricted Sources                                                                              
Hit http://uk.archive.ubuntu.com lucid/universe Sources                                                                                
Hit http://uk.archive.ubuntu.com lucid/multiverse Sources                                                                                          
Hit http://uk.archive.ubuntu.com lucid-security/main Packages                                                                                      
Hit http://uk.archive.ubuntu.com lucid-security/restricted Packages                                                                                
Hit http://uk.archive.ubuntu.com lucid-security/universe Packages                                                                                  
Hit http://uk.archive.ubuntu.com lucid-security/multiverse Packages                                                                                
Hit http://uk.archive.ubuntu.com lucid-security/main Sources                                                                                       
Hit http://uk.archive.ubuntu.com lucid-security/restricted Sources                                                                                 
Hit http://debian.wgdd.de lucid/main Packages                                                                                                      
Get: 7 http://dl.google.com stable/non-free Packages [1,010B]                                                                                      
Hit http://uk.archive.ubuntu.com lucid-security/universe Sources                                                                                   
Hit http://uk.archive.ubuntu.com lucid-security/multiverse Sources                                                                                 
Hit http://uk.archive.ubuntu.com lucid-updates/main Packages                                                                                       
Hit http://uk.archive.ubuntu.com lucid-updates/restricted Packages                                                                                 
Hit http://uk.archive.ubuntu.com lucid-updates/universe Packages                                                                                   
Hit http://uk.archive.ubuntu.com lucid-updates/multiverse Packages                                                                                 
Hit http://uk.archive.ubuntu.com lucid-updates/main Sources                                                                                        
Hit http://uk.archive.ubuntu.com lucid-updates/restricted Sources                                                                                  
Hit http://uk.archive.ubuntu.com lucid-updates/universe Sources                                                                                    
Hit http://archive.canonical.com lucid/partner Sources                                                                                             
Hit http://debian.wgdd.de lucid/restricted Packages                                                                                                
Hit http://uk.archive.ubuntu.com lucid-updates/multiverse Sources                                                                                  
Ign http://deb.opera.com lenny/non-free Packages                                                                                                   
Hit http://ppa.launchpad.net lucid/main Sources                                                                                                    
Hit http://uk.archive.ubuntu.com lucid-proposed/main Packages                                                                                      
Hit http://uk.archive.ubuntu.com lucid-proposed/restricted Packages                                                                                
Hit http://uk.archive.ubuntu.com lucid-proposed/universe Packages                                                                                  
Hit http://uk.archive.ubuntu.com lucid-proposed/multiverse Packages                                                                                
Hit http://uk.archive.ubuntu.com lucid-proposed/main Sources                                                                                       
Hit http://uk.archive.ubuntu.com lucid-proposed/restricted Sources                                                                                 
Hit http://uk.archive.ubuntu.com lucid-proposed/universe Sources                                                                                   
Hit http://uk.archive.ubuntu.com lucid-proposed/multiverse Sources                                                                                 
Hit http://uk.archive.ubuntu.com lucid-backports/main Packages                                                                                     
Hit http://debian.wgdd.de lucid/universe Packages                                                                                                  
Hit http://debian.wgdd.de lucid/multiverse Packages                                                                                                
Hit http://debian.wgdd.de maverick/main Packages                                                                                                   
Hit http://debian.wgdd.de maverick/restricted Packages                                                                                             
Hit http://debian.wgdd.de maverick/universe Packages                                                                                               
Hit http://debian.wgdd.de maverick/multiverse Packages                                                                                             
Get: 8 http://dl.google.com testing/non-free Packages [793B]                                                                                       
Hit http://uk.archive.ubuntu.com lucid-backports/restricted Packages                                                                               
Hit http://uk.archive.ubuntu.com lucid-backports/universe Packages                                                                                 
Hit http://uk.archive.ubuntu.com lucid-backports/multiverse Packages                                                                               
Hit http://uk.archive.ubuntu.com lucid-backports/main Sources                                                                                      
Hit http://uk.archive.ubuntu.com lucid-backports/restricted Sources                                                                                
Hit http://packages.medibuntu.org lucid/free Packages                                                                                              
Hit http://uk.archive.ubuntu.com lucid-backports/universe Sources                                                                                  
Ign http://deb.opera.com lenny/non-free Packages                                                                                                   
Hit http://debian.wgdd.de sid/main Packages                                                                                                        
Hit http://debian.wgdd.de sid/contrib Packages                                                                                                     
Hit http://debian.wgdd.de sid/non-free Packages                                                                                                    
Hit http://uk.archive.ubuntu.com lucid-backports/multiverse Sources                                                                                
Hit http://debian.wgdd.de sid/main Sources                                                                                                         
Hit http://debian.wgdd.de sid/contrib Sources                                                                                                      
Get: 9 http://dl.google.com stable/main Packages [765B]                                                                                            
Hit http://ppa.launchpad.net lucid/main Sources                                                                                                    
Hit http://packages.medibuntu.org lucid/non-free Packages                                                                         
Hit http://debian.wgdd.de sid/non-free Sources                                                                                               
Ign http://deb.opera.com stable/non-free Packages                                                                                            
Hit http://packages.medibuntu.org lucid/free Sources                                                                   
Hit http://deb.opera.com lenny/non-free Packages                                                                       
Hit http://packages.medibuntu.org lucid/non-free Sources                                                               
Ign http://deb.opera.com stable/non-free Packages               
Hit http://deb.opera.com stable/non-free Packages               
Hit http://archive.getdeb.net lucid-getdeb Release.gpg
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/apps Translation-en_GB
Hit http://archive.getdeb.net lucid-getdeb Release       
Hit http://archive.getdeb.net lucid-getdeb/apps Packages 
Fetched 9,548B in 6s (1,557B/s)                                                                                                                    
Reading package lists... Done

```

And for upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

here is a snap short for the "update manager" picture, it was similar but I cannot replicate the same.

[ATTACH]207737[/ATTACH]

---

