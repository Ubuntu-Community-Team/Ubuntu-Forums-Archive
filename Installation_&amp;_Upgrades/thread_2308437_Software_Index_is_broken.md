---
title: "Software Index is broken"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by webber3 on 2016-01-03
Hello, i am having a problem updating the software.. i searched for the problem and it looks like beacuse of missing linux headers.. tried a few things to install them and found out i dont have enough space to install them as i am running linux on a usb stick..  i wanted to remove some headers from /usr/src but not sure which ones to remove..  Pls help me out with this problem.. Greatly appreciate the help.

Output from my cmds

```
[I]:~$ sudo dpkg --configure -a

dpkg: dependency problems prevent configuration of linux-headers-3.16.0-55-generic:
 linux-headers-3.16.0-55-generic depends on linux-headers-3.16.0-55; however:
  Package linux-headers-3.16.0-55 is not installed.

dpkg: error processing package linux-headers-3.16.0-55-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-lts-utopic:
 linux-headers-generic-lts-utopic depends on linux-headers-3.16.0-55-generic; however:
  Package linux-headers-3.16.0-55-generic is not configured yet.

dpkg: error processing package linux-headers-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-utopic:
 linux-generic-lts-utopic depends on linux-headers-generic-lts-utopic (= 3.16.0.55.46); however:
  Package linux-headers-generic-lts-utopic is not configured yet.

dpkg: error processing package linux-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-3.16.0-55-generic
 linux-headers-generic-lts-utopic
 linux-generic-lts-utopic

:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.16.0-55
The following NEW packages will be installed:
  linux-headers-3.16.0-55
0 upgraded, 1 newly installed, 0 to remove and 54 not upgraded.
3 not fully installed or removed.
Need to get 9,058 kB of archives.
After this operation, 64.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.16.0-55 all 3.16.0-55.74~14.04.1 [9,058 kB]
Fetched 9,058 kB in 5s (1,620 kB/s)                  
(Reading database ... 507110 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.16.0-55_3.16.0-55.74~14.04.1_all.deb ...
Unpacking linux-headers-3.16.0-55 (3.16.0-55.74~14.04.1) ...
No apport report written because the error message indicates a disk full error
      dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.16.0-55_3.16.0-55.74~14.04.1_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.16.0-55/drivers/staging/media/Kconfig.dpkg-new' (while processing `./usr/src/linux-headers-3.16.0-55/drivers/staging/media/Kconfig'): No space left on device
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.16.0-55_3.16.0-55.74~14.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

