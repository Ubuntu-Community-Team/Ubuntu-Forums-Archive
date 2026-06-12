---
title: "Cannot install any software"
date: 2012-03-29
forum: Installation &amp; Upgrades
---

### Post by stbb24 on 2012-03-29
Hello everyone!!!
so i tried updating everything in the update manager and everything seem to be fine while i was updating. after the update i simply rebooted my computer. after that i tried installing other softwares that i need like wine, geany, and vlc but i couldn't install any of them.

here's what i get when installing wine:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine1.2: Depends: libmpg123-0 (>= 1.6.2) but it is not installable
           Recommends: ttf-droid but it is not installable
           Recommends: ttf-umefont but it is not installable
E: Broken packages

here's what i get when installing vlc using ubuntu software center:
Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

here's what i get when installing geany:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package geany

i really don't know what to do and i tried using ubuntu 10.04 before and installed these softwares perfectly fine.

any help would be appreciated.thanks in advance :)

---

### Post by cortman on 2012-03-29
First, run

```
sudo apt-get update
```

And post the full results here, contained within code tags. You can get the code tags by clicking the "#" button on the reply toolbar.

---

### Post by Bucky Ball on 2012-03-29
What release are you using?

Also, as suggested, do 'sudo apt-get update' and then:

```
sudo apt-get upgrade
```

This will upgrade installed packages/apps, not the release.

---

### Post by stbb24 on 2012-03-29
> **cortman said:**
> First, run

```
sudo apt-get update
```And post the full results here, contained within code tags. You can get the code tags by clicking the "#" button on the reply toolbar.

so here's what happened after trying sudo apt-get update

```
Hit http://archive.ubuntu.com lucid Release.gpg                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US             
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US       
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US       
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:1 http://archive.ubuntu.com lucid-updates Release.gpg [198B]               
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release 
Hit http://archive.canonical.com lucid/partner Packages
Hit http://archive.canonical.com lucid/partner Sources
Hit http://archive.ubuntu.com lucid-security Release.gpg                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid Release                                    
Hit http://archive.ubuntu.com lucid-updates Release                            
Hit http://archive.ubuntu.com lucid-security Release                           
Hit http://archive.ubuntu.com lucid/main Packages                              
Hit http://archive.ubuntu.com lucid/restricted Packages                        
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://archive.ubuntu.com lucid/restricted Sources                         
Hit http://archive.ubuntu.com lucid/universe Packages                          
Hit http://archive.ubuntu.com lucid/universe Sources                           
Hit http://archive.ubuntu.com lucid/multiverse Packages                        
Hit http://archive.ubuntu.com lucid/multiverse Sources                         
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Fetched 198B in 31s (6B/s)
Reading package lists... Done
 
```

---

### Post by Bucky Ball on 2012-03-29
Now 

```
sudo apt-get upgrade 
```

...

---

