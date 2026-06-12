---
title: "dpkg is stalling. I can't install anything because of this."
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by mahasmb on 2012-06-18
I can't update anything. I guess this happened because my computer was running really slowly and I interrupted an installation. 

Running "sudo dpkg --configure -a" just stalls. As you can see below, I've tried a few things but nothing's helping. I've spent hours already Googling and trying anything that looks like it might help.

Please help. I need to install a few things and this is making it impossible unless I start from scratch, which I really don't want to have to resort to.


```
**maha@maha-ubuntudesk:~$ sudo dpkg --configure -a**
[sudo] password for maha: 
Setting up linux-image-3.0.0-21-generic (3.0.0-21.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
^CFailed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-21-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-21-generic-pae (3.0.0-21.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-21-generic-pae /boot/vmlinuz-3.0.0-21-generic-pae
Error! Your kernel headers for kernel 3.0.0-21-generic-pae cannot be found.
Please install the linux-headers-3.0.0-21-generic-pae package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.0.0-21-generic-pae cannot be found.
Please install the linux-headers-3.0.0-21-generic-pae package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-21-generic-pae /boot/vmlinuz-3.0.0-21-generic-pae
update-initramfs: Generating /boot/initrd.img-3.0.0-21-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-21-generic-pae /boot/vmlinuz-3.0.0-21-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-21-generic-pae /boot/vmlinuz-3.0.0-21-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-21-generic-pae /boot/vmlinuz-3.0.0-21-generic-pae
^CFailed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-21-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.0.0-21-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-21-generic; however:
  Package linux-image-3.0.0-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.21.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.0.0-21-generic-pae; however:
  Package linux-image-3.0.0-21-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.0.0.21.25); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.0.0-21-generic
 linux-image-3.0.0-21-generic-pae
 linux-image-generic
 linux-generic
 linux-image-generic-pae
 linux-generic-pae
**maha@maha-ubuntudesk:~$ sudo dpkg --audit**
[sudo] password for maha: 
Another process has locked the database for writing, and might currently be
modifying it, some of the following problems might just be due to that.

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-image-generic-pae Generic Linux kernel image
 linux-headers-3.0.0-21-generic-pae Linux kernel headers for version 3.0.0 on x
 linux-image-generic  Generic Linux kernel image
 linux-generic-pae    Complete Generic Linux kernel
 linux-generic        Complete Generic Linux kernel

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-image-3.0.0-21-generic Linux kernel image for version 3.0.0 on x86/x86_6
 linux-image-3.0.0-21-generic-pae Linux kernel image for version 3.0.0 on x86

**maha@maha-ubuntudesk:~$ sudo dpkg --configure linux-generic**
dpkg: error: dpkg status database is locked by another process
maha@maha-ubuntudesk:~$ sudo dpkg --configure linux-generic
dpkg: error: dpkg status database is locked by another process
maha@maha-ubuntudesk:~$ sudo dpkg --configure linux-generic
dpkg: error: dpkg status database is locked by another process
maha@maha-ubuntudesk:~$ sudo dpkg --configure linux-generic
dpkg: error: dpkg status database is locked by another process
**maha@maha-ubuntudesk:~$ sudo dpkg --audit**
[sudo] password for maha: 
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-image-generic-pae Generic Linux kernel image
 linux-headers-3.0.0-21-generic-pae Linux kernel headers for version 3.0.0 on x
 linux-image-generic  Generic Linux kernel image
 linux-generic-pae    Complete Generic Linux kernel
 linux-generic        Complete Generic Linux kernel

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-image-3.0.0-21-generic Linux kernel image for version 3.0.0 on x86/x86_6
 linux-image-3.0.0-21-generic-pae Linux kernel image for version 3.0.0 on x86

**maha@maha-ubuntudesk:~$ dselect --help**
The program 'dselect' is currently not installed.  You can install it by typing:
sudo apt-get install dselect
**maha@maha-ubuntudesk:~$ sudo apt-get install dselect**
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
maha@maha-ubuntudesk:~$ sudo dpkg --configure -a
Setting up linux-image-3.0.0-21-generic (3.0.0-21.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic


```




