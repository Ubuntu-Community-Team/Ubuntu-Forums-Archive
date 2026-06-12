---
title: "Upgrade 15.10 to 16.04 - unable to download repository"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by Jim Breen on 2016-09-09
Like some others I have run into this problem when attempting to upgrade.

ls -ld /etc/apt/sources.list.d/*  gives:
-rw-r--r-- 1 root root 118 Sep 10 12:04 /etc/apt/sources.list.d/aheck-ubuntu-ppa-wily.list
-rw-r--r-- 1 root root 118 Sep 10 12:04 /etc/apt/sources.list.d/aheck-ubuntu-ppa-wily.list.save
-rw-r--r-- 1 root root  73 Sep 10 12:04 /etc/apt/sources.list.d/spideroakone.list
-rw-r--r-- 1 root root  73 Sep 10 12:04 /etc/apt/sources.list.d/spideroakone.list.save

sudo apt update (at the end) gives:

....
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse Sources                                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                                                   
  404  Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main amd64 Packages                                        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                                                    
  404  Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted amd64 Packages                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en_AU                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe amd64 Packages                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse amd64 Packages                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main i386 Packages                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted i386 Packages                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe i386 Packages                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse i386 Packages                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main Translation-en                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse Translation-en                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted Translation-en                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe Translation-en                                    
Fetched 2,539 B in 12s (205 B/s)                                                                        
W: GPG error: [http://APT.spideroak.com](http://APT.spideroak.com) release InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 573E3D1C51AE1B3D
W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Not that fussed about the SpiderOak client - I can remove it and start afresh, but the launchpad 
stuff might be more serious.

---

### Post by uRock on 2016-09-10
You may have to go into Software Sources and disable the mentioned PPA.

---

### Post by Jim Breen on 2016-09-11
Many thanks. That seems to have done the trick. Now for a deep breath and The Upgrade....

---

### Post by uRock on 2016-09-14
Awesome! Hopefully the upgrade went well!

---

### Post by Bucky Ball on 2016-09-14
You can upgrade from the unsupported 15.10 to the supported 16.04? That's an innovation. Thought you might need to [look here]("https://help.ubuntu.com/community/EOLUpgrades"). 

[Here's a release schedule]("http://www.ubuntu.com/info/release-end-of-life") for your future reference.

Before upgrading you should switch off (disable) any PPAs you have installed manually and any video drivers, too, if you can get the machine to run on the open-source one. This will give you the easiest ride. You may find yourself picking through a haystack with a heap of leftover PPAs and drivers in an attempt to locate what is screwing up your upgrade otherwise (like now).

As 'vanilla' as you can get it before an upgrade is rule-of-thumb. Less problematic.

---

