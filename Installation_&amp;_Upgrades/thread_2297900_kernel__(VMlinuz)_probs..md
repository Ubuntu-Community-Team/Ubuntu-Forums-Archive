---
title: "kernel / (VMlinuz??) probs."
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by Euanbuntu on 2015-10-07
Ok, so a while ago I got a system message saying something along the lines of 'no space in /boot', so I went and did a couple of things.

I cleared out some of the old files in /boot, leaving only the most recent ones, but before this, I may have emptied an src file by accident, thinking I was doing the right thing.

It seems now that /usr/local/src is empty - I don't know if this is a good thing or not :-/ 

Anyway, recently I tried opening the Software Centre and get this error:-

> New software cannot be installed, because there is a problem with the software currently installed. Do you want to repair this problem now?

So I click yes, but then after it attempts to 'Repair installed software', get this:

```

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 295023 files and directories currently installed.)
Preparing to unpack .../linux-image-3.16.0-50-generic_3.16.0-50.67~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-50-generic (3.16.0-50.67~14.04.1) over (3.16.0-50.66~14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.16.0-50-generic_3.16.0-50.67~14.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.16.0-50-generic' to '/boot/vmlinuz-3.16.0-50-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.16.0-50-generic_3.16.0-50.67~14.04.1_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of linux-signed-image-3.16.0-50-generic:
 linux-signed-image-3.16.0-50-generic depends on linux-image-3.16.0-50-generic (= 3.16.0-50.67~14.04.1); however:
  Version of linux-image-3.16.0-50-generic on system is 3.16.0-50.66~14.04.1.

dpkg: error processing package linux-signed-image-3.16.0-50-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-generic-lts-utopic:
 linux-signed-image-generic-lts-utopic depends on linux-signed-image-3.16.0-50-generic; however:
  Package linux-signed-image-3.16.0-50-generic is not configured yet.

dpkg: error processing package linux-signed-image-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-3.16.0-50-generic (3.16.0-50.67~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-50-generic

gzip: stdout: No space left on device
cpio: write error: Broken pipe
E: mkinitramfs failure cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-3.16.0-50-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.16.0-50-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-signed-generic-lts-utopic:
 linux-signed-generic-lts-utopic depends on linux-signed-image-generic-lts-utopic (= 3.16.0.50.41); however:
  Package linux-signed-image-generic-lts-utopic is not configured yet.

dpkg: error processing package linux-signed-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-utopic:
 linux-image-generic-lts-utopic depends on linux-image-extra-3.16.0-50-generic; however:
  Package linux-image-extra-3.16.0-50-generic is not configured yet.

dpkg: error processing package linux-image-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-utopic:
 linux-generic-lts-utopic depends on linux-image-generic-lts-utopic (= 3.16.0.50.41); however:
  Package linux-image-generic-lts-utopic is not configured yet.

dpkg: error processing package linux-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured

```

Next I did some searching on here and askubuntu etc etc, and tried doing the following, all with vaguely similar results:

> sudo apt-get update && sudo apt-get upgrade

that gave me this:

```
bubble@fishtank:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-signed-image-3.16.0-50-generic : Depends: linux-image-3.16.0-50-generic (= 3.16.0-50.67~14.04.1) but 3.16.0-50.66~14.04.1 is installed
E: Unmet dependencies. Try using -f.

```

so I tried that and got