:~$ sudo apt-get update && sudo apt-get dist-upgrade
 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [64.4 kB]           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [64.4 kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [101 kB]         
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [246 kB]        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5,359 B] 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [145 kB]    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B]  
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [31.9 kB]    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,161 B] 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [654 kB] 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,357 B] 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [374 kB]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [122 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [334 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.1 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [340 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [4,955 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [218 kB] 
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [2,437 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3,206 B]
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [71.1 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,832 B]
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:26 [http://deb.opera.com](http://deb.opera.com) stable InRelease [2,590 B]                         
Err [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
  
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [174 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 3,021 kB in 44s (67.7 kB/s)                                            
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/InRelease](http://deb.opera.com/opera/dists/stable/InRelease)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-3.16.0-55-generic : Depends: linux-headers-3.16.0-55 but it is not installed
E: Unmet dependencies. Try using -f.


:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        15G   13G  575M  96% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           390M  1.2M  388M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
none            100M   20K  100M   1% /run/user

:~$ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/sdb1      960992 960330    662  100% /
none           215920      2 215918    1% /sys/fs/cgroup
udev           211042    534 210508    1% /dev
tmpfs          215920    547 215373    1% /run
none           215920      3 215917    1% /run/lock
none           215920      1 215919    1% /run/shm
none           215920     27 215893    1% /run/user

```
[/I]Cheers[/SIZE]

---

### Post by matt_symes on 2016-01-03
Hi

```
/dev/sdb1 960992 960330 662 100% /
```

Your root partition is full up. You need to uninstall some software to make room.

Let's see what old kernels and headersyou have.

```
dpkg -l | grep linux-image
```

```
dpkg -l | grep linux-headers
```

Kind regards

---

### Post by webber3 on 2016-01-03
Thanks for the quick reply. Here is the info

```
:~$ dpkg -l | grep linux-image
rc  linux-image-3.16.0-30-generic               3.16.0-30.40~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-31-generic               3.16.0-31.43~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-33-generic               3.16.0-33.44~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-34-generic               3.16.0-34.47~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-36-generic               3.16.0-36.48~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-37-generic               3.16.0-37.51~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-38-generic               3.16.0-38.52~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-45-generic               3.16.0-45.60~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-46-generic               3.16.0-46.62~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-48-generic               3.16.0-48.64~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-49-generic               3.16.0-49.65~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-50-generic               3.16.0-50.67~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-51-generic               3.16.0-51.69~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-52-generic               3.16.0-52.71~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-53-generic               3.16.0-53.72~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-55-generic               3.16.0-55.74~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
rc  linux-image-extra-3.16.0-30-generic         3.16.0-30.40~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-31-generic         3.16.0-31.43~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-33-generic         3.16.0-33.44~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-34-generic         3.16.0-34.47~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-36-generic         3.16.0-36.48~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-37-generic         3.16.0-37.51~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-38-generic         3.16.0-38.52~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-45-generic         3.16.0-45.60~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-46-generic         3.16.0-46.62~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-48-generic         3.16.0-48.64~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-49-generic         3.16.0-49.65~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-50-generic         3.16.0-50.67~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-51-generic         3.16.0-51.69~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-52-generic         3.16.0-52.71~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-53-generic         3.16.0-53.72~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-55-generic         3.16.0-55.74~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-utopic              3.16.0.55.46                            i386         Generic Linux kernel image

:~$ dpkg -l | grep linux-headers
ii  linux-headers-3.16.0-31                     3.16.0-31.43~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-31-generic             3.16.0-31.43~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-33                     3.16.0-33.44~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-33-generic             3.16.0-33.44~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-34                     3.16.0-34.47~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-34-generic             3.16.0-34.47~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-36                     3.16.0-36.48~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-36-generic             3.16.0-36.48~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-37                     3.16.0-37.51~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-37-generic             3.16.0-37.51~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-38                     3.16.0-38.52~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-38-generic             3.16.0-38.52~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-45                     3.16.0-45.60~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-45-generic             3.16.0-45.60~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-46                     3.16.0-46.62~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-46-generic             3.16.0-46.62~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-48                     3.16.0-48.64~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-48-generic             3.16.0-48.64~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-49                     3.16.0-49.65~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-49-generic             3.16.0-49.65~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-50                     3.16.0-50.67~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-50-generic             3.16.0-50.67~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-51                     3.16.0-51.69~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-51-generic             3.16.0-51.69~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-52                     3.16.0-52.71~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-52-generic             3.16.0-52.71~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-53                     3.16.0-53.72~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-53-generic             3.16.0-53.72~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
iU  linux-headers-3.16.0-55-generic             3.16.0-55.74~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
iU  linux-headers-generic-lts-utopic            3.16.0.55.46                            i386         Generic Linux kernel headers



```

---

### Post by matt_symes on 2016-01-03
Hi

Copy and paste this into the terminal.

```
sudo dpkg -P linux-image{,-extra}-3.16.0-{30,31,33,34,36,37,38,45,46,48,49,50,51}-generic
```

```
sudo apt-get -f install
```

Kind regards

---

### Post by webber3 on 2016-01-03
That fixed it !!!!! Thanks a ton  matt_symes  This problem has been bugging me for about a month now.

---

### Post by webber3 on 2016-01-23
> **webber3 said:**
> Hello, i am having a problem updating the software.. i searched for the problem and it looks like beacuse of missing linux headers.. tried a few things to install them and found out i dont have enough space to install them as i am running linux on a usb stick..  i wanted to remove some headers from /usr/src but not sure which ones to remove..  Pls help me out with this problem.. Greatly appreciate the help.

Output from my cmds

```
[I]:~$ sudo dpkg --configure -a

dpkg: dependency problems prevent configuration of linux-headers-3.16.0-55-generic:
 linux-headers-3.16.0-55-generic depends on linux-headers-3.16.0-55; however:
  Package linux-headers-3.16.0-55 is not installed.

dpkg: error processing package linux-headers-3.16.0-55-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-lts-utopic:
 linux-headers-generic-lts-utopic depends on linux-headers-3.16.0-55-generic; however:
  Package linux-headers-3.16.0-55-generic is not configured yet.

dpkg: error processing package linux-headers-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-utopic:
 linux-generic-lts-utopic depends on linux-headers-generic-lts-utopic (= 3.16.0.55.46); however:
  Package linux-headers-generic-lts-utopic is not configured yet.

dpkg: error processing package linux-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-3.16.0-55-generic
 linux-headers-generic-lts-utopic
 linux-generic-lts-utopic

:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.16.0-55
The following NEW packages will be installed:
  linux-headers-3.16.0-55
0 upgraded, 1 newly installed, 0 to remove and 54 not upgraded.
3 not fully installed or removed.
Need to get 9,058 kB of archives.
After this operation, 64.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.16.0-55 all 3.16.0-55.74~14.04.1 [9,058 kB]
Fetched 9,058 kB in 5s (1,620 kB/s)                  
(Reading database ... 507110 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.16.0-55_3.16.0-55.74~14.04.1_all.deb ...
Unpacking linux-headers-3.16.0-55 (3.16.0-55.74~14.04.1) ...
No apport report written because the error message indicates a disk full error
      dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.16.0-55_3.16.0-55.74~14.04.1_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.16.0-55/drivers/staging/media/Kconfig.dpkg-new' (while processing `./usr/src/linux-headers-3.16.0-55/drivers/staging/media/Kconfig'): No space left on device
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.16.0-55_3.16.0-55.74~14.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

:~$ sudo apt-get update && sudo apt-get dist-upgrade
 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [64.4 kB]           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [64.4 kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [101 kB]         
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [246 kB]        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5,359 B] 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [145 kB]    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B]  
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [31.9 kB]    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,161 B] 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [654 kB] 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,357 B] 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [374 kB]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [122 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [334 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.1 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [340 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [4,955 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [218 kB] 
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [2,437 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3,206 B]
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [71.1 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,832 B]
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:26 [http://deb.opera.com](http://deb.opera.com) stable InRelease [2,590 B]                         
Err [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
  
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [174 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 3,021 kB in 44s (67.7 kB/s)                                            
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/InRelease](http://deb.opera.com/opera/dists/stable/InRelease)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-3.16.0-55-generic : Depends: linux-headers-3.16.0-55 but it is not installed
E: Unmet dependencies. Try using -f.


:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        15G   13G  575M  96% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           390M  1.2M  388M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
none            100M   20K  100M   1% /run/user

:~$ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/sdb1      960992 960330    662  100% /
none           215920      2 215918    1% /sys/fs/cgroup
udev           211042    534 210508    1% /dev
tmpfs          215920    547 215373    1% /run
none           215920      3 215917    1% /run/lock
none           215920      1 215919    1% /run/shm
none           215920     27 215893    1% /run/user
[/I]
```Cheers[/SIZE]

> **matt_symes said:**
> Hi

```
/dev/sdb1 960992 960330 662 100% /
```

Your root partition is full up. You need to uninstall some software to make room.

Let's see what old kernels and headersyou have.

```
dpkg -l | grep linux-image
```

```
dpkg -l | grep linux-headers
```

Kind regards


[SIZE=3]**Same problem again.. the root partition got full..**[/SIZE]


```
:~$ dpkg -l | grep linux-image
ii  linux-image-3.16.0-52-generic               3.16.0-52.71~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-53-generic               3.16.0-53.72~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-55-generic               3.16.0-55.74~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-57-generic               3.16.0-57.77~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-59-generic               3.16.0-59.79~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-52-generic         3.16.0-52.71~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-53-generic         3.16.0-53.72~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-55-generic         3.16.0-55.74~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-57-generic         3.16.0-57.77~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-59-generic         3.16.0-59.79~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-utopic              3.16.0.59.50                            i386         Generic Linux kernel image

$ dpkg -l | grep linux-headers
ii  linux-headers-3.16.0-31                     3.16.0-31.43~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-31-generic             3.16.0-31.43~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-33                     3.16.0-33.44~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-33-generic             3.16.0-33.44~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-34                     3.16.0-34.47~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-34-generic             3.16.0-34.47~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-36                     3.16.0-36.48~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-36-generic             3.16.0-36.48~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-37                     3.16.0-37.51~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-37-generic             3.16.0-37.51~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-38                     3.16.0-38.52~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-38-generic             3.16.0-38.52~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-45                     3.16.0-45.60~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-45-generic             3.16.0-45.60~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-46                     3.16.0-46.62~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-46-generic             3.16.0-46.62~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-48                     3.16.0-48.64~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-48-generic             3.16.0-48.64~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-49                     3.16.0-49.65~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-49-generic             3.16.0-49.65~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-50                     3.16.0-50.67~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-50-generic             3.16.0-50.67~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-51                     3.16.0-51.69~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-51-generic             3.16.0-51.69~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-52                     3.16.0-52.71~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-52-generic             3.16.0-52.71~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-53                     3.16.0-53.72~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-53-generic             3.16.0-53.72~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-55                     3.16.0-55.74~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-55-generic             3.16.0-55.74~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-57                     3.16.0-57.77~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-57-generic             3.16.0-57.77~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
iU  linux-headers-3.16.0-59-generic             3.16.0-59.79~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
iU  linux-headers-generic-lts-utopic            3.16.0.59.50                            i386         Generic Linux kernel headers



sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-headers-3.16.0-59-generic:
 linux-headers-3.16.0-59-generic depends on linux-headers-3.16.0-59; however:
  Package linux-headers-3.16.0-59 is not installed.

dpkg: error processing package linux-headers-3.16.0-59-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-lts-utopic:
 linux-headers-generic-lts-utopic depends on linux-headers-3.16.0-59-generic; however:
  Package linux-headers-3.16.0-59-generic is not configured yet.

dpkg: error processing package linux-headers-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-utopic:
 linux-generic-lts-utopic depends on linux-headers-generic-lts-utopic (= 3.16.0.59.50); however:
  Package linux-headers-generic-lts-utopic is not configured yet.

dpkg: error processing package linux-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-3.16.0-59-generic
 linux-headers-generic-lts-utopic
 linux-generic-lts-utopic

```


Can someone please guide which files to purge ??

---

### Post by matt_symes on 2016-01-23
Hi

Please post the output of these commands.

```

df -h
df -i
```

Kind regards

---

### Post by webber3 on 2016-01-24
```
:~$ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
udev           211042    530 210512    1% /dev
tmpfs          215920    530 215390    1% /run
/dev/sdb1      960992 956126   4866  100% /
none           215920      2 215918    1% /sys/fs/cgroup
none           215920      3 215917    1% /run/lock
none           215920      1 215919    1% /run/shm
none           215920     16 215904    1% /run/user
:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           390M  1.2M  388M   1% /run
/dev/sdb1        15G   11G  2.7G  81% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
none            100M   16K  100M   1% /run/user
```

---

### Post by matt_symes on 2016-01-24
Hi

> **webber3 said:**
> ```
:~$ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
[B]/dev/sdb1      960992 956126   4866  100% /
[/B]:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
mpfs           390M  1.2M  388M   1% /run
**/dev/sdb1        15G   11G  2.7G  81% /**

```

You are out of inodes on your root partition.

To free some up, let's remove the old kernel headers you're not going to need.

Copy and paste these commands into the terminal.

```
sudo dpkg -P linux-headers-3.16.0-{31,33,34,36,37,38,45,46,48,49}{,-generic}
```

```
sudo apt-get -f install
```

Post back any error and then post the output of
```

df -i
df -h
```

To note: you only have 2.7G on your root partition.

Kind regards

---

### Post by webber3 on 2016-01-24
Hi Matt_symes,

Thanks a lot. That did free up a lot of nodes and fixed the problem.

When i keep installing the new firmwares, what should i do to remove the old ones which might not be necessary? like the kernels we are removing now.

```
sudo dpkg -P linux-headers-3.16.0-{31,33,34,36,37,38,45,46,48,49}{,-generic}

(Reading database ... 503799 files and directories currently installed.)
Removing linux-headers-3.16.0-31-generic (3.16.0-31.43~14.04.1) ...
Removing linux-headers-3.16.0-33-generic (3.16.0-33.44~14.04.1) ...
Removing linux-headers-3.16.0-34-generic (3.16.0-34.47~14.04.1) ...
Removing linux-headers-3.16.0-36-generic (3.16.0-36.48~14.04.1) ...
Removing linux-headers-3.16.0-37-generic (3.16.0-37.51~14.04.1) ...
Removing linux-headers-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
Removing linux-headers-3.16.0-45-generic (3.16.0-45.60~14.04.1) ...
Removing linux-headers-3.16.0-46-generic (3.16.0-46.62~14.04.1) ...
Removing linux-headers-3.16.0-48-generic (3.16.0-48.64~14.04.1) ...
Removing linux-headers-3.16.0-49-generic (3.16.0-49.65~14.04.1) ...
Removing linux-headers-3.16.0-31 (3.16.0-31.43~14.04.1) ...
Removing linux-headers-3.16.0-33 (3.16.0-33.44~14.04.1) ...
Removing linux-headers-3.16.0-34 (3.16.0-34.47~14.04.1) ...
Removing linux-headers-3.16.0-36 (3.16.0-36.48~14.04.1) ...
Removing linux-headers-3.16.0-37 (3.16.0-37.51~14.04.1) ...
Removing linux-headers-3.16.0-38 (3.16.0-38.52~14.04.1) ...
Removing linux-headers-3.16.0-45 (3.16.0-45.60~14.04.1) ...
Removing linux-headers-3.16.0-46 (3.16.0-46.62~14.04.1) ...
Removing linux-headers-3.16.0-48 (3.16.0-48.64~14.04.1) ...
Removing linux-headers-3.16.0-49 (3.16.0-49.65~14.04.1) ...
:~$ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
udev           211042    530 210512    1% /dev
tmpfs          215920    539 215381    1% /run
/dev/sdb1      960992 711226 249766   75% /
none           215920      2 215918    1% /sys/fs/cgroup
none           215920      3 215917    1% /run/lock
none           215920      1 215919    1% /run/shm
none           215920     16 215904    1% /run/user

:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           390M  1.2M  388M   1% /run
/dev/sdb1        15G  9.9G  3.8G  73% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
none            100M   16K  100M   1% /run/user

:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.16.0-59
The following NEW packages will be installed:
  linux-headers-3.16.0-59
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
3 not fully installed or removed.
Need to get 9,075 kB of archives.
After this operation, 64.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.16.0-59 all 3.16.0-59.79~14.04.1 [9,075 kB]
Fetched 9,075 kB in 15s (585 kB/s)                                             
(Reading database ... 258923 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.16.0-59_3.16.0-59.79~14.04.1_all.deb ...
Unpacking linux-headers-3.16.0-59 (3.16.0-59.79~14.04.1) ...
Setting up linux-headers-3.16.0-59 (3.16.0-59.79~14.04.1) ...
Setting up linux-headers-3.16.0-59-generic (3.16.0-59.79~14.04.1) ...
Setting up linux-headers-generic-lts-utopic (3.16.0.59.50) ...
Setting up linux-generic-lts-utopic (3.16.0.59.50) ...


:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           390M  1.2M  388M   1% /run
/dev/sdb1        15G   10G  3.6G  74% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
none            100M   16K  100M   1% /run/user
:~$ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
udev           211042    530 210512    1% /dev
tmpfs          215920    542 215378    1% /run
/dev/sdb1      960992 726843 234149   76% /
none           215920      2 215918    1% /sys/fs/cgroup
none           215920      3 215917    1% /run/lock
none           215920      1 215919    1% /run/shm
none           215920     16 215904    1% /run/user
```



And what is the purpose of 
"sudo apt-get autoremove"

Should i run autoremove more often ?

---

### Post by matt_symes on 2016-01-24
Hi

> 
And what is the purpose of
"sudo apt-get autoremove"

Should i run autoremove more often ? 

It'll remove packages that have been installed for other packages, but are now no longer required.

Your kernel headers were such packages but the *autoremove* command will not run if the partition is too full (as you have seen :)) I'm not sure of the state of autoremove at the moment though, as i tend to do most things manually.

You should run it often or enable *autoremove* automatically, so the package manager will run it for you.

Kind regards

---

