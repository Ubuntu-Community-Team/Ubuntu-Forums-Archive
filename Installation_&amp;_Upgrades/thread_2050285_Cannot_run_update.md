---
title: "Cannot run update"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by cioo on 2012-08-30
Probably as a result of tinkering in an attempt to get the sound to work on my laptop, it has resulted in my not being able to run the updates.  Here is the error message:

W:Failed to fetch [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Would appreciate help to sort it out, thanks.

---

### Post by drmrgd on 2012-08-30
Based on the information on their Launchpad page, there doesn't appear to be any packages available for Precise:

[https://launchpad.net/~team-iquik/+archive/alsa](https://launchpad.net/~team-iquik/+archive/alsa)

It looks like the last version listed is for 10.04.

---

### Post by cioo on 2012-08-30
ok, so what do I do about it?  I cannot update anything at the moment - this error is preventing all updates.   Presumably try to stop it looking for the launchpad update - but how?

---

### Post by drmrgd on 2012-08-30
No, I don't think that's the case.  The error is only saying that it can't fetch any data from that PPA since it can't find it.  The rest should be OK.  Just to make sure, please post the full results of:

```
sudo apt-get update
```

Also, are you running Precise or an older version, and did you just change that particular repository causing the error?

---

### Post by cioo on 2012-08-30
Here is the result of that command:

Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise InRelease
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise Release                               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:4 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/main Sources                          
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/universe Sources                      
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/universe TranslationIndex             
Get:5 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/main Sources [158 kB]       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [41.0 kB]       
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [12.1 kB]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386 B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [162 kB] 
Get:11 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]
Get:12 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/universe Sources [50.1 kB] 
Get:13 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Get:14 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/main i386 Packages [378 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [41.6 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Get:18 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:19 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/universe i386 Packages [127 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:20 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,672 B]
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/main Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/main Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise/universe Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 1,103 kB in 4s (226 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

*************
You might be right, but normally the update manager lists up the new updates to download and install.  Since this fault has occurred, I do not get any kind of listing, just the error message which makes me concerned that it might not be updating anything properly.

I am running 12.04.

---

### Post by cioo on 2012-08-30
ok, so just to make me look stupid, it did now come up with a list of updates in the update manager.... So I suppose everything except the launchpad is now updating as it should :rolleyes:

However, the package information is not updating.  It still says that the package info was last updated 15 days ago...

---

