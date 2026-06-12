---
title: "Downloading package indexes failed (Hardware Drivers)"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by s7ev1n on 2010-07-09
Hello everyone,

When I go to System/Administration/Hardware Drivers I have an error message:

Downloading package indexes failed, please check your network status. Most drivers will not be available.

After that I get the Hardware Drivers window empty..

My network is working fine so I don't know whats the problem,

Please the attachments files for more details,

Thank you

---

### Post by s7ev1n on 2010-08-26
Anyone?

---

### Post by plucky on 2010-08-26
Open a terminal (**Applications > Accessories > Terminal**) and run ```
sudo apt-get update
``` and post results.

---

### Post by jon.reeve on 2010-12-28
Having the same issue trying to install drivers on a MacBook. Apt-get update works fine.

---

### Post by meashsoft on 2011-01-03
I got This please Help !!

```
Get:1 http://us.archive.ubuntu.com maverick Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Get:2 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:4 http://us.archive.ubuntu.com maverick Release [39.8kB]
Err http://us.archive.ubuntu.com maverick Release                      
  
Get:5 http://security.ubuntu.com maverick-security Release [27.2kB]    
Err http://security.ubuntu.com maverick-security Release
  
Get:6 http://us.archive.ubuntu.com maverick-updates Release [31.4kB]
Err http://us.archive.ubuntu.com maverick-updates Release
  
Fetched 597B in 2s (297B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by wojox on 2011-01-03
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```

---

### Post by themadhatter0 on 2011-01-06
I've got exactly the same problem on a Dell Precision M4400. Wojox's suggestion gets a clean update for apt, but it doesn't solve the driver problem.

There are so many niggles with this release of Ubuntu, I am actually considering getting Windows 7 instead :(

---

### Post by themadhatter0 on 2011-02-02
I ended up downloading the proprietary drivers I needed from the vendor's website and installing them manually. 

I still can't figure out what's wrong with jockey, but at least everything is working now!

---

### Post by VadimS on 2011-02-11
Had the same issue crop up today, worked fine yesterday. Possibly after an update.
apt-get update comes up fine.
It's obviously connected to the Internet (I'm running it right now).

I've got it installed to an external drive and I move it around regularly, and I end up re-installing the drivers quite often, don't want to have to do it manually.

---

### Post by nicktaiwan on 2011-02-12
Hi,

I've just installed 10.10 64 bit (from USB stick) on a brand new HD (no other OS on it) on my Acer 5520 laptop and I've got the same issue as posted above, here is the output of a sudo apt-get update:

