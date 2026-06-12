---
title: "Cannot Connect to Software Archives"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by edsellsstuff on 2011-02-25
Receive the following error when trying to install packages using Software Center or Synaptic Manager. Was working fine just until the other day.

Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/universe/p/pdfedit/pdfedit_0.4.5-1_i386.deb](http://my.archive.ubuntu.com/ubuntu/pool/universe/p/pdfedit/pdfedit_0.4.5-1_i386.deb) Could not connect to my.archive.ubuntu.com:80 (203.106.62.88). - connect (111: Connection refused)

I'm using Ubuntu 10.10 - the Maverick Meerkat - released in October 2010

I tried the following:
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install codeblocks

Using any of these command did not help and received the following output and one would see "could not connect messages and failed to fetch". 

Any help and or leads would be appreciated in resolving the issue.

-------------------------------------------------------------------------
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en                 
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick Release.gpg                          
  Could not connect to my.archive.ubuntu.com:80 (203.106.62.88). - connect (111: Connection refused)
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates Release.gpg                  
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to my.archive.ubuntu.com:http:
Err [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
  Unable to connect to my.archive.ubuntu.com:http:
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Reading package lists... Done
W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://my.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to my.archive.ubuntu.com:80 (203.106.62.88). - connect (111: Connection refused)

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to my.archive.ubuntu.com:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by zenwalker on 2011-02-25
What is the mode your internet connection? Are you able to browse via browser? Are you behind proxy? Check if your internet is available at that moment. Try to browse any of those failed links (as it says by the synaptic, etc) via browser.

---

### Post by edsellsstuff on 2011-02-27
To your question about internet connection. The internet works find, can do anything I want to do, surf, email, download videos, even live streaming of TV. In addition I am not using a proxy. The only new thing I have done recently was to install pdns-resolver and configure it to improve speed performance. That is why i'm a bit confused why I cannot connect to the ubuntu servers.

Another Note: I have another Ubuntu version (LTS) installed on same computer and it works fine and connect upgrade etc. as expected. Thus leaving me to believe maybe I have a corrupt file somewhere.

---

### Post by edsellsstuff on 2011-03-01
:D Yes it looked like the cache file was corrupted. What I did was to open the software center and within the edit menu software sources. Then changed the download from location to another server. This forced an update of the cache and when completed, I was able to install a software package without a problem.:) Problem resolved

---