```
**maha@maha-ubuntudesk:~$ sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.0.0-21-generic (3.0.0-21.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic

```

---

### Post by gnusci on 2012-06-18
$ sudo apt-get update
$ sudo apt-get upgrade

---

### Post by mahasmb on 2012-06-18
Thanks for your help, but those commands are how I discovered the problem in the first place. I'll run them again anyways.

```
**maha@maha-ubuntudesk:~$ sudo apt-get update**
[sudo] password for maha: 
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                                                                                                              
Get:1 http://dl.google.com stable Release.gpg [198 B]                                                                                                                  
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                                         
Ign http://security.ubuntu.com oneiric-security InRelease                                                                                                              
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                             
Ign http://deb.opera.com stable InRelease                                                                                                    
Get:2 http://security.ubuntu.com oneiric-security Release.gpg [198 B]                                                                        
Get:3 http://dl.google.com stable Release.gpg [198 B]                                                                                                                  
Get:4 http://dl.google.com stable Release [1,347 B]                                                                                          
Hit http://ppa.launchpad.net oneiric Release                                                                                                                           
Get:5 http://security.ubuntu.com oneiric-security Release [40.8 kB]                                                                                                    
Hit http://deb.opera.com stable Release.gpg                                                                                                                            
Hit http://deb.opera.com stable Release                                                                                                                                
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                                                      
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                                                                                
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                                                             
Hit http://deb.opera.com stable/non-free i386 Packages                                                                                                 
Get:6 http://dl.google.com stable Release [1,338 B]                                                                                                    
Get:7 http://dl.google.com stable/main i386 Packages [1,249 B]                                                                                                         
Ign http://deb.opera.com stable/non-free TranslationIndex                                                                                                              
Get:8 http://security.ubuntu.com oneiric-security/main Sources [40.9 kB]                                                                                           
Ign http://dl.google.com stable/main TranslationIndex                                                                                                                  
Get:9 http://dl.google.com stable/main i386 Packages [464 B]                                                                                                           
Get:10 http://security.ubuntu.com oneiric-security/restricted Sources [1,959 B]                                                                                        
Get:11 http://security.ubuntu.com oneiric-security/universe Sources [18.0 kB]                                                                                          
Get:12 http://security.ubuntu.com oneiric-security/multiverse Sources [1,642 B]                                                                                        
Get:13 http://security.ubuntu.com oneiric-security/main i386 Packages [128 kB]                                                                                         
Get:14 http://security.ubuntu.com oneiric-security/restricted i386 Packages [3,939 B]                                                                                  
Get:15 http://security.ubuntu.com oneiric-security/universe i386 Packages [40.2 kB]                                                                                    
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA                                                                                                            
Get:16 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,376 B]                                                                                  
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex                                                                                                  
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex                                                                                            
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex                                                                                            
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex                                                                                              
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                                                                               
Hit http://security.ubuntu.com oneiric-security/main Translation-en                                                                                                    
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en                                                                                               
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en                                                  
Ign http://deb.opera.com stable/non-free Translation-en_CA                                                                                       
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                                                                          
Ign http://deb.opera.com stable/non-free Translation-en                                                                    
Ign http://ca.archive.ubuntu.com oneiric InRelease                                                                         
Ign http://ca.archive.ubuntu.com oneiric-updates InRelease                                           
Ign http://ca.archive.ubuntu.com oneiric-backports InRelease             
Ign http://extras.ubuntu.com oneiric InRelease                           
Get:17 http://ca.archive.ubuntu.com oneiric Release.gpg [198 B]
Get:18 http://extras.ubuntu.com oneiric Release.gpg [72 B]                           
Get:19 http://ca.archive.ubuntu.com oneiric-updates Release.gpg [198 B]  
Hit http://extras.ubuntu.com oneiric Release                                         
Get:20 http://ca.archive.ubuntu.com oneiric-backports Release.gpg [198 B] 
Hit http://extras.ubuntu.com oneiric/main Sources                                    
Get:21 http://ca.archive.ubuntu.com oneiric Release [40.8 kB]            
Hit http://extras.ubuntu.com oneiric/main i386 Packages                            
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                         
Get:22 http://ca.archive.ubuntu.com oneiric-updates Release [40.8 kB]                                                                                                  
Get:23 http://ca.archive.ubuntu.com oneiric-backports Release [40.8 kB]                                                                                                
Get:24 http://ca.archive.ubuntu.com oneiric/main Sources [877 kB]                                                                                                      
Ign http://extras.ubuntu.com oneiric/main Translation-en_CA                                                                                                            
Ign http://extras.ubuntu.com oneiric/main Translation-en                                                                                                               
Ign http://dl.google.com stable/main TranslationIndex                                                                                                                  
Ign http://dl.google.com stable/main Translation-en_CA                                                                                                                 
Ign http://dl.google.com stable/main Translation-en                                                                                                                    
Ign http://dl.google.com stable/main Translation-en_CA                                                                                                                 
Ign http://dl.google.com stable/main Translation-en                                                                                                                    
Get:25 http://ca.archive.ubuntu.com oneiric/restricted Sources [5,351 B]                                                                                               
Get:26 http://ca.archive.ubuntu.com oneiric/universe Sources [4,677 kB]                                                                                                
Get:27 http://ca.archive.ubuntu.com oneiric/multiverse Sources [149 kB]                                                                                                
Get:28 http://ca.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]                                                                                              
Get:29 http://ca.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]                                                                                         
Get:30 http://ca.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]                                                                                          
Get:31 http://ca.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]                                                                                          
Hit http://ca.archive.ubuntu.com oneiric/main TranslationIndex                                                                                                         
Hit http://ca.archive.ubuntu.com oneiric/multiverse TranslationIndex                                                                                                   
Hit http://ca.archive.ubuntu.com oneiric/restricted TranslationIndex                                                                                                   
Hit http://ca.archive.ubuntu.com oneiric/universe TranslationIndex                                                                                                     
Get:32 http://ca.archive.ubuntu.com oneiric-updates/main Sources [143 kB]                                                                                              
Get:33 http://ca.archive.ubuntu.com oneiric-updates/restricted Sources [3,347 B]                                                                                       
Get:34 http://ca.archive.ubuntu.com oneiric-updates/universe Sources [55.5 kB]                                                                                         
Get:35 http://ca.archive.ubuntu.com oneiric-updates/multiverse Sources [3,652 B]                                                                                       
Get:36 http://ca.archive.ubuntu.com oneiric-updates/main i386 Packages [358 kB]                                                                                        
Get:37 http://ca.archive.ubuntu.com oneiric-updates/restricted i386 Packages [6,631 B]                                                                                 
Get:38 http://ca.archive.ubuntu.com oneiric-updates/universe i386 Packages [119 kB]                                                                                    
Get:39 http://ca.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,361 B]                                                                                 
Hit http://ca.archive.ubuntu.com oneiric-updates/main TranslationIndex                                                                                                 
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex                                                                                           
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted TranslationIndex                                                                                           
Hit http://ca.archive.ubuntu.com oneiric-updates/universe TranslationIndex                                                                                             
Get:40 http://ca.archive.ubuntu.com oneiric-backports/main Sources [2,742 B]                                                                                           
Get:41 http://ca.archive.ubuntu.com oneiric-backports/restricted Sources [14 B]                                                                                        
Get:42 http://ca.archive.ubuntu.com oneiric-backports/universe Sources [9,019 B]                                                                                       
Get:43 http://ca.archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]                                                                                        
Get:44 http://ca.archive.ubuntu.com oneiric-backports/main i386 Packages [3,296 B]                                                                                     
Get:45 http://ca.archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]                                                                                  
Get:46 http://ca.archive.ubuntu.com oneiric-backports/universe i386 Packages [13.4 kB]                                                                                 
Get:47 http://ca.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]                                                                                  
Hit http://ca.archive.ubuntu.com oneiric-backports/main TranslationIndex                                                                                               
Hit http://ca.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex                                                                                         
Hit http://ca.archive.ubuntu.com oneiric-backports/restricted TranslationIndex                                                                                         
Hit http://ca.archive.ubuntu.com oneiric-backports/universe TranslationIndex                                                                                           
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en_CA                                                                                                        
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en                                                                                                           
Hit http://ca.archive.ubuntu.com oneiric/multiverse Translation-en                                                                                                     
Hit http://ca.archive.ubuntu.com oneiric/restricted Translation-en                                                                                                     
Hit http://ca.archive.ubuntu.com oneiric/universe Translation-en                                                                                                       
Hit http://ca.archive.ubuntu.com oneiric-updates/main Translation-en                                                                                                   
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse Translation-en                                                                                             
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted Translation-en                                                                                             
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Translation-en                                                                                               
Hit http://ca.archive.ubuntu.com oneiric-backports/main Translation-en                                                                                                 
Hit http://ca.archive.ubuntu.com oneiric-backports/multiverse Translation-en                                                                                           
Hit http://ca.archive.ubuntu.com oneiric-backports/restricted Translation-en                                                                                           
Hit http://ca.archive.ubuntu.com oneiric-backports/universe Translation-en                                                                                             
Fetched 12.7 MB in 34s (371 kB/s)                                                                                                                                      
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
**maha@maha-ubuntudesk:~$ sudo apt-get upgrade**
[B][COLOR="Red"]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR][/B]

```

