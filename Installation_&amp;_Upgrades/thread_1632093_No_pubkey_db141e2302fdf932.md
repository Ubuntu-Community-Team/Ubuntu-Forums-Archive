---
title: "No_pubkey db141e2302fdf932"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by ethanpk on 2010-11-27
i was trying to install a touchpad indicator app, as per these instructions:


To install Touchpad Indicator in Ubuntu (10.10 Maverick Meerkat only), you'll have to use the same PPA for Picapy:
sudo add-apt-repository ppa:lorenzo-carbonell/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator

after running "sudo apt-get update" I got this message:


ethankelley@ubuntu:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [316B]                     
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/) maverick/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [57.3kB]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Get:5 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,098B]                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages/DiffIndex            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner amd64 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Fetched 2,959B in 1s (1,619B/s)
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932


what is the pubkey issue and how can I fix it?

---

### Post by oldos2er on 2010-11-27
Remove the Lucid repositories from your sources.

Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```

---

### Post by low351 on 2010-11-29
That doesn't work for me...

[COLOR="Navy"]udo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
gpg: requesting key 02FDF932 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0[/COLOR]

---

### Post by oldos2er on 2010-11-29
Sometimes the server seems to be down or very slow. Try again a little later.

---

### Post by patrickcage on 2010-11-29
> **oldos2er said:**
> Remove the Lucid repositories from your sources.

Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```

That solved it for me, thanks Ann

---

### Post by francois.e on 2010-11-29
This is the solution for me too on ubuntu 10.10. 

Thanks **oldos2er.**

---

### Post by Altimos on 2010-11-30
Does not work for me...

```
jeremy@Kenrom:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
gpg: requesting key 02FDF932 from hkp server keyserver.ubuntu.com
gpg: key 02FDF932: "Launchpad Application Review Board PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

---

### Post by oldos2er on 2010-11-30
Looks like you already have that key. Can you post the output of ```
sudo apt-get update
```?

---

### Post by halcyonz on 2010-12-01
> **oldos2er said:**
> Remove the Lucid repositories from your sources.

Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```

Thanks, worked immediately. :popcorn:

---

### Post by Anubis on 2010-12-01
> **oldos2er said:**
> Remove the Lucid repositories from your sources.

Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```
Thanks

---

### Post by oldos2er on 2010-12-01
You're all welcome.

---

### Post by oglipogli on 2011-02-25
> **oldos2er said:**
> Looks like you already have that key. Can you post the output of ```
sudo apt-get update
```?

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
gpg: requesting key 02FDF932 from hkp server keyserver.ubuntu.com
gpg: key 02FDF932: public key "Launchpad Application Review Board PPA" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
administrator@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)/ feisty/main Translation-en_IN
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)/ feisty/restricted Translation-en_IN
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid Release.gpg                                    
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN       
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_IN              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/) lucid/main Translation-en_IN
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/) lucid/main Translation-en_IN
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_IN
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get: 3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,082B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid/main Translation-en_IN                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid/restricted Translation-en_IN           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid/universe Translation-en_IN             
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid/multiverse Translation-en_IN           
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates Release.gpg                            
Get: 4 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_IN                
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid-updates/main Translation-en_IN         
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_IN            
Get: 5 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid-updates/restricted Translation-en_IN   
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid-updates/universe Translation-en_IN     
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid-updates/multiverse Translation-en_IN   
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security Release.gpg                           
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid-security/main Translation-en_IN        
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid-security/restricted Translation-en_IN  
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) lucid-security/multiverse Translation-en_IN
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid Release
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates Release                          
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security Release                         
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/main Packages                            
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/restricted Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/main Sources       
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/restricted Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/universe Packages  
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/universe Sources   
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/multiverse Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/multiverse Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates/main Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates/restricted Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates/main Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates/restricted Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates/universe Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates/universe Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates/multiverse Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-updates/multiverse Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security/main Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security/restricted Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security/main Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security/restricted Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security/universe Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security/universe Sources
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security/multiverse Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid-security/multiverse Sources
Fetched 4,013B in 37s (106B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

"Please comment"

---