Err [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick Release.gpg
  Could not connect to tw.archive.ubuntu.com:80 (140.112.8.139). - connect (111: Connection refused)
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick-updates Release.gpg
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
  Unable to connect to tw.archive.ubuntu.com:http:
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Reading package lists...

I installed 10.10 yesterday on a different machine and I did not have issues.

I currently don't have a way to install proprietary drivers automatically and doing it manually won't solve the whole issue.

Cheers,

Nick

---

### Post by nicktaiwan on 2011-02-12
Sorry the output log was incomplete for apt-get update, here is the complete log:

Err [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick Release.gpg
  Could not connect to tw.archive.ubuntu.com:80 (140.112.8.139). - connect (111: Connection refused)
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                  
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US                               
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                            
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US                         
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                            
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US                         
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                                                                    
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US                                                                                 
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) maverick-updates Release.gpg                                                                                                
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                                                                                
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US                       
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en                    
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US                 
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en                    
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US                 
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en                      
  Unable to connect to tw.archive.ubuntu.com:http:
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US                                                                         
  Unable to connect to tw.archive.ubuntu.com:http:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]                                                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [31.4kB]
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [9,762B]
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources [656B]    
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [26.7kB]
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages [700B]  
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [10.6kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [643B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages [91.1kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages [14B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages [47.0kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages [1,512B]
Fetched 220kB in 3s (61.3kB/s)                          
Reading package lists... Done
W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://tw.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to tw.archive.ubuntu.com:80 (140.112.8.139). - connect (111: Connection refused)

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to tw.archive.ubuntu.com:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

Also I've tried Wojox's way and I still have the same problem ...

Is anyone encountering this problem on 32 bits ? I've installed hundreds of 32 bits before and no issue and now I've this issue with 64 bit for my first install.

Cheers,

Nick

---

### Post by plucky on 2011-02-12
Try a different server as the tw server seems to be offline.

Open **Software Sources** and on the first page at the "Download From" button,select a different server.

Good Luck

---

### Post by nicktaiwan on 2011-02-12
Hi Plucky,

Thanks it worked when switching to another country.

Nick

---

### Post by VadimS on 2011-02-14
Seems we had the same symptoms but not cause.
I tried several different servers to no avail.



Get:1 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick Release.gpg [198B]
Ign [http://www.lug.bu.edu/mirror/ubuntu/](http://www.lug.bu.edu/mirror/ubuntu/) maverick/main Translation-en                                                                                        
Get:2 [http://www.lug.bu.edu/mirror/ubuntu/](http://www.lug.bu.edu/mirror/ubuntu/) maverick/main Translation-en_CA [10.1kB]                                                                          
Ign [http://www.lug.bu.edu/mirror/ubuntu/](http://www.lug.bu.edu/mirror/ubuntu/) maverick/multiverse Translation-en                                                                                  
Ign [http://www.lug.bu.edu/mirror/ubuntu/](http://www.lug.bu.edu/mirror/ubuntu/) maverick/multiverse Translation-en_CA             
Ign [http://www.lug.bu.edu/mirror/ubuntu/](http://www.lug.bu.edu/mirror/ubuntu/) maverick/restricted Translation-en                
Get:3 [http://www.lug.bu.edu/mirror/ubuntu/](http://www.lug.bu.edu/mirror/ubuntu/) maverick/restricted Translation-en_CA [425B]    
Ign [http://www.lug.bu.edu/mirror/ubuntu/](http://www.lug.bu.edu/mirror/ubuntu/) maverick/universe Translation-en                  
Ign [http://www.lug.bu.edu/mirror/ubuntu/](http://www.lug.bu.edu/mirror/ubuntu/) maverick/universe Translation-en_CA               
Get:4 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick Release [39.8kB]                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                                 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_CA                               
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                              
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                           
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_CA                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                  
Ign [http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu/](http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu/](http://ppa.launchpad.net/glennric/dolphin-emu/ubuntu/) maverick/main Translation-en_CA
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                
Get:5 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick/restricted Sources [4,370B]                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                                 
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en                             
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_CA                          
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                         
Get:6 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick/main Sources [829kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages
Get:7 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick/multiverse Sources [151kB]
Get:8 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick/universe Sources [4,179kB]
Get:9 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick/multiverse i386 Packages [183kB]                                                                                        
Get:10 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick/restricted i386 Packages [5,992B]                                                                                      
Get:11 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick/universe i386 Packages [5,791kB]                                                                                       
Get:12 [http://www.lug.bu.edu](http://www.lug.bu.edu) maverick/main i386 Packages [1,492kB]                                                                                           
Fetched 12.7MB in 29s (430kB/s)                                                                                                                              
Reading package lists... Done

---

### Post by VadimS on 2011-02-15
Seems I'm stuck manually installing the ATI driver once a week.

---

### Post by Ben_neB on 2011-06-23
Is there an actual fix for this yet? I have the same problem, and it's REALLY getting annoying... I have tried every fix mentioned here to no avail. I'm running Ubuntu 10.10

---

### Post by dhumphries_ on 2011-11-20
I have the same problem. I'm trying to connect to the internet on an compaq presario that i just installed ubuntu 10.04 on. when i went to system/admin/hardwear drivers i got this message. i looked on here and found this tread and saw that it was solved so i tried the code that was first posted on here my results were:

Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Reading package lists... Done 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Some index files failed to download, they have been ignored, or old ones used instead. 

I apologize if this is annoying. im new to linux and ubuntu but would like to get familiar with it. should i find the drives on my other laptop and try to install them manual by transferring them on my flashdrive. once again im sorry if this is stupid i love computers but dont have the means for school or anything and if someone could point me in the right direction how to fix this maybe i needed a different code than the ones posted.

---

