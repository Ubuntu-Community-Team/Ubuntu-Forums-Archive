---
title: "Package Install Dependency Error"
date: 2016-02-14
forum: Installation &amp; Upgrades
---

### Post by bryansimmons on 2016-02-14
Received the following errors when attempting to install libgl1-mesa-glx:

[COLOR=#0000ff]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.[/COLOR]

Seems the message originates with removal of dependency packages:

libcheese-gtk23 will be removed
libcheese7 will be removed
libclutter-1.0-0 will be removed
libclutter-gtk-1.0-0 will be removed
libcogl15 will be removed
libcogl-pango15 will be removed

Why would the install remove these packages if they are dependencies for the package being installed?

Complete list of install preview attached.

Ubuntu 14.04, 3.16.0-60-generic.

---

### Post by ian-weisser on 2016-02-14
> **bryansimmons said:**
> Why would the install remove these packages if they are dependencies for the package being installed?

Because you have introduced a *version conflict*. It's that 'impossible situation' the system was warning you about.

This usually happens to users who unwisely install wrong-version software from a PPA or other non-Ubuntu source.

Please show us the contents of your /etc/apt/sources.list file, and the contents of all files in the /etc/apt/sources.list.d/ directory

---

### Post by bryansimmons on 2016-02-15
Contents of /etc/apt/sources.list file and /etc/apt/sources.list.d directory attached.

---

### Post by ian-weisser on 2016-02-15
Please run the following commands and post the complete output here.
```
sudo apt update
sudo apt upgrade
```

Er, please cut-and-paste the output instead of attaching. Use [code] tags to contain the output.

---

### Post by bryansimmons on 2016-02-15
```

Results from sudo apt update:

Hit http://repo.steampowered.com precise InRelease
Hit http://repo.steampowered.com precise/steam Sources                         
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security InRelease                       
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/main Sources           
Get:2 http://us.archive.ubuntu.com trusty-updates/main Sources [258 kB]        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Get:3 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,342 B] 
Get:4 http://us.archive.ubuntu.com trusty-updates/universe Sources [150 kB]    
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://ppa.launchpad.net trusty Release.gpg                       
Get:5 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,547 B] 
Get:6 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [704 kB] 
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://ppa.launchpad.net trusty Release                                    
Get:7 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:8 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [337 kB]
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://ppa.launchpad.net trusty Release                                    
Get:9 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://ppa.launchpad.net trusty Release                                    
Get:10 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [682 kB] 
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [339 kB]
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Get:13 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.4 kB]
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources    
Hit http://ppa.launchpad.net trusty/main amd64 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages 
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://us.archive.ubuntu.com trusty Release                         
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources          
Hit http://us.archive.ubuntu.com trusty/multiverse Sources        
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages       
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages 
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages      
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com trusty/main Translation-en        
Ign http://ppa.launchpad.net trusty/main Translation-en_US         
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US

```
```

Results from sudo apt upgrade:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by ian-weisser on 2016-02-15
Good, your package manager is not broken.
Let's keep it that way.
You stopped and asked for support at exactly the right time. Good job!

Therefore, the version or source of libgl1-mesa-glx seems suspect. Let's look into that.
Please show us the output of:
```
apt-cache policy libgl1-mesa-glx
```

---

### Post by bryansimmons on 2016-02-15
Thank you for assisting.  Requested output "apt-cache policy libgl1-mesa-glx" is below.

  ```
Installed: (none)
  Candidate: 10.1.3-0ubuntu0.6
  Version table:
     10.1.3-0ubuntu0.6 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     10.1.0-4ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```

---

### Post by ian-weisser on 2016-02-15
Let's try disabling other sources, the most common cause of version conflicts.

1) Open System Settings --> Software and Updates --> Other Software tab
Uncheck all. Remember which ones were checked.
Close.

2) sudo apt update

3) sudo apt install libgl1-mesa-glx

If you get errors, paste them here.

If it works without errors, reopen Other Software and re-check those sources.

---

### Post by bryansimmons on 2016-02-15
```
sudo apt update
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://us.archive.ubuntu.com trusty-backports InRelease             
Hit http://security.ubuntu.com trusty-security InRelease               
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://security.ubuntu.com trusty-security/main Sources      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources  
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://security.ubuntu.com trusty-security/restricted Sources 
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe Sources     
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages 
Hit http://security.ubuntu.com trusty-security/multiverse Sources   
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/main amd64 Packages  
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages  
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en 
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages   
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en  
Hit http://us.archive.ubuntu.com trusty-backports/main Sources          
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages  
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en 
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en   
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://us.archive.ubuntu.com trusty Release   
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done

```
```
sudo apt install libgl1-mesa-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by ian-weisser on 2016-02-15
Well, we have cleared the decks and can get to work.

Let's look at some of those version conflicts in detail.

Please show us the output of
```
apt-cache policy libcogl15
apt-cache policy libclutter-gst-2.0-0
apt-cache policy gstreamer1.0-clutter
apt-cache policy libcogl-pango15
```

---

### Post by bryansimmons on 2016-02-15
```
apt-cache policy libcogl15
libcogl15:
  Installed: 1.16.2-1
  Candidate: 1.16.2-1
  Version table:
 *** 1.16.2-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```
```
apt-cache policy libclutter-gst-2.0-0
libclutter-gst-2.0-0:
  Installed: 2.0.8-1build1
  Candidate: 2.0.8-1build1
  Version table:
 *** 2.0.8-1build1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```
```
apt-cache policy gstreamer1.0-clutter
gstreamer1.0-clutter:
  Installed: 2.0.8-1build1
  Candidate: 2.0.8-1build1
  Version table:
 *** 2.0.8-1build1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```
```
apt-cache policy libcogl-pango15
libcogl-pango15:
  Installed: 1.16.2-1
  Candidate: 1.16.2-1
  Version table:
 *** 1.16.2-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by ian-weisser on 2016-02-15
The second-level dependencies look fine.

Last three to take a look at:
```
apt cache policy libcheese-gtk23
apt-cache policy libcheese7
apt-cache policy libclutter-1.0-0
```

---

### Post by bryansimmons on 2016-02-15
```
apt-cache policy libcheese-gtk23
libcheese-gtk23:
  Installed: 3.10.2-0ubuntu2
  Candidate: 3.10.2-0ubuntu2
  Version table:
 *** 3.10.2-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```
```
apt-cache policy libcheese7
libcheese7:
  Installed: 3.10.2-0ubuntu2
  Candidate: 3.10.2-0ubuntu2
  Version table:
 *** 3.10.2-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```
```
apt-cache policy libclutter-1.0-0
libclutter-1.0-0:
  Installed: 1.16.4-0ubuntu2
  Candidate: 1.16.4-0ubuntu2
  Version table:
 *** 1.16.4-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by ian-weisser on 2016-02-15
Everything looks right.
I'm honestly stumped as to where the package conflict is coming from. Something to do with cheese, but what? hmmm.....

Try installing again.
```
sudo apt install libgl1-mesa-glx
```

If it fails with the same error, then uninstall cheese and try again.
```
sudo apt-get remove cheese
sudo apt-get autoremove
sudo apt install libgl1-mesa-glx
sudo apt-get install cheese 
```

---

### Post by bryansimmons on 2016-02-15
Same error.
```
sudo apt install libgl1-mesa-glx
[sudo] password for bcs: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```
Removed/Installed Cheese.
```
sudo apt-get remove cheese
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cheese
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
After this operation, 417 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 202990 files and directories currently installed.)
Removing cheese (3.10.2-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
```
```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-video-effects
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
After this operation, 145 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 202981 files and directories currently installed.)
Removing gnome-video-effects (0.4.1-0ubuntu1) ...
```
```
sudo apt-get install cheese
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-video-effects
Suggested packages:
  gnome-video-effects-frei0r gnome-video-effects-extra
The following NEW packages will be installed:
  cheese gnome-video-effects
0 upgraded, 2 newly installed, 0 to remove and 8 not upgraded.
Need to get 84.0 kB of archives.
After this operation, 562 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main gnome-video-effects all 0.4.1-0ubuntu1 [35.4 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main cheese amd64 3.10.2-0ubuntu2 [48.6 kB]
Fetched 84.0 kB in 0s (222 kB/s) 
Selecting previously unselected package gnome-video-effects.
(Reading database ... 202958 files and directories currently installed.)
Preparing to unpack .../gnome-video-effects_0.4.1-0ubuntu1_all.deb ...
Unpacking gnome-video-effects (0.4.1-0ubuntu1) ...
Selecting previously unselected package cheese.
Preparing to unpack .../cheese_3.10.2-0ubuntu2_amd64.deb ...
Unpacking cheese (3.10.2-0ubuntu2) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up gnome-video-effects (0.4.1-0ubuntu1) ...
Setting up cheese (3.10.2-0ubuntu2) ...
```
Error persists.
```
sudo apt install libgl1-mesa-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```
Will "sudo apt install libgl1-mesa-glx" attempt to install the cheese libraries if these are not present?

---

### Post by ian-weisser on 2016-02-15
Let's see what happens if we completely uninstall the problem packages.
This is a simulation. Nothing will actually be removed.
We want to ensure nothing critical gets removed before we proceed.

Like before, the idea is to uninstall the conflicting packages completely, then install libgl1-mesa-glx, then see if those non-critical packages (like cheese) can be reinstalled.

Try:
```
sudo apt-get remove --simulate libclutter-1.0-0
```

---

### Post by ian-weisser on 2016-02-15
Let's see what happens if we completely uninstall the problem packages.
This is a simulation. Nothing will actually be removed.
We want to ensure nothing critical gets removed before we proceed.

Like before, the idea is to uninstall the conflicting packages completely, then install libgl1-mesa-glx, then see if those non-critical packages (like cheese) can be reinstalled.

Try:
```
sudo apt-get remove --simulate libclutter-1.0-0
```

---

### Post by bryansimmons on 2016-02-16
```
apt-get remove --simulate libclutter-1.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  accountsservice-ubuntu-schemas accountsservice-ubuntu-touch-schemas
  empathy-common folks-common gnome-control-center-data gnome-settings-daemon
  gnome-video-effects gsettings-ubuntu-touch-schemas gstreamer0.10-nice
  gstreamer0.10-plugins-good gstreamer0.10-x gstreamer1.0-nice
  indicator-network libavahi-gobject0 libfarstream-0.1-0 libfarstream-0.2-2
  libfolks-eds25 libfolks-telepathy25 libfolks25 libgoa-backend-1.0-1
  libgupnp-igd-1.0-4 libmeanwhile1 libmission-control-plugins0 libnice10
  libofono-qt1 libonline-accounts-client1 libpurple-bin libpurple0
  libqgsttools-p1 libqt5multimedia5-plugins libqt5multimediaquick-p5
  libqt5multimediawidgets5 libqt5systeminfo5 libsystemsettings1
  libtelepathy-farstream3 libtelepathy-logger3
  libubuntu-download-manager-client0 libubuntu-download-manager-common0
  libubuntu-download-manager-priv0 libubuntuoneauth-2.0-0 libzephyr4
  packagekit-tools python3-gnupg qtdeclarative5-folderlistmodel-plugin
  qtdeclarative5-qtmultimedia-plugin qtdeclarative5-systeminfo-plugin
  qtdeclarative5-ubuntuone1.0 signon-plugin-password suru-icon-theme
  system-image-common system-image-dbus telepathy-gabble telepathy-haze
  telepathy-logger telepathy-mission-control-5 telepathy-salut
  ubuntu-download-manager ubuntu-keyboard-data ubuntu-mobile-icons
  ubuntu-purchase-service ubuntu-touch-sounds ubuntuone-credentials-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor
  gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0 libboost-iostreams1.54.0
  libboost-program-options1.54.0 libboost-serialization1.54.0 libcapnp-0.4.0
  libclick-0.4-0 libcontent-hub0 libdbus-cpp2 libdee-qt5-3 libgflags2
  libgoogle-glog0 libhud-client2 libhybris-common1 libjsoncpp0
  liblttng-ust-ctl2 liblttng-ust0 libmediascanner-2.0-0 libmirclient7
  libmirclientplatform-mesa libmirplatform libmirplatformgraphics-mesa
  libmirprotobuf0 libmirserver18 libpgm-5.1-0 libprocess-cpp1 libqdjango-db0
  libqmenumodel0 libqt5xmlpatterns5 libubuntu-application-api-mirserver1
  libubuntu-location-service0 libubuntu-platform-hardware-api1 libunity-api0
  libunity-mir1 libunity-scopes1 libunwind8 libupstart-app-launch2 liburcu1
  libusermetricsoutput1 libzmq3 libzmqpp3 mediascanner2.0 python3-apparmor
  python3-apparmor-click python3-click python3-libapparmor qmenumodel-qml
  qtdeclarative5-dee-plugin qtdeclarative5-gsettings1.0
  qtdeclarative5-ubuntu-content0.1 qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-settings-components-assets
  qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-unity-notifications-plugin qtdeclarative5-xmllistmodel-plugin
  sqlite3 thumbnailer-service unity-plugin-scopes unity-scope-mediascanner2
  unity-scope-scopes unity8 unity8-private upstart-app-launch
  upstart-app-launch-tools usermetricsservice
Suggested packages:
  content-hub sqlite3-doc
Recommended packages:
  unity-scope-click
The following packages will be REMOVED:
  account-plugin-aim account-plugin-jabber account-plugin-salut
  account-plugin-yahoo cheese empathy gir1.2-totem-1.0 gnome-contacts
  gstreamer1.0-clutter indicator-bluetooth libcheese-gtk23 libcheese7
  libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libtotem0
  mcp-account-manager-uoa nautilus-sendto-empathy totem totem-mozilla
  totem-plugins ubuntu-desktop unity-control-center
  unity-control-center-signon webaccounts-extension-common xul-ext-webaccounts
The following NEW packages will be installed:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor
  gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0 libboost-iostreams1.54.0
  libboost-program-options1.54.0 libboost-serialization1.54.0 libcapnp-0.4.0
  libclick-0.4-0 libcontent-hub0 libdbus-cpp2 libdee-qt5-3 libgflags2
  libgoogle-glog0 libhud-client2 libhybris-common1 libjsoncpp0
  liblttng-ust-ctl2 liblttng-ust0 libmediascanner-2.0-0 libmirclient7
  libmirclientplatform-mesa libmirplatform libmirplatformgraphics-mesa
  libmirprotobuf0 libmirserver18 libpgm-5.1-0 libprocess-cpp1 libqdjango-db0
  libqmenumodel0 libqt5xmlpatterns5 libubuntu-application-api-mirserver1
  libubuntu-location-service0 libubuntu-platform-hardware-api1 libunity-api0
  libunity-mir1 libunity-scopes1 libunwind8 libupstart-app-launch2 liburcu1
  libusermetricsoutput1 libzmq3 libzmqpp3 mediascanner2.0 python3-apparmor
  python3-apparmor-click python3-click python3-libapparmor qmenumodel-qml
  qtdeclarative5-dee-plugin qtdeclarative5-gsettings1.0
  qtdeclarative5-ubuntu-content0.1 qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-settings-components-assets
  qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-unity-notifications-plugin qtdeclarative5-xmllistmodel-plugin
  sqlite3 thumbnailer-service unity-plugin-scopes unity-scope-mediascanner2
  unity-scope-scopes unity8 unity8-private upstart-app-launch
  upstart-app-launch-tools usermetricsservice
0 upgraded, 70 newly installed, 26 to remove and 9 not upgraded.
Remv account-plugin-aim [3.8.6-0ubuntu9.2]
Remv account-plugin-jabber [3.8.6-0ubuntu9.2]
Remv account-plugin-salut [3.8.6-0ubuntu9.2]
Remv account-plugin-yahoo [3.8.6-0ubuntu9.2]
Remv cheese [3.10.2-0ubuntu2]
Remv nautilus-sendto-empathy [3.8.6-0ubuntu9.2]
Remv mcp-account-manager-uoa [3.8.6-0ubuntu9.2]
Remv empathy [3.8.6-0ubuntu9.2]
Remv totem-plugins [3.10.1-1ubuntu4]
Remv gir1.2-totem-1.0 [3.10.1-1ubuntu4]
Remv gnome-contacts [3.8.3-1ubuntu1]
Remv totem-mozilla [3.10.1-1ubuntu4]
Remv totem [3.10.1-1ubuntu4]
Remv xul-ext-webaccounts [0.5-0ubuntu2.14.04.1]
Remv webaccounts-extension-common [0.5-0ubuntu2.14.04.1]
Remv unity-control-center-signon [0.1.7~+14.04.20140211.2-0ubuntu4]
Remv unity-control-center [14.04.3+14.04.20150916-0ubuntu1] [indicator-bluetooth:amd64 ubuntu-desktop:amd64 ]
Remv libcheese7 [3.10.2-0ubuntu2] [indicator-bluetooth:amd64 ubuntu-desktop:amd64 libcheese-gtk23:amd64 ]
Remv gstreamer1.0-clutter [2.0.8-1build1] [indicator-bluetooth:amd64 ubuntu-desktop:amd64 libcheese-gtk23:amd64 ]
Remv indicator-bluetooth [0.0.6+14.04.20140207-0ubuntu2] [ubuntu-desktop:amd64 libcheese-gtk23:amd64 ]
Remv libcheese-gtk23 [3.10.2-0ubuntu2] [ubuntu-desktop:amd64 ]
Remv libtotem0 [3.10.1-1ubuntu4] [ubuntu-desktop:amd64 ]
Remv libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2] [ubuntu-desktop:amd64 ]
Remv libclutter-gst-2.0-0 [2.0.8-1build1] [ubuntu-desktop:amd64 ]
Remv libclutter-1.0-0 [1.16.4-0ubuntu2] [ubuntu-desktop:amd64 ]
Remv ubuntu-desktop [1.325]
Inst gir1.2-gee-0.8 (0.10.5-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-json-1.0 (0.16.2-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libclick-0.4-0 (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-click-0.4 (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-click (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Inst click (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Inst libboost-iostreams1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libboost-program-options1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libboost-serialization1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst liburcu1 (0.7.12-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst liblttng-ust-ctl2 (2.4.0-4ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst liblttng-ust0 (2.4.0-4ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libupstart-app-launch2 (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libcontent-hub0 (0.0+14.04.20140415-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libdee-qt5-3 (3.3+14.04.20140317-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libgflags2 (2.0-1.1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libunwind8 (1.1-2.2ubuntu3 Ubuntu:14.04/trusty [amd64])
Inst libgoogle-glog0 (0.3.3-1 Ubuntu:14.04/trusty [amd64])
Inst libhud-client2 (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libmediascanner-2.0-0 (0.100+14.04.20140403-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirprotobuf0 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirclientplatform-mesa (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64]) []
Inst libmirclient7 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirplatform (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirplatformgraphics-mesa (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libmirserver18 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libpgm-5.1-0 (5.1.118-1~dfsg-0.1ubuntu3 Ubuntu:14.04/trusty [amd64])
Inst libprocess-cpp1 (1.0.0+14.04.20140328-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libqdjango-db0 (0.4.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libqmenumodel0 (0.2.7+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libqt5xmlpatterns5 (5.2.1-3 Ubuntu:14.04/trusty [amd64])
Inst libdbus-cpp2 (2.0.0+14.04.20140326-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libhybris-common1 (0.1.0+git20131207+e452e83-0ubuntu12 Ubuntu:14.04/trusty [amd64])
Inst libubuntu-platform-hardware-api1 (0.20+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libubuntu-location-service0 (0.0.2+14.04.20140307-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libubuntu-application-api-mirserver1 (0.20+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libunity-api0 (7.80.6+14.04.20140402-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libunity-mir1 (0.3+14.04.20140417-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libcapnp-0.4.0 (0.4.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libjsoncpp0 (0.6.0~rc2-3ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libzmq3 (4.0.4+dfsg-2 Ubuntu:14.04/trusty [amd64])
Inst libzmqpp3 (3.2.0-0ubuntu3 Ubuntu:14.04/trusty [amd64])
Inst libunity-scopes1 (0.4.2+14.04.20140408-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst sqlite3 (3.8.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Inst usermetricsservice (1.1.1+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libusermetricsoutput1 (1.1.1+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-dee-plugin (3.3+14.04.20140317-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-ubuntu-content0.1 (0.0+14.04.20140415-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-ubuntu-settings-components-assets (0.1+14.04.20140306-0ubuntu1 Ubuntu:14.04/trusty [all])
Inst qtdeclarative5-ubuntu-settings-components (0.1+14.04.20140306-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-ubuntu-thumbnailer0.1 (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst qtdeclarative5-unity-notifications-plugin (0.1.1+14.04.20140402-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-xmllistmodel-plugin (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Inst unity-plugin-scopes (0.4.0+14.04.20140408-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst qtdeclarative5-gsettings1.0 (0.1+14.04.20140408-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst apparmor-easyprof-ubuntu (1.1.16 Ubuntu:14.04/trusty [all])
Inst python3-libapparmor (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-apparmor (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64])
Inst apparmor-easyprof (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [all])
Inst python3-apparmor-click (0.2ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst click-apparmor (0.2ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst mediascanner2.0 (0.100+14.04.20140403-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst qmenumodel-qml (0.2.7+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst thumbnailer-service (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst unity-scope-mediascanner2 (0.2+14.04.20140404-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst unity-scope-scopes (0.1+14.04.20140404-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst unity8-private (7.85+14.04.20140416-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst unity8 (7.85+14.04.20140416-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst upstart-app-launch (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst upstart-app-launch-tools (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-gee-0.8 (0.10.5-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-json-1.0 (0.16.2-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libclick-0.4-0 (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-click-0.4 (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-click (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf click (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libboost-iostreams1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libboost-program-options1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libboost-serialization1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf liburcu1 (0.7.12-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf liblttng-ust-ctl2 (2.4.0-4ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf liblttng-ust0 (2.4.0-4ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libupstart-app-launch2 (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libcontent-hub0 (0.0+14.04.20140415-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libdee-qt5-3 (3.3+14.04.20140317-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libgflags2 (2.0-1.1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libunwind8 (1.1-2.2ubuntu3 Ubuntu:14.04/trusty [amd64])
Conf libgoogle-glog0 (0.3.3-1 Ubuntu:14.04/trusty [amd64])
Conf libhud-client2 (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libmediascanner-2.0-0 (0.100+14.04.20140403-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirprotobuf0 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirclientplatform-mesa (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirclient7 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirplatform (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirplatformgraphics-mesa (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libmirserver18 (0.1.8+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libpgm-5.1-0 (5.1.118-1~dfsg-0.1ubuntu3 Ubuntu:14.04/trusty [amd64])
Conf libprocess-cpp1 (1.0.0+14.04.20140328-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libqdjango-db0 (0.4.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libqmenumodel0 (0.2.7+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libqt5xmlpatterns5 (5.2.1-3 Ubuntu:14.04/trusty [amd64])
Conf libdbus-cpp2 (2.0.0+14.04.20140326-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libhybris-common1 (0.1.0+git20131207+e452e83-0ubuntu12 Ubuntu:14.04/trusty [amd64])
Conf libubuntu-platform-hardware-api1 (0.20+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libubuntu-location-service0 (0.0.2+14.04.20140307-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libubuntu-application-api-mirserver1 (0.20+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libunity-api0 (7.80.6+14.04.20140402-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libunity-mir1 (0.3+14.04.20140417-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libcapnp-0.4.0 (0.4.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libjsoncpp0 (0.6.0~rc2-3ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libzmq3 (4.0.4+dfsg-2 Ubuntu:14.04/trusty [amd64])
Conf libzmqpp3 (3.2.0-0ubuntu3 Ubuntu:14.04/trusty [amd64])
Conf libunity-scopes1 (0.4.2+14.04.20140408-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf sqlite3 (3.8.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf usermetricsservice (1.1.1+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libusermetricsoutput1 (1.1.1+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-dee-plugin (3.3+14.04.20140317-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-ubuntu-content0.1 (0.0+14.04.20140415-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-ubuntu-settings-components-assets (0.1+14.04.20140306-0ubuntu1 Ubuntu:14.04/trusty [all])
Conf qtdeclarative5-ubuntu-settings-components (0.1+14.04.20140306-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-ubuntu-thumbnailer0.1 (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf qtdeclarative5-unity-notifications-plugin (0.1.1+14.04.20140402-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-xmllistmodel-plugin (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-plugin-scopes (0.4.0+14.04.20140408-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf qtdeclarative5-gsettings1.0 (0.1+14.04.20140408-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf apparmor-easyprof-ubuntu (1.1.16 Ubuntu:14.04/trusty [all])
Conf python3-libapparmor (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-apparmor (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64])
Conf apparmor-easyprof (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [all])
Conf python3-apparmor-click (0.2ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf click-apparmor (0.2ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf mediascanner2.0 (0.100+14.04.20140403-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf qmenumodel-qml (0.2.7+14.04.20140305-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf thumbnailer-service (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-scope-mediascanner2 (0.2+14.04.20140404-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf unity-scope-scopes (0.1+14.04.20140404-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf unity8-private (7.85+14.04.20140416-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf unity8 (7.85+14.04.20140416-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf upstart-app-launch (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf upstart-app-launch-tools (0.3+14.04.20140411-0ubuntu1 Ubuntu:14.04/trusty [amd64])


```

---

### Post by ian-weisser on 2016-02-16
Fascinating.

I see a lot of Unity 8 packages there...are you trying to install a different Desktop Environment?
Or perhaps multiple environments?
Or clean up from past attempts?

Several directions we can go from here. Need to know your intent.

---

### Post by bryansimmons on 2016-02-16
This is a new install using Ubuntu default selections with no plans to deviate from the Unity desktop at this time.  OS was added to an existing machine (also Ubuntu) through the addition of an M.2 drive.  Install of new OS added dual boot capability.  Planning to remove the old OS when new install is fully configured and stable.

---

### Post by ian-weisser on 2016-02-16
This is clearly not a new install anymore.
A new install of Ubuntu (the ubuntu-desktop metapackage) includes libgl1-mesa-glx, and doesn't include unity8 and that boatload of other eligible-for-autoremove packages.
Steam, PPAs, unity8, and incompatible versions of Cheese are not part of the default install.

Since you seem to have no neccesary data on this system yet, my advice is to reinstall. Enough time wasted already.

It you want to try something fun-but-dangeous instead of reinstalling, then remove libclutter-1.0-0, autoremove, autoclean, install -f, then reinstall ubuntu-desktop.
Your system will either be completely fixed or horribly broken. If broken, then reinstall.

---

### Post by bryansimmons on 2016-02-16
Maybe at this point it should be considered a migration then since I am in the process of moving to the new environment.  Would be interesting to know what happened to libgl1-mesa-glx and where Unity8 and the other software originated since I do not recall installing any of these.

Willing to proceed with the experiment, any necessary data will be backed up to an alternate drive before starting.

In the event a reinstall is necessary, can the existing partition be reused and will the boot manager work as it does now, offering a choice of environments, or will this need to re-established manually?

Thanks again for all your patience and assistance.

---

### Post by bryansimmons on 2016-02-16
The fun-but-dangerous experiment appears to be successful.  After execution I was able to install the missing packages without error.  Application requesting the missing packages (Steam) is no longer attempting to install these.  libcheese-gtk23 and other associated cheese programs were not installed since there is no web cam on this system.  All seems well.

---

