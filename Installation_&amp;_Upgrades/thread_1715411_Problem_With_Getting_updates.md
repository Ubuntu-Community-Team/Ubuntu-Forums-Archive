---
title: "Problem With Getting updates"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by Hotel Bravo on 2011-03-26
Hi every time I try to do a sudo ap-get update i get this```
Err http://archive.canonical.com lucid Release.gpg                                                                                                                     
  Could not connect to 98.168.182.109:8123 (98.168.182.109), connection timed out
Err http://archive.canonical.com/ubuntu/ lucid/partner Translation-en                                                                                                  
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com maverick Release.gpg                                                                                                                  
  Could not connect to 98.168.182.109:8123 (98.168.182.109), connection timed out
Err http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                                                               
  Unable to connect to 98.168.182.109:8123:
Err http://archive.canonical.com maverick Release.gpg                                                                                                                  
  Unable to connect to 98.168.182.109:8123:
Err http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                                                               
  Unable to connect to 98.168.182.109:8123:
Err http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US                                                                                            
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                                  
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                          
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                       
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US                    
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                       
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US                    
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                         
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                      
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com maverick-updates Release.gpg                                     
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                     
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US                  
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en               
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US            
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en               
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US            
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                 
  Unable to connect to 98.168.182.109:8123:
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US              
  Unable to connect to 98.168.182.109:8123:
Err http://security.ubuntu.com maverick-security Release.gpg                                      
  Could not connect to 98.168.182.109:8123 (98.168.182.109), connection timed out
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                      
  Unable to connect to 98.168.182.109:8123:
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US                   
  Unable to connect to 98.168.182.109:8123:
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                
  Unable to connect to 98.168.182.109:8123:
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US             
  Unable to connect to 98.168.182.109:8123:
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                
  Unable to connect to 98.168.182.109:8123:
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US             
  Unable to connect to 98.168.182.109:8123:
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                  
  Unable to connect to 98.168.182.109:8123:
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US               
  Unable to connect to 98.168.182.109:8123:
Err http://ppa.launchpad.net maverick Release.gpg                                                 
  Could not connect to 98.168.182.109:8123 (98.168.182.109), connection timed out
Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en                 
  Unable to connect to 98.168.182.109:8123:
Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US              
  Unable to connect to 98.168.182.109:8123:
Reading package lists... Done                                                                     
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Could not connect to 98.168.182.109:8123 (98.168.182.109), connection timed out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Could not connect to 98.168.182.109:8123 (98.168.182.109), connection timed out

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Could not connect to 98.168.182.109:8123 (98.168.182.109), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/Release.gpg  Could not connect to 98.168.182.109:8123 (98.168.182.109), connection timed out

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Unable to connect to 98.168.182.109:8123:

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Unable to connect to 98.168.182.109:8123:
``` If anyone can help me out with this I would be very greatful.

---

### Post by Dark_Stang on 2011-03-26
Try another server, I can't ping that one either.

To select another server, open up software sources. Then choose a different server for the "Download From" list. Or just choose "Select Best Server" and it will choose the server with the least latency.

---

