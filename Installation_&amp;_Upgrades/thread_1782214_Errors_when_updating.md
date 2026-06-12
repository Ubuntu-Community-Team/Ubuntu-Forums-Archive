---
title: "Errors when updating"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by ticktoast on 2011-06-14
For about a month now, I've received errors every time I try to install any updates. 
```
Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.
```I looked around and saw that a lot of people had the same issue. However, when I tried the solutions that people had given, none of them seemed to solve the problem. Any suggestions on how to fix this?

---

### Post by jerrrys on 2011-06-14
have you installed some PPA's ? your missing a key (authentication) in your software sources (MainMenu>System>Administration>SoftwareSources)

---

### Post by ticktoast on 2011-06-14
...I don't seem to have anything along those lines in my menu...?
(sorry. I'm sort of hopeless, here..)

---

### Post by jerrrys on 2011-06-14
have you added any packages from other sources (not in the software center)?

EDIT:  i forgot

sudo software-properties-gtk

---

### Post by sikander3786 on 2011-06-14
Most of the time, that error seems to appear if the repository index expired on your PC. Go to Terminal and run:

```
sudo apt-get update
```

Then try installation again.

[http://ubuntu4beginners.blogspot.com/2011/02/requires-installation-of-untrusted.html](http://ubuntu4beginners.blogspot.com/2011/02/requires-installation-of-untrusted.html)

If the errors persist, we need to see the complete output of the above command as well as these one's:

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

---

### Post by ticktoast on 2011-06-15
The error is still appearing even after an update. Here's the output..
```
Ign file: apt-build InRelease
Ign file: apt-build Release.gpg                                                
Get:1 file: apt-build Release [89 B]                                           
Ign file: apt-build/main TranslationIndex                                      
Ign file: apt-build/main Translation-en_US                                     
Ign file: apt-build/main Translation-en                                        
Ign http://archive.canonical.com maverick InRelease                            
Ign http://security.ubuntu.com natty-security InRelease                        
Hit http://archive.canonical.com maverick Release.gpg                          
Hit http://security.ubuntu.com natty-security Release.gpg                      
Hit http://archive.canonical.com maverick Release                              
Hit http://security.ubuntu.com natty-security Release                          
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://security.ubuntu.com natty-security/restricted Sources               
Ign http://archive.canonical.com maverick/partner TranslationIndex             
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://archive.canonical.com maverick/partner Translation-en_US            
Ign http://archive.canonical.com maverick/partner Translation-en               
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://extras.ubuntu.com maverick InRelease                                
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://archive.ubuntu.com natty-updates InRelease                          
Ign http://archive.ubuntu.com natty-security InRelease                         
Hit http://extras.ubuntu.com maverick Release.gpg                              
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://archive.ubuntu.com natty-updates Release.gpg                        
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://archive.ubuntu.com natty-security Release.gpg                       
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://archive.ubuntu.com natty-updates Release                            
Hit http://ppa.launchpad.net natty Release                                     
Ign http://extras.ubuntu.com maverick/main TranslationIndex                    
Hit http://archive.ubuntu.com natty-security Release                           
Ign http://ppa.launchpad.net natty Release                                     
Hit http://archive.ubuntu.com natty-updates/restricted Sources                 
Hit http://archive.ubuntu.com natty-updates/main Sources                       
Hit http://archive.ubuntu.com natty-updates/multiverse Sources                 
Hit http://archive.ubuntu.com natty-updates/universe Sources                   
Hit http://archive.ubuntu.com natty-updates/restricted i386 Packages           
Hit http://ppa.launchpad.net natty Release                                     
Hit http://archive.ubuntu.com natty-updates/main i386 Packages                 
Hit http://archive.ubuntu.com natty-updates/multiverse i386 Packages           
Hit http://archive.ubuntu.com natty-updates/universe i386 Packages             
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Hit http://archive.ubuntu.com natty-security/restricted Sources                
Hit http://archive.ubuntu.com natty-security/main Sources                      
Hit http://archive.ubuntu.com natty-security/multiverse Sources                
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://archive.ubuntu.com natty-security/universe Sources                  
Hit http://archive.ubuntu.com natty-security/restricted i386 Packages          
Hit http://archive.ubuntu.com natty-security/main i386 Packages                
Hit http://archive.ubuntu.com natty-security/multiverse i386 Packages          
Hit http://archive.ubuntu.com natty-security/universe i386 Packages            
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.ubuntu.com natty-security/main TranslationIndex             
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex         
Ign http://extras.ubuntu.com maverick/main Translation-en_US                   
Ign http://extras.ubuntu.com maverick/main Translation-en                      
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                          
  404  Not Found
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US             
Ign http://archive.ubuntu.com natty-updates/main Translation-en                
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US       
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en          
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en          
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com natty-updates/universe Translation-en            
Ign http://archive.ubuntu.com natty-security/main Translation-en_US            
Ign http://archive.ubuntu.com natty-security/main Translation-en               
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US      
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en         
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US      
Ign http://archive.ubuntu.com natty-security/restricted Translation-en         
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US        
Ign http://archive.ubuntu.com natty-security/universe Translation-en           
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://packages.medibuntu.org natty InRelease                              
Ign http://us.archive.ubuntu.com natty-updates InRelease
Get:2 http://packages.medibuntu.org natty Release.gpg [197 B]
Hit http://us.archive.ubuntu.com natty Release.gpg        
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Get:3 http://packages.medibuntu.org natty Release [6,848 B]
Ign http://packages.medibuntu.org natty Release           
Hit http://us.archive.ubuntu.com natty Release    
Hit http://us.archive.ubuntu.com natty-updates Release                         
Ign http://packages.medibuntu.org natty/free i386 Packages/DiffIndex           
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/main Sources       
Hit http://us.archive.ubuntu.com natty/multiverse Sources 
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://packages.medibuntu.org natty/non-free i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources
Hit http://us.archive.ubuntu.com natty-updates/main Sources
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://packages.medibuntu.org natty/free TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Fetched 198 B in 18s (11 B/s)                                                  
N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension
W: GPG error: http://packages.medibuntu.org natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```And for the other 2 commands, it gave me..
```
morgan@Morgan:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release i386 (20101008)]/ maverick main multiverse restricted universe

# deb cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release i386 (20101008)]/ maverick main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ natty-security restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ natty-security restricted main multiverse universe #Added by software-properties
morgan@Morgan:~$ ls -l /etc/apt/sources.list.d
total 172
-rw-r--r-- 1 root root 132 2011-06-14 11:48 alecive-antigone-natty.list
-rw-r--r-- 1 root root 132 2011-06-14 11:48 alecive-antigone-natty.list.save
-rw-r--r-- 1 root root 150 2011-06-14 11:48 and471-kazam-daily-stable-natty.list
-rw-r--r-- 1 root root 150 2011-06-14 11:48 and471-kazam-daily-stable-natty.list.save
-rw-r--r-- 1 root root   0 2008-11-05 04:35 apt-build
-rw-r--r-- 1 root root  56 2011-06-14 11:48 apt-build.list
-rw-r--r-- 1 root root  56 2011-06-14 11:48 apt-build.list.save
-rw-r--r-- 1 root root 202 2011-06-14 11:48 cheleb-blender-svn-maverick.list
-rw-r--r-- 1 root root 142 2011-04-23 21:12 cheleb-blender-svn-maverick.list.distUpgrade
-rw-r--r-- 1 root root 202 2011-06-14 11:48 cheleb-blender-svn-maverick.list.save
-rw-r--r-- 1 root root 200 2011-06-14 11:48 cinelerra-ppa-ppa-maverick.list
-rw-r--r-- 1 root root 140 2011-04-23 21:12 cinelerra-ppa-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root 200 2011-06-14 11:48 cinelerra-ppa-ppa-maverick.list.save
-rw-r--r-- 1 root root 204 2011-06-14 11:48 doctormo-wacom-plus-maverick.list
-rw-r--r-- 1 root root 144 2011-04-23 21:12 doctormo-wacom-plus-maverick.list.distUpgrade
-rw-r--r-- 1 root root 204 2011-06-14 11:48 doctormo-wacom-plus-maverick.list.save
-rw-r--r-- 1 root root 206 2011-06-14 11:48 faster3ck-converseen-maverick.list
-rw-r--r-- 1 root root 146 2011-04-23 21:12 faster3ck-converseen-maverick.list.distUpgrade
-rw-r--r-- 1 root root 206 2011-06-14 11:48 faster3ck-converseen-maverick.list.save
-rw-r--r-- 1 root root 192 2011-06-14 11:48 hughescih-ppa-maverick.list
-rw-r--r-- 1 root root 132 2011-04-23 21:12 hughescih-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root 192 2011-06-14 11:48 hughescih-ppa-maverick.list.save
-rw-r--r-- 1 root root 186 2011-06-14 11:48 irie-wacom-maverick.list
-rw-r--r-- 1 root root 126 2011-04-23 21:12 irie-wacom-maverick.list.distUpgrade
-rw-r--r-- 1 root root 186 2011-06-14 11:48 irie-wacom-maverick.list.save
-rw-r--r-- 1 root root 210 2011-06-14 11:48 jonoomph-openshot-edge-maverick.list
-rw-r--r-- 1 root root 150 2011-04-23 21:12 jonoomph-openshot-edge-maverick.list.distUpgrade
-rw-r--r-- 1 root root 210 2011-06-14 11:48 jonoomph-openshot-edge-maverick.list.save
-rw-r--r-- 1 root root 130 2011-06-14 11:48 libreoffice-ppa-natty.list
-rw-r--r-- 1 root root 130 2011-06-14 11:48 libreoffice-ppa-natty.list.save
-rw-r--r-- 1 root root 216 2011-06-14 11:48 matthaeus123-mrw-gimp-svn-maverick.list
-rw-r--r-- 1 root root 156 2011-04-23 21:12 matthaeus123-mrw-gimp-svn-maverick.list.distUpgrade
-rw-r--r-- 1 root root 216 2011-06-14 11:48 matthaeus123-mrw-gimp-svn-maverick.list.save
-rw-r--r-- 1 root root 275 2011-06-14 11:48 medibuntu.list
-rw-r--r-- 1 root root 275 2011-06-14 11:48 medibuntu.list.save
-rw-r--r-- 1 root root 190 2011-06-14 11:48 pmcenery-ppa-maverick.list
-rw-r--r-- 1 root root 130 2011-04-23 21:12 pmcenery-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root 190 2011-06-14 11:48 pmcenery-ppa-maverick.list.save
-rw-r--r-- 1 root root 190 2011-06-14 11:48 ripps818-ppa-maverick.list
-rw-r--r-- 1 root root 130 2011-04-23 21:12 ripps818-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root 190 2011-06-14 11:48 ripps818-ppa-maverick.list.save
-rw-r--r-- 1 root root 194 2011-06-14 11:48 tiheum-equinox-maverick.list
-rw-r--r-- 1 root root 134 2011-04-23 21:12 tiheum-equinox-maverick.list.distUpgrade
-rw-r--r-- 1 root root 194 2011-06-14 11:48 tiheum-equinox-maverick.list.save
-rw-r--r-- 1 root root   0 2011-03-27 01:01 winehq.list

```

---

### Post by sikander3786 on 2011-06-15
A few gpg keys are missing. Run this command in Terminal and post the outputs please:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

And for the 404 Error, the Kazam PPA seems to be down at the moment. Go to Software Center > Edit > Software Sources > Other Software tab and disable 2 of the Kazam PPAs. Again try:

```
sudo apt-get update
```

---

### Post by ticktoast on 2011-06-15
Ah.. thank you for that bit!

Here's the output:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

```

---

### Post by sikander3786 on 2011-06-15
Output is ok. So we hope everything is working fine now?

---

### Post by ticktoast on 2011-06-15
Mmh.. unfortunately not. I'm still getting the same error when I try to run the update manager..

---

### Post by sikander3786 on 2011-06-16
Ok. Then go to Software Center > Edit > Software Sources and on the main tab, choose 'Main' as your download server. Run apt-get update and try using update-manager again.

---

### Post by jerrrys on 2011-06-16
you have a mix of maverick and natty in your software sources.  whats up with that?  are you running mavrick?

---

