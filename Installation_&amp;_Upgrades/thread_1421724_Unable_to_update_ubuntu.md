---
title: "Unable to update ubuntu"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by jamil_1 on 2010-03-04
Hi,
I am unable to update ubuntu/install new software using either the synaptic manager or the terminal. I am behind a proxy. It was working fine that it suddenly started to give errors say proxy authentication required. I can access internet through the broswer and I have added the line: 
export http_proxy=http://Domain\\id:****Paswd****@172.25.10.3:80/

One thing that I want to ask is when we use $ and & in our password do I need escape character or not ? What is the escape character for bash ? \ ?


Here is the dump when I write: sudo apt-get update

[FONT="Courier New"]

jamil@jamil-laptop:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic Release.gpg                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/main Translation-en_US                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic Release                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Err [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
  407  Proxy Authentication Required
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                     
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages   
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  407  Proxy Authentication Required
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources          
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                     
  407  Proxy Authentication Required
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/main Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
  407  Proxy Authentication Required
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
  407  Proxy Authentication Required
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
  407  Proxy Authentication Required
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
  407  Proxy Authentication Required
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
  407  Proxy Authentication Required
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
  407  Proxy Authentication Required
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
  407  Proxy Authentication Required
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
  407  Proxy Authentication Required
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/main Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/restricted Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/universe Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/universe Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/multiverse Sources
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/main Packages
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/restricted Packages
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/main Sources
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/restricted Sources
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/universe Packages
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/universe Sources
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/multiverse Packages
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic/multiverse Sources
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/main Packages
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/restricted Packages
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/main Sources
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/restricted Sources
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/universe Packages
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/universe Sources
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/multiverse Packages
  407  Proxy Authentication Required
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) karmic-updates/multiverse Sources
  407  Proxy Authentication Required
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/main/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://pk.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  407  Proxy Authentication Required

E: Some index files failed to download, they have been ignored, or old ones used instead.[/FONT]

---

