---
title: "apt-get gives 503 service unavailable"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by kemitix on 2007-03-04
My laptop is giving a 503 error message for each network deb lines in sources.list.  The server and network is all okay as I can fetch the file with wget with no problems.

I have another PC on the same LAN and it can run apt-get update properly.

Any suggestions?

Here is a copy of the result of running apt-get update:

```
pcampbell@titan:~$ sudo apt-get update
Ign http://download.skype.com stable Release.gpg
Ign http://gb.archive.ubuntu.com edgy Release.gpg                                             
Ign http://gb.archive.ubuntu.com edgy/universe Translation-en_GB                              
Ign http://gb.archive.ubuntu.com edgy/main Translation-en_GB                                  
Ign http://security.ubuntu.com edgy-security Release.gpg                                      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_GB                       
Ign http://security.ubuntu.com edgy-security/main Translation-en_GB                           
Ign http://download.skype.com stable/non-free Translation-en_GB                               
Ign http://gb.archive.ubuntu.com edgy/multiverse Translation-en_GB                            
Ign http://archive.ubuntu.com edgy-updates Release.gpg               
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_GB
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com edgy/restricted Translation-en_GB   
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_GB
Ign http://download.skype.com stable Release                         
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_GB    
Ign http://gb.archive.ubuntu.com edgy Release                        
Ign http://download.skype.com stable/non-free Packages               
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_GB
Ign http://security.ubuntu.com edgy-security Release
Ign http://gb.archive.ubuntu.com edgy/universe Packages        
Ign http://gb.archive.ubuntu.com edgy/main Packages            
Ign http://gb.archive.ubuntu.com edgy/multiverse Packages
Ign http://gb.archive.ubuntu.com edgy/restricted Packages
Ign http://gb.archive.ubuntu.com edgy/universe Sources
Ign http://gb.archive.ubuntu.com edgy/main Sources
Ign http://gb.archive.ubuntu.com edgy/multiverse Sources
Ign http://gb.archive.ubuntu.com edgy/restricted Sources
Errhttp://gb.archive.ubuntu.com edgy/universe Packages
  503 Service Unavailable
Errhttp://gb.archive.ubuntu.com edgy/main Packages
  503 Service Unavailable
Errhttp://gb.archive.ubuntu.com edgy/multiverse Packages
  503 Service Unavailable
Errhttp://gb.archive.ubuntu.com edgy/restricted Packages
  503 Service Unavailable
Errhttp://gb.archive.ubuntu.com edgy/universe Sources
  503 Service Unavailable
Errhttp://gb.archive.ubuntu.com edgy/main Sources
  503 Service Unavailable
Errhttp://gb.archive.ubuntu.com edgy/multiverse Sources
  503 Service Unavailable
Errhttp://gb.archive.ubuntu.com edgy/restricted Sources
  503 Service Unavailable
Ign http://security.ubuntu.com edgy-security/universe Packages
Ign http://security.ubuntu.com edgy-security/main Packages
Ign http://security.ubuntu.com edgy-security/multiverse Packages
Ign http://security.ubuntu.com edgy-security/restricted Packages
Ign http://security.ubuntu.com edgy-security/universe Sources
Ign http://security.ubuntu.com edgy-security/main Sources
Ign http://security.ubuntu.com edgy-security/multiverse Sources
Ign http://security.ubuntu.com edgy-security/restricted Sources
Errhttp://security.ubuntu.com edgy-security/universe Packages
  503 Service Unavailable
Errhttp://security.ubuntu.com edgy-security/main Packages
  503 Service Unavailable
Errhttp://security.ubuntu.com edgy-security/multiverse Packages
  503 Service Unavailable
Errhttp://security.ubuntu.com edgy-security/restricted Packages
  503 Service Unavailable
Errhttp://security.ubuntu.com edgy-security/universe Sources
  503 Service Unavailable
Errhttp://security.ubuntu.com edgy-security/main Sources
  503 Service Unavailable
Errhttp://security.ubuntu.com edgy-security/multiverse Sources
  503 Service Unavailable
Errhttp://security.ubuntu.com edgy-security/restricted Sources
  503 Service Unavailable
Errhttp://download.skype.com stable/non-free Packages
  503 Service Unavailable
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports Release.gpg
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy-proposed Release.gpg
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_GB
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_GB
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy-updates Release
Ign http://archive.ubuntu.com edgy-backports Release
Ign http://archive.ubuntu.com edgy-proposed Release
Ign http://archive.ubuntu.com edgy-updates/universe Packages
Ign http://archive.ubuntu.com edgy-updates/main Packages
Ign http://archive.ubuntu.com edgy-updates/multiverse Packages
Ign http://archive.ubuntu.com edgy-updates/restricted Packages
Ign http://archive.ubuntu.com edgy-updates/universe Sources
Ign http://archive.ubuntu.com edgy-updates/main Sources
Ign http://archive.ubuntu.com edgy-updates/multiverse Sources
Ign http://archive.ubuntu.com edgy-updates/restricted Sources
Ign http://archive.ubuntu.com edgy-backports/universe Packages
Ign http://archive.ubuntu.com edgy-backports/main Packages
Ign http://archive.ubuntu.com edgy-backports/multiverse Packages
Ign http://archive.ubuntu.com edgy-backports/restricted Packages
Ign http://archive.ubuntu.com edgy-backports/universe Sources
Ign http://archive.ubuntu.com edgy-backports/main Sources
Ign http://archive.ubuntu.com edgy-backports/multiverse Sources
Ign http://archive.ubuntu.com edgy-backports/restricted Sources
Ign http://archive.ubuntu.com edgy-proposed/universe Packages
Ign http://archive.ubuntu.com edgy-proposed/main Packages
Ign http://archive.ubuntu.com edgy-proposed/multiverse Packages
Ign http://archive.ubuntu.com edgy-proposed/restricted Packages
Ign http://archive.ubuntu.com edgy-proposed/universe Sources
Ign http://archive.ubuntu.com edgy-proposed/main Sources
Ign http://archive.ubuntu.com edgy-proposed/multiverse Sources
Ign http://archive.ubuntu.com edgy-proposed/restricted Sources
Errhttp://archive.ubuntu.com edgy-updates/universe Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-updates/main Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-updates/multiverse Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-updates/restricted Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-updates/universe Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-updates/main Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-updates/multiverse Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-updates/restricted Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-backports/universe Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-backports/main Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-backports/multiverse Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-backports/restricted Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-backports/universe Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-backports/main Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-backports/multiverse Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-backports/restricted Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-proposed/universe Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-proposed/main Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-proposed/multiverse Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-proposed/restricted Packages
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-proposed/universe Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-proposed/main Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-proposed/multiverse Sources
  503 Service Unavailable
Errhttp://archive.ubuntu.com edgy-proposed/restricted Sources
  503 Service Unavailable
Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  503 Service Unavailable
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz  503 Service Unavailable
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  503 Service Unavailable
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz  503 Service Unavailable
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz  503 Service Unavailable
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz  503 Service Unavailable
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz  503 Service Unavailable
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/source/Sources.gz  503 Service Unavailable
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/source/Sources.gz  503 Service Unavailable
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by taurus on 2007-03-04
I've heard that if you replace the http with ftp in /etc/apt/sources.list, everything should work again.

```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```

---

### Post by kemitix on 2007-03-04
Thanks.  That is working now.

Does anyone know *why* this happens?

---

### Post by pejcao on 2007-03-04
> **taurus said:**
> I've heard that if you replace the http with ftp in /etc/apt/sources.list, everything should work again.

```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```

Still hangs/freez'es on updating, any other ideas?

EDIT: pinging archive.ubuntu.com gives me 170ms or less, that's odd!

OTHER EDIT: placing 200.44.32.12 & 200.44.32.13 as DNS's does'nt helps (CANTV's {Venezuela} primary + 2° DNS's {asigned via DHCP}. Those work) . I can get whatever I want on the Internet but a "HANG OUT TIME" on apt's update.

Tried those threads about dhcpc3 (client) (editing /etc/dhcp3/dhclient.conf + forcing DNS's are allready set but not success)

forgive my spelling! (I'm from Venezuela ES_ve speaking) tnx in advance for any help!  Can't  update!

---

### Post by kemitix on 2007-03-05
I've figured out what had been causing my problems.

I had previously been using a proxy on the laptop, but had stopped using it for a while.  All references to it had been removed from /etc/apt/apt.conf and /etc/wgetrc.  However I didn't realise that there was still an environment variable being set: **http_proxy**.  There as no corresponding ftp_proxy, thus the change to using ftp rather than http worked.

I had searched for references to proxy settings in my /etc directory, but hadn't found any.  What I hadn't checked were the Gnome settings.  **System - Preferences - Network Proxy**  This was what had been setting my environment.  (But for some reason it didn't set the ftp_proxy variable despite having a proxy defined for it.)

Removing the proxy settings and reverting my /etc/apt/sources.list to http and my apt-get update is now behaving as expected.

---

