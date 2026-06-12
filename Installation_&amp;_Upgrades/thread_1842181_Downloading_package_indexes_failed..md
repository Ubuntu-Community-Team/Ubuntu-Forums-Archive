---
title: "Downloading package indexes failed."
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by cadamcross on 2011-09-10
Hi.  I'm running Lucid Lynx.  When I run System/Administration/Hardware Drivers, I get an error message that reads 
"Downloading package indexes failed, please check your network status.  Most drivers will not be available."

I have Internet access, so that's not the problem.  Also, I did Google this and found the thread at [http://ubuntuforums.org/showthread.php?t=1527426](http://ubuntuforums.org/showthread.php?t=1527426), but despite the identical error message, I think the problem is different from that thread because when I apt-get update I get
```

Hit http://linux.dropbox.com lucid Release.gpg
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US              
Hit http://linux.dropbox.com lucid Release                                     
Hit http://packages.medibuntu.org lucid Release.gpg                            
Hit http://linux.dropbox.com lucid/main Packages                               
Get:1 http://dl.google.com stable Release.gpg [198B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Get:2 http://dl.google.com stable Release.gpg [198B]                           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Hit http://archive.ubuntu.com lucid Release.gpg                                
Get:3 http://dl.google.com stable Release [1,347B]                             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid Release                                 
Get:4 http://dl.google.com stable Release [1,347B]                             
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Hit http://archive.ubuntu.com lucid Release                                    
Get:5 http://dl.google.com stable/main Packages [1,199B]                       
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://archive.ubuntu.com lucid/main Sources                               
Get:6 http://dl.google.com stable/main Packages [758B]                         
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://archive.ubuntu.com lucid/restricted Sources               
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US
Hit http://packages.medibuntu.org lucid Release           
Hit http://packages.medibuntu.org lucid/free Packages     
Hit http://packages.medibuntu.org lucid/non-free Packages
Fetched 5,047B in 1s (2,602B/s)
Reading package lists... Done

```

I don't know what other information a person might need from me to diagnose this, so let me know.   Thanks for any help.

---

### Post by wojox on 2011-09-10
Run:

```
sudo apt-get update; sudo apt-get upgrade
```

Post back any error messages.

---

### Post by cadamcross on 2011-09-10
Done and done.  No error messages.  Problem remains.  

```
 sudo apt-get update

Get:1 http://dl.google.com stable Release.gpg [198B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Hit http://linux.dropbox.com lucid Release.gpg                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US              
Get:2 http://dl.google.com stable Release.gpg [198B]                           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://archive.ubuntu.com lucid Release.gpg                                
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Get:3 http://dl.google.com stable Release [1,347B]                             
Hit http://linux.dropbox.com lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Get:4 http://dl.google.com stable Release [1,347B]                             
Hit http://packages.medibuntu.org lucid Release.gpg                            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://linux.dropbox.com lucid/main Packages                               
Hit http://archive.ubuntu.com lucid Release                                    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:5 http://dl.google.com stable/main Packages [1,199B]                       
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Get:6 http://dl.google.com stable/main Packages [758B]                         
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Hit http://archive.ubuntu.com lucid/restricted Sources                         
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Hit http://packages.medibuntu.org lucid Release           
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Fetched 5,047B in 2s (2,390B/s)
Reading package lists... Done

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by cadamcross on 2011-09-10
PS: This is something that used to work and is now broken (versus never having worked on this Ubuntu installation).

---

### Post by wojox on 2011-09-11
> **cadamcross said:**
> PS: This is something that used to work and is now broken (versus never having worked on this Ubuntu installation).

I'm lost? I don't see any error messages and your all updated.

---

### Post by haqking on 2011-09-11
> **wojox said:**
> I'm lost? I don't see any error messages and your all updated.

+1

there is no error message and everything is upto date by the looks of it

---

### Post by cadamcross on 2011-09-11
I ran update and upgrade because I was asked to, but I never said there were errors regarding that.  I get an error message, as per my original post, when I run System/Administration/Hardware Drivers from the menu.

---

### Post by plucky on 2011-09-12
```
Get:1 http://dl.google.com stable Release.gpg [198B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Hit http://linux.dropbox.com lucid Release.gpg                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US              
Get:2 http://dl.google.com stable Release.gpg [198B]                           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://archive.ubuntu.com lucid Release.gpg                                
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Get:3 http://dl.google.com stable Release [1,347B]                             
Hit http://linux.dropbox.com lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Get:4 http://dl.google.com stable Release [1,347B]                             
Hit http://packages.medibuntu.org lucid Release.gpg                            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://linux.dropbox.com lucid/main Packages                               
Hit http://archive.ubuntu.com lucid Release                                    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:5 http://dl.google.com stable/main Packages [1,199B]                       
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Get:6 http://dl.google.com stable/main Packages [758B]                         
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Hit http://archive.ubuntu.com lucid/restricted Sources                         
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Hit http://packages.medibuntu.org lucid Release           
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Fetched 5,047B in 2s (2,390B/s)
Reading package lists... Done

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


I don't see the main repository and lucid-update repository in that list.

Open Software Sources and make sure the main repository and lucid-updates repository is ticked, then reload and see if that makes a difference.

Good Luck

---

### Post by cadamcross on 2011-09-12
Thanks for pointing that out about the repositories.  I think the sources.list file may have been altered directly, and changing the settings within the Ubuntu Software Center didn't seem to have the desired effect.  I used something I found on the Internet called the Ubuntu Sources List Generator to figure out what I should add to the sources.list file.  Restoring the main repository and the update repositories corrected my problem, so thank you very much for the suggestion.

By the way, is there some official listing somewhere for the Ubuntu main repository?  The only place I could find it anywhere was within the Ubuntu Sources List Generator.

---

