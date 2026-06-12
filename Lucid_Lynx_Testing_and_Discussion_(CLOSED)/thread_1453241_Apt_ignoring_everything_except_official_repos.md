---
title: "Apt ignoring everything except official repos"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2010-04-13
I just upgraded a machine to lucid and apt is acting very strangely. It's ignoring everything except the offical repos. PPAs, Medibuntu, the Canonical Partner repo, etc.

```
sudo apt-get update
Ign http://ppa.launchpad.net lucid Release.gpg
Ign http://packages.medibuntu.org lucid Release.gpg                            
Ign http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US   
Ign http://archive.canonical.com lucid Release.gpg                  
Ign http://ppa.launchpad.net lucid Release.gpg                      
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Ign http://ppa.launchpad.net/chromium-daily/beta/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release     
Ign http://packages.medibuntu.org lucid Release
Ign http://archive.canonical.com lucid Release 
Ign http://packages.medibuntu.org lucid/free Packages                          
Ign http://ppa.launchpad.net lucid Release                                     
Ign http://archive.canonical.com lucid/partner Packages                        
Ign http://packages.medibuntu.org lucid/non-free Packages                      
Ign http://ppa.launchpad.net lucid Release                                     
Ign http://archive.canonical.com lucid/partner Packages                        
Ign http://packages.medibuntu.org lucid/free Packages                          
Ign http://ppa.launchpad.net lucid/main Packages                               
Err http://archive.canonical.com lucid/partner Packages                        
  403  Forbidden
Ign http://packages.medibuntu.org lucid/non-free Packages                      
Ign http://ppa.launchpad.net lucid/main Packages                               
Ign http://ppa.launchpad.net lucid/main Packages                               
Err http://packages.medibuntu.org lucid/free Packages                          
  403  Forbidden
Err http://packages.medibuntu.org lucid/non-free Packages                      
  403  Forbidden
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://mirror.anl.gov lucid Release.gpg
Ign http://ppa.launchpad.net lucid/main Packages                   
Err http://ppa.launchpad.net lucid/main Packages                   
  403  Forbidden
Err http://ppa.launchpad.net lucid/main Packages
  403  Forbidden
Err http://ppa.launchpad.net lucid/main Packages
  403  Forbidden
Ign http://mirror.anl.gov/pub/ubuntu/ lucid/main Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid/restricted Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid/universe Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid/multiverse Translation-en_US
Hit http://mirror.anl.gov lucid-updates Release.gpg
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-updates/main Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://mirror.anl.gov lucid-backports Release.gpg
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-backports/main Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://mirror.anl.gov lucid-security Release.gpg
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-security/main Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-security/universe Translation-en_US
Ign http://mirror.anl.gov/pub/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://mirror.anl.gov lucid Release      
Hit http://mirror.anl.gov lucid-updates Release
Hit http://mirror.anl.gov lucid-backports Release                  
Hit http://mirror.anl.gov lucid-security Release                   
Hit http://mirror.anl.gov lucid/main Packages                      
Hit http://mirror.anl.gov lucid/restricted Packages
Hit http://mirror.anl.gov lucid/universe Packages
Hit http://mirror.anl.gov lucid/multiverse Packages
Hit http://mirror.anl.gov lucid-updates/main Packages
Hit http://mirror.anl.gov lucid-updates/restricted Packages
Hit http://mirror.anl.gov lucid-updates/universe Packages
Hit http://mirror.anl.gov lucid-updates/multiverse Packages
Hit http://mirror.anl.gov lucid-backports/main Packages
Hit http://mirror.anl.gov lucid-backports/restricted Packages
Hit http://mirror.anl.gov lucid-backports/universe Packages
Hit http://mirror.anl.gov lucid-backports/multiverse Packages
Hit http://mirror.anl.gov lucid-security/main Packages
Hit http://mirror.anl.gov lucid-security/restricted Packages
Hit http://mirror.anl.gov lucid-security/universe Packages
Hit http://mirror.anl.gov lucid-security/multiverse Packages
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://ppa.launchpad.net/chromium-daily/beta/ubuntu/dists/lucid/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/lucid/main/binary-i386/Packages.gz  403  Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Anyone else have this problem?

---

### Post by FuturePilot on 2010-04-13
Ah, it was because of the squid-deb-proxy setup I was attempting to do.

---

