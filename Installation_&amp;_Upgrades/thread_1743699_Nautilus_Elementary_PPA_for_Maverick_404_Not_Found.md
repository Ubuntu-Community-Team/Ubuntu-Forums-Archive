---
title: "Nautilus Elementary PPA for Maverick: 404 Not Found"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by jonbwilson on 2011-04-29
Every time I run sudo apt-get update in the terminal, I get an error that the PPA for Nautilus Elementary is not found.  Is this just because of heavy traffic today or is it down?  I can't find anything online saying it's down, but I just did a fresh install of 10.10 after 11.04 jacked my system, and I would really like to get Nautilus Elementary installed. What's the story?

---

### Post by jonbwilson on 2011-04-29
FYI, this is the output of sudo apt-get update:

```
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en   
Hit http://ppa.launchpad.net maverick Release.gpg                   
Ign http://ppa.launchpad.net/alecive/antigone/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en     
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US      
Hit http://extras.ubuntu.com maverick Release                             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://ppa.launchpad.net/alecive/antigone/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                    
Hit http://extras.ubuntu.com maverick/main Sources                                               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Hit http://extras.ubuntu.com maverick/main i386 Packages
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-security Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release    
Hit http://us.archive.ubuntu.com maverick-updates Release            
Hit http://us.archive.ubuntu.com maverick-security Release           
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://ppa.launchpad.net maverick Release.gpg    
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources               
Hit http://us.archive.ubuntu.com maverick/main i386 Packages               
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages         
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages           
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources             
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources       
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages   
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages 
Hit http://us.archive.ubuntu.com maverick-security/main Sources            
Hit http://us.archive.ubuntu.com maverick-security/restricted Sources
Hit http://us.archive.ubuntu.com maverick-security/universe Sources
Hit http://us.archive.ubuntu.com maverick-security/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-security/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg    
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/deluge-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/deluge-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/hel-sheep/pastie/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/hel-sheep/pastie/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ruben-verweij/thunderbird-indicator/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ruben-verweij/thunderbird-indicator/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/shutter/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/shutter/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release        
Hit http://ppa.launchpad.net maverick Release        
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release  
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release  
Hit http://ppa.launchpad.net maverick Release  
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release                              
Hit http://ppa.launchpad.net maverick Release        
Hit http://ppa.launchpad.net maverick Release  
Hit http://ppa.launchpad.net maverick Release  
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release  
Ign http://ppa.launchpad.net maverick/main Sources                         
Ign http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Ign http://ppa.launchpad.net maverick/main Sources
Ign http://ppa.launchpad.net maverick/main i386 Packages
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/am-monkeyd/nautilus-elementary/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/am-monkeyd/nautilus-elementary/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