I actually didn't have Muon or any other package service running, so I don't understand why I've got that message.

So, since I'm desperate, I opened up System Monitor, did a search for "dpkg" (I actually find something) and ended the "dpkg" process that's still running, but I guess stalled?

And I try again

```
**maha@maha-ubuntudesk:~$ sudo apt-get update**
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                                                                                                              
Ign http://deb.opera.com stable InRelease                                                                                                                              
Get:1 http://dl.google.com stable Release.gpg [198 B]                                                                                                                  
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                                         
Ign http://extras.ubuntu.com oneiric InRelease                                                                                                                         
Get:2 http://dl.google.com stable Release.gpg [198 B]                                                                                                                  
Hit http://deb.opera.com stable Release.gpg                                                                                                                            
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                                       
Ign http://security.ubuntu.com oneiric-security InRelease                                                        
Hit http://extras.ubuntu.com oneiric Release.gpg                                                                 
Get:3 http://dl.google.com stable Release [1,347 B]                                                              
Hit http://deb.opera.com stable Release                                                                                                                         
Ign http://ca.archive.ubuntu.com oneiric InRelease                                                                                                              
Ign http://ca.archive.ubuntu.com oneiric-updates InRelease                                                                            
Ign http://ca.archive.ubuntu.com oneiric-backports InRelease                                                                          
Hit http://ppa.launchpad.net oneiric Release                                                                     
Hit http://security.ubuntu.com oneiric-security Release.gpg                                                                             
Get:4 http://dl.google.com stable Release [1,338 B]                                                                                     
Hit http://extras.ubuntu.com oneiric Release                                                                                                 
Hit http://ca.archive.ubuntu.com oneiric Release.gpg                                                                                         
Hit http://ca.archive.ubuntu.com oneiric-updates Release.gpg                                                          
Hit http://security.ubuntu.com oneiric-security Release                                                               
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                            
Hit http://extras.ubuntu.com oneiric/main Sources                                                                     
Hit http://deb.opera.com stable/non-free i386 Packages                                                                
Hit http://ca.archive.ubuntu.com oneiric-backports Release.gpg                                                        
Hit http://ca.archive.ubuntu.com oneiric Release                                                                      
Hit http://security.ubuntu.com oneiric-security/main Sources                                                                                                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                                                                                     
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                                            
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                               
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                                  
Ign http://deb.opera.com stable/non-free TranslationIndex                                                                                   
Hit http://ca.archive.ubuntu.com oneiric-updates Release                                                              
Hit http://ca.archive.ubuntu.com oneiric-backports Release                                                            
Hit http://security.ubuntu.com oneiric-security/restricted Sources                                                                                                 
Hit http://security.ubuntu.com oneiric-security/universe Sources                                                                       
Hit http://security.ubuntu.com oneiric-security/multiverse Sources                                                                     
Hit http://security.ubuntu.com oneiric-security/main i386 Packages                                                                     
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages                                                               
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages                                                                 
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages                                                               
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex                                                                  
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex                                                            
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex                                                            
Get:5 http://dl.google.com stable/main i386 Packages [1,249 B]                                                                         
Hit http://ca.archive.ubuntu.com oneiric/main Sources                                                                                        
Hit http://ca.archive.ubuntu.com oneiric/restricted Sources                                                      
Hit http://ca.archive.ubuntu.com oneiric/universe Sources                                                        
Hit http://ca.archive.ubuntu.com oneiric/multiverse Sources                                                      
Hit http://ca.archive.ubuntu.com oneiric/main i386 Packages                                                      
Hit http://ca.archive.ubuntu.com oneiric/restricted i386 Packages                                                
Ign http://dl.google.com stable/main TranslationIndex                                                                                                         
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex                                                              
Get:6 http://dl.google.com stable/main i386 Packages [464 B]                                                                           
Hit http://ca.archive.ubuntu.com oneiric/universe i386 Packages                                                                            
Hit http://ca.archive.ubuntu.com oneiric/multiverse i386 Packages                                                                          
Hit http://ca.archive.ubuntu.com oneiric/main TranslationIndex                                                                             
Hit http://ca.archive.ubuntu.com oneiric/multiverse TranslationIndex                                                                       
Hit http://ca.archive.ubuntu.com oneiric/restricted TranslationIndex                                                                       
Hit http://ca.archive.ubuntu.com oneiric/universe TranslationIndex                                                                         
Hit http://ca.archive.ubuntu.com oneiric-updates/main Sources                                                        
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted Sources                                                  
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Sources                                                                          
Hit http://security.ubuntu.com oneiric-security/main Translation-en                                                                        
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en                                                                  
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse Sources                                                                        
Hit http://ca.archive.ubuntu.com oneiric-updates/main i386 Packages                                                                        
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted i386 Packages                                                                  
Hit http://ca.archive.ubuntu.com oneiric-updates/universe i386 Packages                                                                    
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse i386 Packages                                            
Hit http://ca.archive.ubuntu.com oneiric-updates/main TranslationIndex                                               
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex                                         
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted TranslationIndex                                                               
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en                                                                  
Hit http://ca.archive.ubuntu.com oneiric-updates/universe TranslationIndex                                                                 
Hit http://ca.archive.ubuntu.com oneiric-backports/main Sources                                                                            
Hit http://ca.archive.ubuntu.com oneiric-backports/restricted Sources                                                                      
Hit http://ca.archive.ubuntu.com oneiric-backports/universe Sources                                                                        
Hit http://ca.archive.ubuntu.com oneiric-backports/multiverse Sources                                                
Hit http://ca.archive.ubuntu.com oneiric-backports/main i386 Packages                                                
Hit http://ca.archive.ubuntu.com oneiric-backports/restricted i386 Packages                                                                
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                                                                    
Hit http://ca.archive.ubuntu.com oneiric-backports/universe i386 Packages                                            
Hit http://ca.archive.ubuntu.com oneiric-backports/multiverse i386 Packages                                          
Hit http://ca.archive.ubuntu.com oneiric-backports/main TranslationIndex                                             
Hit http://ca.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex                                       
Hit http://ca.archive.ubuntu.com oneiric-backports/restricted TranslationIndex                                       
Hit http://ca.archive.ubuntu.com oneiric-backports/universe TranslationIndex                   
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en_CA                                
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en                                                         
Hit http://ca.archive.ubuntu.com oneiric/multiverse Translation-en                                                   
Hit http://ca.archive.ubuntu.com oneiric/restricted Translation-en                                                   
Hit http://ca.archive.ubuntu.com oneiric/universe Translation-en                                                     
Hit http://ca.archive.ubuntu.com oneiric-updates/main Translation-en                                                 
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse Translation-en                     
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted Translation-en                     
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Translation-en                       
Ign http://extras.ubuntu.com oneiric/main Translation-en_CA                                    
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA                                    
Hit http://ca.archive.ubuntu.com oneiric-backports/main Translation-en                         
Hit http://ca.archive.ubuntu.com oneiric-backports/multiverse Translation-en                   
Hit http://ca.archive.ubuntu.com oneiric-backports/restricted Translation-en                                         
Ign http://extras.ubuntu.com oneiric/main Translation-en                                                             
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                             
Hit http://ca.archive.ubuntu.com oneiric-backports/universe Translation-en                     
Ign http://deb.opera.com stable/non-free Translation-en_CA               
Ign http://deb.opera.com stable/non-free Translation-en
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_CA
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_CA
Ign http://dl.google.com stable/main Translation-en
Fetched 4,794 B in 3s (1,221 B/s)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
**maha@maha-ubuntudesk:~$ sudo apt-get upgrade**
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
[B]maha@maha-ubuntudesk:~$ sudo dpkg --configure -a
[/B]Setting up linux-image-3.0.0-21-generic (3.0.0-21.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic


```