```
bubble@fishtank:~$ sudo apt-get -f install
[sudo] password for bubble: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-46 linux-headers-3.16.0-46-generic
  linux-headers-3.16.0-48 linux-headers-3.16.0-48-generic
  linux-image-3.16.0-46-generic linux-image-3.16.0-48-generic
  linux-image-extra-3.16.0-46-generic linux-image-extra-3.16.0-48-generic
  linux-signed-image-3.16.0-46-generic linux-signed-image-3.16.0-48-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.16.0-50-generic
Suggested packages:
  fdutils linux-lts-utopic-tools
The following packages will be upgraded:
  linux-image-3.16.0-50-generic
1 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
6 not fully installed or removed.
Need to get 0 B/16.2 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 295023 files and directories currently installed.)
Preparing to unpack .../linux-image-3.16.0-50-generic_3.16.0-50.67~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-50-generic (3.16.0-50.67~14.04.1) over (3.16.0-50.66~14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.16.0-50-generic_3.16.0-50.67~14.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.16.0-50-generic' to '/boot/vmlinuz-3.16.0-50-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.16.0-50-generic_3.16.0-50.67~14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Then I tried 

```
bubble@fishtank:~$ sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease                              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release                                
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [96.9 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources                           
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,341 B]  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [3,357 B]  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main amd64 Packages                    
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [31.0 kB]    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted amd64 Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://deb.bitmask.net](http://deb.bitmask.net) trusty InRelease                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease                         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [350 kB]  
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release.gpg                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release.gpg                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release                           
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release                           
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main amd64 Packages               
Ign [https://launchpad.net](https://launchpad.net) trusty InRelease                                     
Hit [http://deb.bitmask.net](http://deb.bitmask.net) trusty/main Sources                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main amd64 Packages               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_GB            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse i386 Packages               
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en               
Hit [http://deb.bitmask.net](http://deb.bitmask.net) trusty/main amd64 Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en_GB                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en_GB           
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [12.4 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [117 kB]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en_GB            
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://deb.bitmask.net](http://deb.bitmask.net) trusty/main i386 Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en_GB           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [3,691 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en_GB             
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [333 kB]   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [https://launchpad.net](https://launchpad.net) trusty Release.gpg                                   
Ign [https://launchpad.net](https://launchpad.net) trusty Release                                       
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.2 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [117 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,833 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Ign [http://deb.bitmask.net](http://deb.bitmask.net) trusty/main Translation-en_GB                       
Ign [http://deb.bitmask.net](http://deb.bitmask.net) trusty/main Translation-en
Err [https://launchpad.net](https://launchpad.net) trusty/main amd64 Packages                           
  HttpError404
Err [https://launchpad.net](https://launchpad.net) trusty/main i386 Packages                            
  HttpError404
Ign [https://launchpad.net](https://launchpad.net) trusty/main Translation-en_GB                        
Ign [https://launchpad.net](https://launchpad.net) trusty/main Translation-en                           
Fetched 1,082 kB in 9s (118 kB/s)                                              
W: Failed to fetch [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev/dists/trusty/main/binary-amd64/Packages](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev/dists/trusty/main/binary-amd64/Packages)  HttpError404

W: Failed to fetch [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev/dists/trusty/main/binary-i386/Packages](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev/dists/trusty/main/binary-i386/Packages)  HttpError404

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

then

```
bubble@fishtank:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-signed-image-3.16.0-50-generic:
 linux-signed-image-3.16.0-50-generic depends on linux-image-3.16.0-50-generic (= 3.16.0-50.67~14.04.1); however:
  Version of linux-image-3.16.0-50-generic on system is 3.16.0-50.66~14.04.1.

dpkg: error processing package linux-signed-image-3.16.0-50-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-generic-lts-utopic:
 linux-signed-image-generic-lts-utopic depends on linux-signed-image-3.16.0-50-generic; however:
  Package linux-signed-image-3.16.0-50-generic is not configured yet.

dpkg: error processing package linux-signed-image-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-3.16.0-50-generic (3.16.0-50.67~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-50-generic /boot/vmlinuz-3.16.0-50-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-50-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.16.0-50-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.16.0-50-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-signed-generic-lts-utopic:
 linux-signed-generic-lts-utopic depends on linux-signed-image-generic-lts-utopic (= 3.16.0.50.41); however:
  Package linux-signed-image-generic-lts-utopic is not configured yet.

dpkg: error processing package linux-signed-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-utopic:
 linux-image-generic-lts-utopic depends on linux-image-extra-3.16.0-50-generic; however:
  Package linux-image-extra-3.16.0-50-generic is not configured yet.

dpkg: error processing package linux-image-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-utopic:
 linux-generic-lts-utopic depends on linux-image-generic-lts-utopic (= 3.16.0.50.41); however:
  Package linux-image-generic-lts-utopic is not configured yet.

dpkg: error processing package linux-generic-lts-utopic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-signed-image-3.16.0-50-generic
 linux-signed-image-generic-lts-utopic
 linux-image-extra-3.16.0-50-generic
 linux-signed-generic-lts-utopic
 linux-image-generic-lts-utopic
 linux-generic-lts-utopic

```

So now I am lost and would really like some help please!

I know I have some parts of the image/kernel missing, or have the incorrect ones as I can understand that much, but I don't know what to do about it.

Please could someone help me?

Thanks in advance. I can copy/paste any outputs you might need.

---

### Post by dino99 on 2015-10-07
What you did is not enough, you really need to purge the oldest installed kernels (each having 2 headers + 2 images)
Synaptic is an easy tool to do that stuff, but 'autoremove' can partially do the job (does not make it complete)
You only need tthe two latest working kernels (in case one have a problem, you still get the other to boot with)

**** sudo apt-get dist-upgrade  *******
i doubt it can understand that command: next to Trusty, was Utopic, but that one have reached EOL some times ago, so using that command is a bad idea

---

### Post by Euanbuntu on 2015-10-07
> **dino99 said:**
> What you did is not enough, you really need to purge the oldest installed kernels (each having 2 headers + 2 images)
Synaptic is an easy tool to do that stuff, but 'autoremove' can partially do the job (does not make it complete)
You only need tthe two latest working kernels (in case one have a problem, you still get the other to boot with)

**** sudo apt-get dist-upgrade  *******
i doubt it can understand that command: next to Trusty, was Utopic, but that one have reached EOL some times ago, so using that command is a bad idea

Hi thanks for your input.

I wasn't being specific, sorry: at the beginning of my post, when I said I cleared out 'some of the old files in /boot', actually what happened is what you have suggested. But I think I have done something else too and I am not sure how to remedy the situation. 

Here is the contents of /boot now:

```
bubble@fishtank:~$ cd /boot
bubble@fishtank:/boot$ ls
abi-3.16.0-49-generic         lost+found
abi-3.16.0-50-generic         memtest86+.bin
config-3.16.0-49-generic      memtest86+.elf
config-3.16.0-50-generic      memtest86+_multiboot.bin
efi                           System.map-3.16.0-49-generic
grub                          System.map-3.16.0-50-generic
initrd.img-3.16.0-49-generic  vmlinuz-3.16.0-49-generic.efi.signed
initrd.img-3.16.0-50-generic  vmlinuz-3.16.0-50-generic
bubble@fishtank:/boot$ 
```

Does this make things any clearer? Can anyone shed any light on this please?

Also, I just did this, as I noticed it was suggesting I do it and got the following:

```
bubble@fishtank:~$ sudo apt-get autoremove
[sudo] password for bubble: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-signed-image-3.16.0-50-generic : Depends: linux-image-3.16.0-50-generic (= 3.16.0-50.67~14.04.1) but 3.16.0-50.66~14.04.1 is installed
E: Unmet dependencies. Try using -f.
bubble@fishtank:~$ 

```

I think the problem has something to do with these images depending on each other, and that might be what I deleted from /usr/src right at the beginning (look at the first few lines of the original post please)...

Does anyone know how I fix this please?

---

### Post by Euanbuntu on 2015-10-10
bump

---

### Post by mörgæs on 2015-10-11
Please run ```
cat /etc/apt/sources.list
``` and post the output in CODE (not QUOTE) tags.

---

### Post by Euanbuntu on 2015-10-11
> **mörgæs said:**
> Please run ```
cat /etc/apt/sources.list
``` and post the output in CODE (not QUOTE) tags.

Sure, no problem mörgæs. Another good pointer there, thank you - I am learning! :)

```

bubble@fishtank:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-GNOME 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main multiverse restricted universe
deb-src http://archive.ubuntu.com/ubuntu trusty main multiverse restricted universe #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty main multiverse restricted universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main multiverse restricted universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://deb.bitmask.net/debian trusty main
deb-src http://deb.bitmask.net/debian trusty main
deb-src http://deb.bitmask.net/debian trusty main
deb http://archive.canonical.com/ trusty partner
# deb-src http://archive.canonical.com/ trusty partner
deb https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev trusty main
# deb-src https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev trusty main

```

---

### Post by mörgæs on 2015-10-11
The sources.list refers to Trusty but the images mentioned in the posts above have Utopic as part of their name. 

I can't say what is the reason for this nor the solution, just point it out to someone more experienced than me.

---

### Post by Euanbuntu on 2016-01-02
In the end I just did a reinstall.

---

