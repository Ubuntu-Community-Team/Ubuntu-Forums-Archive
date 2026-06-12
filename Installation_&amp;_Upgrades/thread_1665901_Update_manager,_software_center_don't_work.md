---
title: "Update manager, software center don't work"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by dcroxton on 2011-01-12
Update manager and software center both run, but when I click on "install," they both just sit there and don't respond.  If I run software center from a command line, I get the error "WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed."  (There are no updates right now, so I can't get an error from the update manager.)  Apparently they aren't invoking gksudo or whatever it is they need to elevate privileges.

I can get around this by running them as root, but it is kind of annoying.  I'm really surprised that no one else has had this problem, but I've searched it a number of times and I can't find any indication of someone having the same symptoms.

Sincerely,
Derek

---

### Post by sikander3786 on 2011-01-13
Please post the _complete_ output of these commands.

Applications > Accessories > Terminal:

```
sudo apt-get update
```

```
sudo apt-get install -f
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by dcroxton on 2011-01-13
sudo apt-get update
```
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Hit http://linux.dropbox.com maverick Release                                  
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Get:2 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/ maverick/main Translation-en_US
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ maverick/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/slicer/ppa/ubuntu/ maverick/main Translation-en   
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://ppa.launchpad.net/slicer/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/spring/ppa/ubuntu/ maverick/main Translation-en   
Hit http://archive.canonical.com maverick Release                              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Get:3 http://us.archive.ubuntu.com maverick-updates Release.gpg [198B]         
Get:4 http://security.ubuntu.com maverick-security Release [27.2kB]            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://ppa.launchpad.net/spring/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://us.archive.ubuntu.com maverick-backports Release.gpg                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Hit http://archive.canonical.com maverick/partner i386 Packages                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Get:5 http://security.ubuntu.com maverick-security/main Sources [20.1kB]       
Get:6 http://us.archive.ubuntu.com maverick-updates Release [31.4kB]           
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Get:7 http://security.ubuntu.com maverick-security/restricted Sources [14B]    
Get:8 http://security.ubuntu.com maverick-security/universe Sources [8,221B]   
Get:9 http://security.ubuntu.com maverick-security/multiverse Sources [649B]   
Get:10 http://security.ubuntu.com maverick-security/main i386 Packages [66.3kB]
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://us.archive.ubuntu.com maverick-backports Release                    
Hit http://us.archive.ubuntu.com maverick/main Sources                         
Hit http://us.archive.ubuntu.com maverick/restricted Sources                   
Hit http://us.archive.ubuntu.com maverick/universe Sources                     
Hit http://us.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://us.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages             
Ign http://ppa.launchpad.net maverick/main Sources                             
Get:11 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:12 http://security.ubuntu.com maverick-security/universe i386 Packages [33.4kB]
Get:13 http://us.archive.ubuntu.com maverick-updates/main Sources [71.8kB]     
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Get:14 http://security.ubuntu.com maverick-security/multiverse i386 Packages [1,655B]
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Get:15 http://us.archive.ubuntu.com maverick-updates/restricted Sources [14B]
Get:16 http://us.archive.ubuntu.com maverick-updates/universe Sources [23.7kB]
Get:17 http://us.archive.ubuntu.com maverick-updates/multiverse Sources [1,068B]
Get:18 http://us.archive.ubuntu.com maverick-updates/main i386 Packages [196kB]
Get:19 http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:20 http://us.archive.ubuntu.com maverick-updates/universe i386 Packages [77.3kB]
Get:21 http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages [2,522B]
Hit http://us.archive.ubuntu.com maverick-backports/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/multiverse i386 Packages
Fetched 562kB in 1s (323kB/s)
W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

sudo apt-get install -f:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwildmidi0 libzbar0 libflite1 libopenspc0 libfftw3-3 libgme0 libcdaudio1
  libmimic0 librtmp0 libofa0 libmms0 libiptcdata0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

```

---

### Post by sikander3786 on 2011-01-15
There doesn't seem to be any problem with that output except that 2 of the Launchpad PPA's servers are down thus giving a 404 Error.

Go to Software Center > Edit > Software Sources > Other Software Tab and disable the offensive PPAs and try using Software Center again.

---

### Post by aimless_e on 2011-07-11
The problem isn't his repo setup its with the policy kit

softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.225'}): org.debian.apt.install-or-remove-packages

Happens with both update manager and software center when not in gnome, kde, or xfce

I too am looking for the answer to this issue. I'm still coming up dry.

---