Once again, it just stalls right there.

I have been at this for hours on and off, so I've tried rebooting the computer and running each of the commands by themselves to no avail.

I have a general idea of what I'm doing, but don't fully understand everything here. And I'm just now healing from a long treacherous illness so I'm not at my best either.

---

### Post by cybercity@localhost on 2012-06-18
did you try???

```

sudo dpkg -configure -a

or

sudo dpkg --configure -a


```

---

### Post by mahasmb on 2012-06-18
As per my comments in my first post and the first line of code in my first post, yes. I absolutely did try it. Numerous times.

---

### Post by Old_Grey_Wolf on 2012-06-18
You need to remove the lock file. Enter these commands to do that ```
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```

Then update and upgrade.

---

### Post by mahasmb on 2012-06-18
It still stalls after removing the lock file.

```

[B]maha@maha-ubuntudesk:~$ sudo rm /var/lib/dpkg/lock
maha@maha-ubuntudesk:~$ sudo dpkg --configure -a[/B]
Setting up linux-image-3.0.0-21-generic (3.0.0-21.35) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic

```

The problem is with setting up this package: **linux-image-3.0.0-21-generic**

It needs to be set up, but it always stalls, no matter how I do it.

---

### Post by mahasmb on 2012-06-19
```
maha@maha-ubuntudesk:~$ sudo dpkg-reconfigure linux-image-3.0.0-21-generic
[COLOR="Red"]/usr/sbin/dpkg-reconfigure: **linux-image-3.0.0-21-generic is broken** or not fully installed[/COLOR]

```

