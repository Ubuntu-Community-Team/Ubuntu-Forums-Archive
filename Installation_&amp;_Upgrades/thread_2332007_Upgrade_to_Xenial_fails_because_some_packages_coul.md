---
title: "Upgrade to Xenial fails because some packages could not be downloaded"
date: 2016-07-27
forum: Installation &amp; Upgrades
---

### Post by eje2112 on 2016-07-27
Here's the end of the transcript for [FONT=courier new]do-release-upgrade[/FONT]:

```
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/universe ktorrent amd64 4.3.1-4                                                                                                                                                                    
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/main libtracker-sparql-1.0-0 amd64 1.6.2-0ubuntu1                                                                                                                                                  
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/main libxatracker2 amd64 11.2.0-1ubuntu2                                                                                                                                                           
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/universe libktorrent5 amd64 1.3.1-5build2                                                                                                                                                          
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/universe ktorrent-data all 4.3.1-4                                                                                                                                                                 
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/universe libktorrent-l10n all 1.3.1-5build2                                                                                                                                                        
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/universe ktorrent amd64 4.3.1-4                                                                                                                                                                    
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/main libtracker-sparql-1.0-0 amd64 1.6.2-0ubuntu1                                                                                                                                                  
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/main libxatracker2 amd64 11.2.0-1ubuntu2                                                                                                                                                           
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/universe libktorrent5 amd64 1.3.1-5build2                                                                                                                                                          
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/universe ktorrent-data all 4.3.1-4                                                                                                                                                                 
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/universe libktorrent-l10n all 1.3.1-5build2                                                                                                                                                        
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/universe ktorrent amd64 4.3.1-4                                                                                                                                                                    
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Err http://us.archive.ubuntu.com/ubuntu/ xenial/main libtracker-sparql-1.0-0 amd64 1.6.2-0ubuntu1                                                                                                                                                  
  Connection failed [IP: 91.189.91.26 80]                                                                                                                                                                                                          
Fetched 0 B in 6s (0 B/s)                                                                                                                                                                                                                          
    
Could not download the upgrades 
    
The upgrade has aborted. Please check your Internet connection or 
installation media and try again. All files downloaded so far have 
been kept. 
    
Failed to fetch 
http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libxatracker2_11.2.0-1ubuntu2_amd64.deb 
Connection failed [IP: 91.189.91.26 80] 
Failed to fetch 
http://us.archive.ubuntu.com/ubuntu/pool/universe/libk/libktorrent/libktorrent5_1.3.1-5build2_amd64.deb 
Connection failed [IP: 91.189.91.26 80] 
Failed to fetch 
http://us.archive.ubuntu.com/ubuntu/pool/universe/k/ktorrent/ktorrent-data_4.3.1-4_all.deb 
Connection failed [IP: 91.189.91.26 80] 
Failed to fetch 
http://us.archive.ubuntu.com/ubuntu/pool/universe/libk/libktorrent/libktorrent-l10n_1.3.1-5build2_all.deb 
Connection failed [IP: 91.189.91.26 80] 
Failed to fetch 
http://us.archive.ubuntu.com/ubuntu/pool/universe/k/ktorrent/ktorrent_4.3.1-4_amd64.deb 
Connection failed [IP: 91.189.91.26 80] 
Failed to fetch 
http://us.archive.ubuntu.com/ubuntu/pool/main/t/tracker/libtracker-sparql-1.0-0_1.6.2-0ubuntu1_amd64.deb 
Connection failed [IP: 91.189.91.26 80] 
      
Restoring original system state
    
Aborting

```

I tried to manually uninstall some of the packages but it didn't seem to make a difference.

I tried this:

```
sudo apt-get --force-yes remove ktorrent-data libktorrent5 libktorrent-l10n ktorrent libtracker-sparql-1.0-0 libxatracker2 xserver-xorg-video-vmware xserver-xorg-video-all libappstream3 appstream kget
```

This is everything that [FONT=courier new]do-release-upgrade[/FONT] can't install and its dependencies, but [FONT=courier new]do-release-upgrade[/FONT] is still trying to download those same packages.

---

### Post by Bashing-om on 2016-07-27
eje2112; Hello; Welcome to the forum.

Hey, is the current system fully updated ?
What does the package manager relate :
please show the complete outputs of terminal commands:
```

sudo apt update
sudo apt upgrade

```

we see where we go from here.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

