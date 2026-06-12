---
title: "update jammed"
date: 2014-03-12
forum: Installation &amp; Upgrades
---

### Post by tiomoco on 2014-03-12
Hi.! Ubuntu 12.04 64 bt on Dell Inspiron 3421 here. Update manager claims there are incompatible packets that don't let some security updates be installed. One that can't is "Firmware for Linux kernel". How can i learn which packets to uninstall..? Thanks.
Tiomoco

---

### Post by Frogs Hair on 2014-03-12
Post the output of the following  command in code tags and close the update manager before running the command in the terminal. To use code tags copy and paste the output in the reply box and use the # symbol from the tools while the text is highlighted. 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tiomoco on 2014-03-13
```
demiano@demiano-Inspiron-3421:~$ sudo apt-get update && sudo apt-get upgrade 
[sudo] password for demiano: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]              
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release                        
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public amd64 Packages       
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public i386 Packages        
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public TranslationIndex     
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [452 kB]          
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [98.9 kB]       
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,789 B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [369 kB] 
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [8,028 B]  
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [105 kB]     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [8,474 B]  
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [758 kB]  
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public Translation-en_US    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell/public Translation-en       
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [12.2 kB] 
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [237 kB] 
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B] 
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [91.2 kB] 
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [14.5 kB] 
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [782 kB]   
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,446 B] 
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [396 kB] 
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [12.2 kB] 
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [242 kB] 
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.7 kB] 
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B] 
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [95.8 kB] 
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B] 
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B] 
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B] 
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main amd64 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse amd64 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex          
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,646 B] 
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B] 
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B] 
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B] 
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Fetched 3,857 kB in 8s (443 kB/s)                                              
Reading package lists... Done 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages will be upgraded: 
  linux-firmware sudo 
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 299 kB/26.1 MB of archives. 
After this operation, 5,498 kB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main sudo amd64 1.8.3p1-1ubuntu3.6 [299 kB] 
Fetched 299 kB in 1s (162 kB/s) 
(Reading database ... 301832 files and directories currently installed.) 
Preparing to replace sudo 1.8.3p1-1ubuntu3.4 (using .../sudo_1.8.3p1-1ubuntu3.6_amd64.deb) ... 
Unpacking replacement sudo ... 
Preparing to replace linux-firmware 1.79 (using .../linux-firmware_1.79.10_all.deb) ... 
Unpacking replacement linux-firmware ... 
dpkg: error processing /var/cache/apt/archives/linux-firmware_1.79.10_all.deb (--unpack): 
 trying to overwrite '/lib/firmware/ar3k/ramps_0x31010000_40.dfu', which is also in package bt-dw1705-firmware 0.1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for man-db ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-firmware_1.79.10_all.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
demiano@demiano-Inspiron-3421:~$
```

---

### Post by matt_symes on 2014-03-13
Hi

Open a terminal and type

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-firmware_1.79.10_all.deb
```

This will overwrite the new firmware over the old one.

This should be alright and can be reverted if it causes any issues.

Kind regards

---

### Post by tiomoco on 2014-03-14
Thanks Matt Symes..! But i'll try that medicine after i've safely backed my stuff :o)

---

### Post by matt_symes on 2014-03-14
Hi

You should be backing up regularly as a matter of course :)

Kind regards

---

### Post by tiomoco on 2014-03-14
Did the OVERRIDE trick and got this: demiano@demiano-Inspiron-3421:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-firmware_1.79.10_all.deb 
[sudo] password for demiano: 
(Reading database ... 301832 files and directories currently installed.) 
Preparing to replace linux-firmware 1.79 (using .../linux-firmware_1.79.10_all.deb) ... 
Unpacking replacement linux-firmware ... 
dpkg: warning: overriding problem because --force enabled: 
 trying to overwrite '/lib/firmware/ar3k/ramps_0x31010000_40.dfu', which is also in package bt-dw1705-firmware 0.1 
dpkg: warning: overriding problem because --force enabled: 
 trying to overwrite '/lib/firmware/ar3k/AthrBT_0x31010000.dfu', which is also in package bt-dw1705-firmware 0.1 
Setting up linux-firmware (1.79.10) ... 
demiano@demiano-Inspiron-3421:~$

HOWEVER, Synaptics claims now that it's the 1.79.10 firmware that is currently installed. We shall see how it goes. Thanks. Have a swell weekend Matt Symes..!

---

### Post by matt_symes on 2014-03-15
Hi

It should be alright to install the new version of the Linux Firmware.

What the original error message was telling you was that the same file (although potentially different versions of it) are in more than one package on your machine.

The package manager will not overwrite one with the other unless you explicitly tell it to and this was the error message you were getting when you tried to update the file from a different package than the one it was installed from.

The messages you posted in your last post are not errors but a warning reminding you of such.

If you do have any problems then it can easily be rolled back as it's just a set of files stored on your hard drive. 

Kind regards

---

### Post by tiomoco on 2014-03-20
Fait accompli..! The overwriting command worked fine. Proof are all these days i've running my little machine. Thanks for your kind advice guys..!!;)

---

