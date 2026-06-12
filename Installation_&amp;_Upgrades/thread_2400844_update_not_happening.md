---
title: "update not happening"
date: 2018-09-11
forum: Installation &amp; Upgrades
---

### Post by shann123 on 2018-09-11
hi 
update not happening, some error. log attached. kindly help in resolving this issue

```
crl@crl-bel:~$ sudo apt-get update
[sudo] password for crl: 
Err [http://downloads.quanergy.com](http://downloads.quanergy.com) trusty InRelease                             
  
Err [http://dl.google.com](http://dl.google.com) stable InRelease                                      
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
  Unable to connect to 172.16.24.10:3128:
Err [http://downloads.quanergy.com](http://downloads.quanergy.com) trusty Release.gpg                           
  Unable to connect to 172.16.24.10:3128:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Unable to connect to 172.16.24.10:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty InRelease                              
  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates InRelease                      
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports InRelease                    
  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-security InRelease
  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty Release.gpg
  Unable to connect to 172.16.24.10:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates Release.gpg
  Unable to connect to 172.16.24.10:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports Release.gpg
  Unable to connect to 172.16.24.10:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
  Unable to connect to 172.16.24.10:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-security Release.gpg
  Unable to connect to 172.16.24.10:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
  Unable to connect to 172.16.24.10:3128:
Err [http://packages.ros.org](http://packages.ros.org) trusty InRelease  
  
Err [http://packages.ros.org](http://packages.ros.org) trusty Release.gpg
  Unable to connect to 172.16.24.10:3128:
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease](http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://downloads.quanergy.com/qview-bahama/ubuntu/dists/trusty/InRelease](http://downloads.quanergy.com/qview-bahama/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/ddalex/gstreamer/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/ddalex/gstreamer/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://packages.ros.org/ros/ubuntu/dists/trusty/InRelease](http://packages.ros.org/ros/ubuntu/dists/trusty/InRelease)  

W: Failed to fetch [http://downloads.quanergy.com/qview-bahama/ubuntu/dists/trusty/Release.gpg](http://downloads.quanergy.com/qview-bahama/ubuntu/dists/trusty/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Failed to fetch [http://ppa.launchpad.net/ddalex/gstreamer/ubuntu/dists/trusty/Release.gpg](http://ppa.launchpad.net/ddalex/gstreamer/ubuntu/dists/trusty/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Failed to fetch [http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu/dists/trusty/Release.gpg](http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu/dists/trusty/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Failed to fetch [http://packages.ros.org/ros/ubuntu/dists/trusty/Release.gpg](http://packages.ros.org/ros/ubuntu/dists/trusty/Release.gpg)  Unable to connect to 172.16.24.10:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by mörgæs on 2018-09-11
Hi, welcome to the fora.

It could be something as simple as a network glitch. Does it work better after a reboot?

By the way, Trusty Tahr is Ubuntu 14.04. Are you sure that you want to keep software that old?

---

