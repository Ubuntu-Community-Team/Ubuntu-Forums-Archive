---
title: "Update Issue"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by D0gb0y on 2012-06-26
I have managed to get the 32bit version of Ubuntu working on my system. It is the sole OS. 

When I check for updates I am told there are many (80 or so) however when I go to download them Im told that my internet connection is not working.  With this error message....

Failed to fetch [http://ppa.launchpad.net/tualatrix/next/ubuntu/pool/main/u/ubuntu-tweak/ubuntu-tweak_0.7.3-0~bzr1865+20120621~precise1_all.deb](http://ppa.launchpad.net/tualatrix/next/ubuntu/pool/main/u/ubuntu-tweak/ubuntu-tweak_0.7.3-0~bzr1865+20120621~precise1_all.deb) 404  Not Found

Now I also have tweak installed, could it be somehow interfering with the update manager?

Cheers for any help from a complete Ubuntu newbie

---

### Post by Frogs Hair on 2012-06-26
I use the same PPA and the source is being located . Try running the following command in the terminal until the source is located.```
sudo apt-get update
```

If that fails changing the server in update manager > settings > Ubuntu software > download from may help. You can choose a sever closer to you from the other category in the drop-down menu .

---

### Post by cortman on 2012-06-26
Also make sure you're not behind a proxy- a classic apt-mess-up problem.

---

### Post by D0gb0y on 2012-06-26
Hey guys thanks for your quick responses. 

Tried to run the update though the terminal and got an error message at the end regarding a duplicate server. 

I went into the software centre and ran a test to see which was the best server. It found another and I changed to that, I tried running the update through the terminal again and it looked like it was working for a moment then this message came up...

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems 

Any ideas?

---

### Post by jmfal on 2012-06-26
Open a terminal and copy/paste this in there:

```
 sudo apt-get update       
```

Press enter, then enter your password at prompt(you will not see it)
Press enter again

if ther is an error post the output in   #  [CODE][CODE]  so it is easier to read

---

### Post by D0gb0y on 2012-06-26
Hi jmfal, 

excuse my stupidity but I have no idea how to get the output in code, quick lesson?:p

---

### Post by jmfal on 2012-06-26
After you run the command in the terminal you can copy/paste whatever is in the terminal to the # . 
Highllight what you want ,, right click> select copy>go to reply boxhere in the forum>> put your cursor between the code brackets >>right click>>select paste

---

### Post by dino99 on 2012-06-26
write your answer, then select the text with the mouse (highlight it) and finally click on # icon above

---

### Post by D0gb0y on 2012-06-26
#

---

### Post by D0gb0y on 2012-06-26
```
Ign http://archive.canonical.com precise InRelease
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://mirror01.th.ifl.net precise InRelease                               
Ign http://mirror01.th.ifl.net precise-updates InRelease                       
Ign http://mirror01.th.ifl.net precise-backports InRelease                     
Ign http://mirror01.th.ifl.net precise-security InRelease                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release.gpg                               
Ign http://dl.google.com stable InRelease                                      
Hit http://mirror01.th.ifl.net precise Release.gpg                             
Hit http://mirror01.th.ifl.net precise-updates Release.gpg                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://packages.medibuntu.org precise InRelease                            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://mirror01.th.ifl.net precise-backports Release.gpg                   
Hit http://archive.canonical.com precise/partner Sources                       
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://mirror01.th.ifl.net precise-security Release.gpg                    
Hit http://mirror01.th.ifl.net precise Release                                 
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Get:2 http://dl.google.com stable Release [1,338 B]                            
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://mirror01.th.ifl.net precise-updates Release                         
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://mirror01.th.ifl.net precise-backports Release                       
Hit http://mirror01.th.ifl.net precise-security Release                        
Hit http://mirror01.th.ifl.net precise/main Sources                            
Hit http://mirror01.th.ifl.net precise/restricted Sources                      
Hit http://mirror01.th.ifl.net precise/universe Sources                        
Hit http://mirror01.th.ifl.net precise/multiverse Sources                      
Hit http://mirror01.th.ifl.net precise/main i386 Packages                      
Get:3 http://dl.google.com stable/main i386 Packages [464 B]                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://mirror01.th.ifl.net precise/restricted i386 Packages                
Hit http://mirror01.th.ifl.net precise/universe i386 Packages                  
Hit http://mirror01.th.ifl.net precise/multiverse i386 Packages                
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Hit http://mirror01.th.ifl.net precise/main TranslationIndex                   
Hit http://mirror01.th.ifl.net precise/multiverse TranslationIndex             
Hit http://mirror01.th.ifl.net precise/restricted TranslationIndex             
Hit http://mirror01.th.ifl.net precise/universe TranslationIndex               
Hit http://mirror01.th.ifl.net precise-updates/main Sources                    
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://mirror01.th.ifl.net precise-updates/restricted Sources              
Hit http://mirror01.th.ifl.net precise-updates/universe Sources                
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://mirror01.th.ifl.net precise-updates/multiverse Sources              
Hit http://mirror01.th.ifl.net precise-updates/main i386 Packages              
Hit http://mirror01.th.ifl.net precise-updates/restricted i386 Packages        
Hit http://mirror01.th.ifl.net precise-updates/universe i386 Packages          
Hit http://mirror01.th.ifl.net precise-updates/multiverse i386 Packages        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://mirror01.th.ifl.net precise-updates/main TranslationIndex           
Hit http://mirror01.th.ifl.net precise-updates/multiverse TranslationIndex     
Hit http://mirror01.th.ifl.net precise-updates/restricted TranslationIndex     
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://mirror01.th.ifl.net precise-updates/universe TranslationIndex       
Hit http://mirror01.th.ifl.net precise-backports/main Sources                  
Hit http://mirror01.th.ifl.net precise-backports/restricted Sources            
Hit http://mirror01.th.ifl.net precise-backports/universe Sources              
Hit http://mirror01.th.ifl.net precise-backports/multiverse Sources            
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://mirror01.th.ifl.net precise-backports/main i386 Packages            
Hit http://mirror01.th.ifl.net precise-backports/restricted i386 Packages      
Hit http://mirror01.th.ifl.net precise-backports/universe i386 Packages        
Hit http://mirror01.th.ifl.net precise-backports/multiverse i386 Packages      
Hit http://mirror01.th.ifl.net precise-backports/main TranslationIndex         
Hit http://mirror01.th.ifl.net precise-backports/multiverse TranslationIndex   
Hit http://mirror01.th.ifl.net precise-backports/restricted TranslationIndex   
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://mirror01.th.ifl.net precise-backports/universe TranslationIndex     
Hit http://mirror01.th.ifl.net precise-security/main Sources                   
Hit http://mirror01.th.ifl.net precise-security/restricted Sources             
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Hit http://mirror01.th.ifl.net precise-security/universe Sources               
Hit http://mirror01.th.ifl.net precise-security/multiverse Sources             
Hit http://mirror01.th.ifl.net precise-security/main i386 Packages             
Hit http://mirror01.th.ifl.net precise-security/restricted i386 Packages       
Hit http://mirror01.th.ifl.net precise-security/universe i386 Packages         
Hit http://mirror01.th.ifl.net precise-security/multiverse i386 Packages       
Hit http://mirror01.th.ifl.net precise-security/main TranslationIndex          
Hit http://mirror01.th.ifl.net precise-security/multiverse TranslationIndex    
Ign http://archive.canonical.com precise/partner Translation-en_GB             
Hit http://mirror01.th.ifl.net precise-security/restricted TranslationIndex    
Hit http://mirror01.th.ifl.net precise-security/universe TranslationIndex      
Hit http://mirror01.th.ifl.net precise/main Translation-en_GB                  
Hit http://mirror01.th.ifl.net precise/main Translation-en                     
Hit http://mirror01.th.ifl.net precise/multiverse Translation-en_GB            
Hit http://mirror01.th.ifl.net precise/multiverse Translation-en               
Hit http://mirror01.th.ifl.net precise/restricted Translation-en_GB            
Hit http://mirror01.th.ifl.net precise/restricted Translation-en               
Hit http://mirror01.th.ifl.net precise/universe Translation-en_GB              
Hit http://mirror01.th.ifl.net precise/universe Translation-en                 
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Hit http://mirror01.th.ifl.net precise-updates/main Translation-en             
Hit http://mirror01.th.ifl.net precise-updates/multiverse Translation-en       
Hit http://mirror01.th.ifl.net precise-updates/restricted Translation-en       
Hit http://mirror01.th.ifl.net precise-updates/universe Translation-en         
Hit http://mirror01.th.ifl.net precise-backports/main Translation-en           
Hit http://mirror01.th.ifl.net precise-backports/multiverse Translation-en     
Hit http://mirror01.th.ifl.net precise-backports/restricted Translation-en     
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://mirror01.th.ifl.net precise-backports/universe Translation-en       
Hit http://mirror01.th.ifl.net precise-security/main Translation-en            
Hit http://mirror01.th.ifl.net precise-security/multiverse Translation-en      
Hit http://mirror01.th.ifl.net precise-security/restricted Translation-en      
Hit http://mirror01.th.ifl.net precise-security/universe Translation-en        
Ign http://dl.google.com stable/main Translation-en_GB                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en  
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en  
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en  
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en  
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en   
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en   
Ign http://packages.medibuntu.org precise/free Translation-en_GB
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_GB
Ign http://packages.medibuntu.org precise/non-free Translation-en
Fetched 2,000 B in 3s (648 B/s)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

---

### Post by IWantFroyo on 2012-06-26
Maybe this line is to blame?

```
Hit http://archive.canonical.com precise/partner i386 Packages
```

The sources should be listed in /etc/apt/sources.list

---

### Post by D0gb0y on 2012-06-26
Im not sure at all, 

here is what is inside the sources list;

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror01.th.ifl.net/ubuntu/ precise main restricted
deb-src http://mirror01.th.ifl.net/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror01.th.ifl.net/ubuntu/ precise-updates main restricted
deb-src http://mirror01.th.ifl.net/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror01.th.ifl.net/ubuntu/ precise universe
deb-src http://mirror01.th.ifl.net/ubuntu/ precise universe
deb http://mirror01.th.ifl.net/ubuntu/ precise-updates universe
deb-src http://mirror01.th.ifl.net/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror01.th.ifl.net/ubuntu/ precise multiverse
deb-src http://mirror01.th.ifl.net/ubuntu/ precise multiverse
deb http://mirror01.th.ifl.net/ubuntu/ precise-updates multiverse
deb-src http://mirror01.th.ifl.net/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror01.th.ifl.net/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://mirror01.th.ifl.net/ubuntu/ precise-backports main restricted universe multiverse

deb http://mirror01.th.ifl.net/ubuntu/ precise-security main restricted
deb-src http://mirror01.th.ifl.net/ubuntu/ precise-security main restricted
deb http://mirror01.th.ifl.net/ubuntu/ precise-security universe
deb-src http://mirror01.th.ifl.net/ubuntu/ precise-security universe
deb http://mirror01.th.ifl.net/ubuntu/ precise-security multiverse
deb-src http://mirror01.th.ifl.net/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
```

---

### Post by IWantFroyo on 2012-06-26
Try commenting out the last two lines (putting ## in front of them). They're duplicates of the second to last paragraph.

---

### Post by D0gb0y on 2012-06-26
So the software list is a read only file, is there a way I can save my edits?

---

### Post by D0gb0y on 2012-06-28
Thanks @IWantFroyo that seemed to do the trick!

Cheers!):P

---