I noticed I already double posted, which is bad enough, so I'm just editing this post instead of triple posting.

$ sudo dpkg --remove --force-remove-reinstreq linux-image-3.0.0-21-generic

Then rebooting into recovery mode and running

$ sudo dpkg --configure -a

seems to have fixed the problem.

I'm gonna give it a day before I mark this as solved, just in case something else breaks.

Thanks for all your help, everyone.

---

### Post by oldos2er on 2012-06-19
Could you please mark the thread as 'Solved' under Thread Tools? Thanks.

---

### Post by mahasmb on 2012-06-19
Something else isn't working ...

I'm upgrading to 12.04, but it's stalled for hours now.

```
Unpacking replacement okular-extra-backends ...
Preparing to replace plasma-widget-menubar 0.1.16-0ubuntu1 (using .../plasma-widget-menubar_0.1.17-0ubuntu1_i386.deb) ...
Unpacking replacement plasma-widget-menubar ...
Preparing to replace plasma-widget-message-indicator 0.5.8-0ubuntu1 (using .../plasma-widget-message-indicator_0.5.8-1ubuntu1_i386.deb) ...
Unpacking replacement plasma-widget-message-indicator ...
Preparing to replace pulseaudio-module-bluetooth 1:1.0-0ubuntu3.1 (using .../pulseaudio-module-bluetooth_1%3a1.1-0ubuntu15.1_i386.deb) ...
Unpacking replacement pulseaudio-module-bluetooth ...
Preparing to replace python-webob 1.0.8-1 (using .../python-webob_1.1.1-1_all.deb) ...
Unpacking replacement python-webob ...
Preparing to replace transcode 3:1.1.5-0ubuntu9 (using .../transcode_3%3a1.1.5-0ubuntu10_i386.deb) ...
Unpacking replacement transcode ...
Preparing to replace transcode-doc 3:1.1.5-0ubuntu9 (using .../transcode-doc_3%3a1.1.5-0ubuntu10_all.deb) ...
Unpacking replacement transcode-doc ...
Preparing to replace transcode-utils 3:1.1.5-0ubuntu9 (using .../transcode-utils_3%3a1.1.5-0ubuntu10_i386.deb) ...
Unpacking replacement transcode-utils ...
Preparing to replace userconfig 0.9.0-0ubuntu9 (using .../userconfig_0.9.0-0ubuntu10_all.deb) ...
Unpacking replacement userconfig ...
Preparing to replace wine 1.2.3-0ubuntu1 (using .../wine_1.4-0ubuntu4_i386.deb) ...
Unpacking replacement wine ...
Processing triggers for install-info ...
Processing triggers for libglib2.0-0 ...
Processing triggers for gxine ...
Updated the MIME types in gxine's menu file.
Setting up gettext-base (0.18.1.1-5ubuntu3) ...
Setting up libnewt0.52 (0.52.11-2ubuntu10) ...
Setting up libpopt0 (1.16-3ubuntu1) ...
Setting up whiptail (0.52.11-2ubuntu10) ...
Setting up friendly-recovery (0.2.25) ...
**[COLOR="Red"]Installing new version of config file /etc/init/friendly-recovery.conf ...[/COLOR]**
```

