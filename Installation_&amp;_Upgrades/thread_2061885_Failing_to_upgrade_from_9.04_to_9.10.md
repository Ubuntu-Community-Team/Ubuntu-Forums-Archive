---
title: "Failing to upgrade from 9.04 to 9.10"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by sprilutsky on 2012-09-23
Hi there,

I was trying to upgarde to the newer Ubuntu release 12.04 and everything was pointing that I need to go from one release to another, before I can go to the latest release of Ubuntu.

While I was trying to go from 9.04 to 9.10 ran into the issues (see below). Can some one point me into the right direction, please?

tsp0001@ubuntu_pc:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
tar: Removing leading `/' from member names

Reading cache

Checking package manager

Can not upgrade 

An upgrade from 'jaunty' to 'lucid' is not supported with this tool. 

tsp0001@ubuntu_pc:~$ 
########################################
Also running the below command ran into some errors as well:
########################################
tsp0001@ubuntu_pc:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:2 [http://dl.google.com](http://dl.google.com) stable Release                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1246B]                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release.gpg                
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Translation-en_US     
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Translation-en_US 
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates Release.gpg        
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security Release.gpg       
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
  404 Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
  404 Not Found [IP: 91.189.91.13 80]
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/universe Translation-en_US  
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
  404 Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
  404 Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
  404 Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
  404 Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
  404 Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
  404 Not Found [IP: 91.189.91.13 80]
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/multiverse Packages
Fetched 2791B in 0s (2865B/s)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages)  404 Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-amd64/Packages)  404 Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages)  404 Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages)  404 Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found [IP: 91.189.91.13 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
tsp0001@ubuntu_pc:~$

---

### Post by darkod on 2012-09-23
It's much better to copy your personal data to some external disk, and do a clean install of 12.04. Since you were not doing upgrades for a long time, it will hardly survive all upgrades without any issues.

9.04 is already out of support (as is 9.10), that's why you have that error because the repositories are moved. There are ways to do upgrade of versions that are EOL, but I would recommend doing a clean install of 12.04. Don't forget to get your data out first.
Otherwise, the EOL upgrade documentation is here:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by sprilutsky on 2012-09-23
Thanks for the reply, but is there any way to actuallu gradually upgrade from 9.04 to 9.10 to ... to 12.04? Any other suggestions besides new install?

Regards

---

### Post by darkod on 2012-09-23
Well, I don't see much point in it, but if you insist this seem to be the way to do it:
[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

Make sure you edit the sources.list and keep only the ones specified in the tutorial. I'm not sure it will work if you have more sources specified.

As for 9.10 to 10.04 it should work in a similar way.

Once you get to 10.04 it's easier since 10.04 is still supported and you should be able tp upgrade to 12.04. Just make sure the settings in Update Manager are set to Long Term releases only, so that from 10.04 it offers upgrade to 12.04 and not to 10.10.

Note that problems might occur when doing so many upgrades in a row, so at the end the whole process might not work out for you at all.

---

### Post by coffeecat on 2012-09-23
@sprilutsky, if you read the link darkod has just posted, you'll see that it warns you that do_release_upgrade will return an error. Just over a year ago, I managed to circumvent this problem for the 9.04 -> 9.10 upgrade with the somewhat irregular hack that I describe here:

[http://ubuntuforums.org/showpost.php?p=11129193&postcount=8](http://ubuntuforums.org/showpost.php?p=11129193&postcount=8)

That is, saving the modified /var/lib/update-manager/meta-release file which tricks the system into thinking that 9.10 is still supported. You still have to do everything else in the link.

**However**.... That was a year ago and I was simply experimenting with a system that was not critical and it didn't matter if it broke (it so happens that it didn't). I do not guarantee that this method will still work, and I offer the idea on a try-at-your-own-risk-don't-blame-me-if-it-goes-wrong basis. As always, back up all your data before you try anything.

I agree with darkod that it would be far better and safer to back up all your personal data and do a fresh install of 12.04.

---

### Post by sprilutsky on 2012-09-23
I tried that and it still failed:
tsp0001@ubuntu_pc:~$ sudo do-release-upgrade
sudo: unable to resolve host ubuntu_pc
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
tar: Removing leading `/' from member names

Reading cache

Checking package manager

Can not upgrade 

An upgrade from 'jaunty' to 'lucid' is not supported with this tool.

---

### Post by coffeecat on 2012-09-23
> **sprilutsky said:**
> I tried that and it still failed:

Read my post #5 - the one just before yours. The link darkod posted warns you of this.

---

### Post by sprilutsky on 2012-09-23
Hi COFFEECAT,

Thanks for your responses - it worked. I now have upgraded to Karmic -9.10.

What should be my next step in the effort to upgrading to 12.04?

tsp0001@ubuntu_pc:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
tsp0001@ubuntu_pc:~$ 


Regards

---

### Post by sprilutsky on 2012-09-23
Actually, I figured out, upgrading to 10.04 now.

Thanks for your help

---

### Post by oldos2er on 2012-09-23
Once you have 10.04 installed, if you wish to you can go directly to 12.04 since they are both LTS releases.

---

