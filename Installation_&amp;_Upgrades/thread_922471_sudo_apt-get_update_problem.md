---
title: "sudo apt-get update problem"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by buntute on 2008-09-17
when I type in terminal sudo apt-get update, it always tries to connect to IP Address 192.168.0.1. This IP is previously my proxy, but now not anymore.
Here is the result:
-------------------------------------------
warnet@ubuntu:~$ sudo apt-get update
[sudo] password for warnet: 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                       
  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                            
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US                      
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                        
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US                      
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                               
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US                    
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US              
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US                
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US              
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg                              
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US                   
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US             
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US               
  Unable to connect to 192.168.0.1 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US             
  Unable to connect to 192.168.0.1 8080:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                                   
  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                        
  Unable to connect to 192.168.0.1 8080:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US                    
  Unable to connect to 192.168.0.1 8080:
Reading package lists... Done                                                         
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release.gpg](http://packages.medibuntu.org/dists/hardy/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
warnet@ubuntu:~$ 
--------------------------------------------------
I have check on my internet-proxy and set to no-proxy, also have unset http_proxy environment, and set Direct Connection on Synaptic, but none of them solve this problem.
Please help...

---

### Post by buntute on 2008-09-18
Never mind. Found the cause finally.
It is because /etc/apt/apt.conf contains:
 Acquire::http::Proxy "http://192.168.0.1:8080/";
After delete its content, now sudo apt-get update working normally.

---

### Post by guimenez on 2008-09-28
the same happens to me, but i don't have nothing in the apt.conf

what can i do?

---

### Post by guimenez on 2008-09-29
thanks for replaying.

i don't have any proxy configuration in update manager. that is the point,i don't know why it still searching for a proxy.

all proxy configuration its disabled (like environment,synaptic,etc)

---

### Post by edfromo on 2008-10-09
> **guimenez said:**
> thanks for replaying.

i don't have any proxy configuration in update manager. that is the point,i don't know why it still searching for a proxy.

all proxy configuration its disabled (like environment,synaptic,etc)

Try doing the update from a different account on the same machine.  I had a similar problem and this worked for me.

---