I've tried closing off everything but the installer, but no luck. I've spent the last two hours trying to fix this with also no luck. Luckily, I can still use Chrome and Opera to do the research.

---

### Post by Old_Grey_Wolf on 2012-06-19
> **mahasmb said:**
> 
**[COLOR="Red"]Installing new version of config file /etc/init/friendly-recovery.conf ...[/COLOR]**

It might be this bug ([#994448]("https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/994448") ). I'm just guessing. Try these commands ```
sudo apt-get -f install

sudo apt-get update

sudo apt-get dist-upgrade
```

---

### Post by mahasmb on 2012-06-20
It doesn't help :/

---

### Post by Old_Grey_Wolf on 2012-06-21
> **mahasmb said:**
> It doesn't help :/

Your original problem was solved.

You are now experiencing problems upgrading to 12.04 from 11.10. I would suggest starting a new thread.

There are several bug reports of problems upgrading when the friendly-recovery (0.2.25) package is present. Personally, if I had this problem I would have backed up my important files and do a fresh install of 12.04.

---

### Post by mahasmb on 2012-06-23
Yeah, I back up all my files every 1-2 weeks. I just didn't want to reinstall all my programs and reconfigure everything after a fresh install, so I opted for just an upgrade this time.

Anyhow, I'm gonna be replacing my HDD anyways since I'm experiencing problems with it. So I'll have to do a fresh install after that anyways.

Thank you for all of the help.

I'm marking this thread as solved.

---

