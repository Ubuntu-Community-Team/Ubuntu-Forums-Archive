---
title: "Software updater failed to download package file Check internet connection"
date: 2016-07-04
forum: Installation &amp; Upgrades
---

### Post by Jerry_Price on 2016-07-04
I run a Toshiba Tecra M5 with Xubuntu 14.04.4 Trusty

For the last week Software updater has failed with the above message. I have searched here and elsewhere for a solution but can't find one.

When I run "sudo apt-get update" it returns:

```
 jerry@jerry-TECRA-M5:~$ sudo apt-get update[sudo] password for jerry: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_AU                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_AU                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_AU                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_AU              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_AU              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_AU                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Reading package lists... Done                                                  
W: There is no public key available for the following key IDs:
1397BC53640DB551
W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages)
jerry@jerry-TECRA-M5:~$ 
```

"sudo apt-get dist-upgrade" it returns:

```
 jerry@jerry-TECRA-M5:~$ sudo apt-get update
[sudo] password for jerry: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_AU                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_AU                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_AU                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_AU              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_AU              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_AU                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Reading package lists... Done                                                  
W: There is no public key available for the following key IDs:
1397BC53640DB551
W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages)
jerry@jerry-TECRA-M5:~$ sudo apt-get dist-upgrade
[sudo] password for jerry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb libntdb1 linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-3.16.0-76
  linux-headers-3.16.0-76-generic linux-headers-generic-lts-utopic
  linux-image-3.16.0-30-generic linux-image-3.16.0-76-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-76-generic
  linux-image-generic-lts-utopic python-ntdb
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.16.0-76 linux-headers-3.16.0-76-generic
  linux-image-3.16.0-76-generic linux-image-extra-3.16.0-76-generic
The following packages will be upgraded:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-extra dpkg
  dpkg-dev gir1.2-gtk-3.0 google-earth-stable grub-common grub-pc grub-pc-bin
  grub2-common libdpkg-perl libexpat1 libgail-3-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libnautilus-extension1a linux-headers-generic-lts-utopic
  linux-image-generic-lts-utopic linux-libc-dev nautilus-data oneconf
  oneconf-common oxideqt-codecs-extra python-oneconf python3-oneconf wget
28 to upgrade, 4 to newly install, 0 to remove and 0 not to upgrade.
Need to get 27.7 MB/174 MB of archives.
After this operation, 221 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main google-earth-stable i386 6.1.0.4738-r0
  404  Not Found [IP: 216.58.220.110 80]
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libgtk-3-common all 3.10.8-0ubuntu1.6 [167 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libgail-3-0 i386 3.10.8-0ubuntu1.6 [20.1 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libgtk-3-0 i386 3.10.8-0ubuntu1.6 [1,923 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main gir1.2-gtk-3.0 i386 3.10.8-0ubuntu1.6 [174 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libgtk-3-bin i386 3.10.8-0ubuntu1.6 [18.0 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libnautilus-extension1a i386 1:3.10.1-0ubuntu9.11 [51.9 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9.11 [50.7 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main oneconf-common all 0.3.7.14.04.1 [6,042 B]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main python3-oneconf all 0.3.7.14.04.1 [19.5 kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main oneconf all 0.3.7.14.04.1 [5,458 B]
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main python-oneconf all 0.3.7.14.04.1 [19.7 kB]
Fetched 2,455 kB in 9s (260 kB/s)                                              
E: Failed to fetch [http://dl.google.com/linux/earth/deb/pool/main/g/google-earth-stable/google-earth-stable_6.1.0.4738-r0_i386.deb](http://dl.google.com/linux/earth/deb/pool/main/g/google-earth-stable/google-earth-stable_6.1.0.4738-r0_i386.deb) 404  Not Found [IP: 216.58.220.110 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
jerry@jerry-TECRA-M5:~$
```

So it appears that something is wrong with Google earth

Why is this only happening now when Google earth has been installed for over a year 
If google earth is missing does that prevent any or all of the updates loading ?
How do I fix it 

Thanks in advance
Jerry

---

### Post by grahammechanical on 2016-07-04
Do you see this?

> E: Failed to fetch [http://dl.google.com/linux/earth/deb...38-r0_i386.deb]("http://dl.google.com/linux/earth/deb/pool/main/g/google-earth-stable/google-earth-stable_6.1.0.4738-r0_i386.deb") 404  Not Found [IP: 216.58.220.110 80]

If just one of the archives/repositories is not available then Update Manager presents that error message. Google no longer supports 32 bit Google Chrome and may be it no longer supports 32 bit Google Earth as well and i386 = 32 bit version. You need to remove that entry from the software sources list. If this was Ubuntu I would say, go to System Settings>Software & Updates>Other Software tab and untick the box for the google repository (dl.google.com). Or, even remove it. I do not know if that information is accurate for Xubuntu.

Regards.

---

### Post by Jerry_Price on 2016-07-05
Thanks Grahammechanical
Yes I did see that line but I didn't know what to do about it. I followed your advice and unticked the box for di.google.com. in the "other software" tab (yes it's the same for Xubuntu) and it all works again.
It's so easy when you know how but completely baffling when you don't
I guess every little bit helps

Thanks for your time and help
Jerry

---

