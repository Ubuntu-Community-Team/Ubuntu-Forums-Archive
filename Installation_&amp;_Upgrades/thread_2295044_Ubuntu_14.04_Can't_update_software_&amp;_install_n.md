---
title: "Ubuntu 14.04 Can't update software &amp; install new software"
date: 2015-09-15
forum: Installation &amp; Upgrades
---

### Post by Raja_Siahaan on 2015-09-15
Hello,
I'm new in using Ubuntu. And I don't know anything about programming code.
I use dual-booting laptop and I booted Ubuntu. When the desktop appeared, there is a notification to update security system and some applications.
When I try to update it, the update process stopped, and the strange "internet connection problem" message has appeared. I'm confused because I have tried the browser to surf the internet and it's so far so good. I opened the Ubuntu Software Center to download some softwares that help my study, but that message appeared after I click "Install".
So far, I searched on internet and found to type 
```
sudo apt-get update
```
and found this in terminal
```

Ign http://id.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://security.ubuntu.com trusty-security InRelease             
Ign http://id.archive.ubuntu.com trusty-updates InRelease            
Ign http://extras.ubuntu.com trusty Release.gpg                      
Ign http://security.ubuntu.com trusty-security Release.gpg           
Ign http://archive.canonical.com trusty InRelease                    
Ign http://id.archive.ubuntu.com trusty-backports InRelease          
Ign http://extras.ubuntu.com trusty Release                          
Ign http://id.archive.ubuntu.com trusty Release.gpg                  
Ign http://security.ubuntu.com trusty-security Release               
Ign http://archive.canonical.com trusty Release.gpg                  
Ign http://id.archive.ubuntu.com trusty-updates Release.gpg
Ign http://archive.canonical.com trusty Release                      
Ign http://id.archive.ubuntu.com trusty-backports Release.gpg        
Ign http://id.archive.ubuntu.com trusty Release                      
Ign http://id.archive.ubuntu.com trusty-updates Release              
Ign http://id.archive.ubuntu.com trusty-backports Release            
Err http://extras.ubuntu.com trusty/main Sources                               
  403  Forbidden
Err http://extras.ubuntu.com trusty/main amd64 Packages                        
  403  Forbidden
Err http://archive.canonical.com trusty/partner Sources              
  403  Forbidden
Err http://extras.ubuntu.com trusty/main i386 Packages               
  403  Forbidden
Err http://archive.canonical.com trusty/partner amd64 Packages       
  403  Forbidden
Ign http://extras.ubuntu.com trusty/main Translation-en_US           
Err http://archive.canonical.com trusty/partner i386 Packages        
  403  Forbidden
Ign http://extras.ubuntu.com trusty/main Translation-en              
Ign http://archive.canonical.com trusty/partner Translation-en_US    
Ign http://archive.canonical.com trusty/partner Translation-en       
Err http://security.ubuntu.com trusty-security/main Sources
  403  Forbidden
Err http://security.ubuntu.com trusty-security/restricted Sources
  403  Forbidden
Err http://security.ubuntu.com trusty-security/universe Sources
  403  Forbidden
Err http://security.ubuntu.com trusty-security/multiverse Sources
  403  Forbidden
Err http://security.ubuntu.com trusty-security/main amd64 Packages
  403  Forbidden
Err http://security.ubuntu.com trusty-security/restricted amd64 Packages
  403  Forbidden
Err http://security.ubuntu.com trusty-security/universe amd64 Packages
  403  Forbidden
Err http://security.ubuntu.com trusty-security/multiverse amd64 Packages
  403  Forbidden
Err http://security.ubuntu.com trusty-security/main i386 Packages
  403  Forbidden
Err http://security.ubuntu.com trusty-security/restricted i386 Packages
  403  Forbidden
Err http://security.ubuntu.com trusty-security/universe i386 Packages
  403  Forbidden
Err http://security.ubuntu.com trusty-security/multiverse i386 Packages
  403  Forbidden
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Ign http://security.ubuntu.com trusty-security/main Translation-en
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Ign http://security.ubuntu.com trusty-security/restricted Translation-en
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Ign http://security.ubuntu.com trusty-security/universe Translation-en
Err http://id.archive.ubuntu.com trusty/main Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/restricted Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/universe Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/multiverse Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/main amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/restricted amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/universe amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/multiverse amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/main i386 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/restricted i386 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/universe i386 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty/multiverse i386 Packages
  403  Forbidden
Ign http://id.archive.ubuntu.com trusty/main Translation-en_US
Ign http://id.archive.ubuntu.com trusty/main Translation-en
Ign http://id.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://id.archive.ubuntu.com trusty/multiverse Translation-en
Ign http://id.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://id.archive.ubuntu.com trusty/restricted Translation-en
Ign http://id.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://id.archive.ubuntu.com trusty/universe Translation-en
Err http://id.archive.ubuntu.com trusty-updates/main Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/restricted Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/universe Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/multiverse Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/main amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/restricted amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/universe amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/main i386 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/restricted i386 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/universe i386 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-updates/multiverse i386 Packages
  403  Forbidden
Ign http://id.archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://id.archive.ubuntu.com trusty-updates/main Translation-en
Ign http://id.archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://id.archive.ubuntu.com trusty-updates/multiverse Translation-en
Ign http://id.archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://id.archive.ubuntu.com trusty-updates/restricted Translation-en
Ign http://id.archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://id.archive.ubuntu.com trusty-updates/universe Translation-en
Err http://id.archive.ubuntu.com trusty-backports/main Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/restricted Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/universe Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/multiverse Sources
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/main amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/restricted amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/universe amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/main i386 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/restricted i386 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/universe i386 Packages
  403  Forbidden
Err http://id.archive.ubuntu.com trusty-backports/multiverse i386 Packages
  403  Forbidden
Ign http://id.archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://id.archive.ubuntu.com trusty-backports/main Translation-en
Ign http://id.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://id.archive.ubuntu.com trusty-backports/multiverse Translation-en
Ign http://id.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://id.archive.ubuntu.com trusty-backports/restricted Translation-en
Ign http://id.archive.ubuntu.com trusty-backports/universe Translation-en_US
Ign http://id.archive.ubuntu.com trusty-backports/universe Translation-en
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  403  Forbidden

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/source/Sources  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/source/Sources  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/partner/source/Sources  403  Forbidden

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://id.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages  403  Forbidden

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Can someone help me to solve this problem? I don't know how to solve it. Thank you :p

---

### Post by v3.xx on 2015-09-15
Well, I'm not so sure about whats going on either.  The output is saying that everything is broke.

Please post the output of ..

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

What country are you in?

---

