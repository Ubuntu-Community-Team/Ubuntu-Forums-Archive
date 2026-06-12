---
title: "problem updating kernel, can anyone help?"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by Nossie on 2008-10-09
Everytime I try and update the kernel I get this error and cant find anything to get around it... any ideas? :-|

An error occured:
```
E: linux-image-2.6.24-21-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-image: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured


```


```
[sudo] password for ian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-image
 linux-restricted-modules-2.6.24-21-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@Jupiter-Ubuntu:~$ 

```

---

### Post by Pumalite on 2008-10-09
Have you tried?:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Nossie on 2008-10-09
Sadly I keep getting this :-| I've also tried fully removing the new packages and doing a fresh upgrade to no avail :(

any help is greatly appreciated, cheers!

<CODE>
ian@Jupiter-Ubuntu:~$ sudo dpkg --configure -a
sudo: unable to resolve host Jupiter-Ubuntu
[sudo] password for ian: 
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-restricted-modules-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-image
ian@Jupiter-Ubuntu:~$ sudo apt-get -f install
sudo: unable to resolve host Jupiter-Ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-image
 linux-restricted-modules-2.6.24-21-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@Jupiter-Ubuntu:~$ sudo apt-get update
sudo: unable to resolve host Jupiter-Ubuntu
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_GB     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Translation-en_GB                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release.gpg         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Translation-en_GB
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                    
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/universe Translation-en_GB     
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/multiverse Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release.gpg                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Translation-en_GB   
Get: 4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get: 5 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Translation-en_GB     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports Release                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security Release                        
Get: 6 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Sources
Fetched 6B in 2s (3B/s)  
Reading package lists... Done
ian@Jupiter-Ubuntu:~$ sudo apt-get dist-upgrade
sudo: unable to resolve host Jupiter-Ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-image
 linux-restricted-modules-2.6.24-21-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@Jupiter-Ubuntu:~$ 
</CODE>

---

### Post by Pumalite on 2008-10-09
Try with all your repos open

---

### Post by Nossie on 2008-10-10
hi,

as far as I know... all the sources are open yet it still seems to be missing stuff??

```
ian@Jupiter-Ubuntu:~$ sudo apt-get update
sudo: unable to resolve host Jupiter-Ubuntu
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_GB           
Ign http://ppa.launchpad.net hardy Release.gpg                      
Hit http://archive.ubuntu.com hardy Release.gpg                     
Hit http://archive.ubuntu.com hardy/main Translation-en_GB           
Hit http://wine.budgetdedicated.com hardy Release.gpg                
Ign http://wine.budgetdedicated.com hardy/main Translation-en_GB     
Ign http://ppa.launchpad.net hardy/main Translation-en_GB            
Ign http://ppa.launchpad.net hardy/universe Translation-en_GB
Ign http://ppa.launchpad.net hardy Release.gpg                       
Ign http://ppa.launchpad.net hardy/main Translation-en_GB            
Ign http://ppa.launchpad.net hardy Release.gpg                       
Ign http://ppa.launchpad.net hardy/main Translation-en_GB            
Ign http://ppa.launchpad.net hardy Release.gpg 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB
Hit http://archive.ubuntu.com hardy/restricted Translation-en_GB     
Hit http://archive.ubuntu.com hardy/universe Translation-en_GB       
Hit http://archive.ubuntu.com hardy/multiverse Translation-en_GB     
Hit http://archive.ubuntu.com hardy-updates Release.gpg              
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_GB   
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_GB
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Get: 1 http://ppa.launchpad.net hardy Release [27.6kB]               
Hit http://wine.budgetdedicated.com hardy Release                    
Hit http://archive.ubuntu.com hardy-backports Release.gpg            
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_GB
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_GB
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_GB
Get: 2 http://ppa.launchpad.net hardy Release [27.6kB]               
Get: 3 http://ppa.launchpad.net hardy Release [27.6kB]               
Get: 4 http://ppa.launchpad.net hardy Release [27.6kB]               
Get: 5 http://ppa.launchpad.net hardy Release [27.6kB]               
Ign http://wine.budgetdedicated.com hardy/main Packages              
Hit http://archive.ubuntu.com hardy-security Release.gpg
Ign http://archive.ubuntu.com hardy-security/main Translation-en_GB
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://archive.ubuntu.com hardy-proposed Release.gpg
Ign http://ppa.launchpad.net hardy/main Packages                     
Ign http://ppa.launchpad.net hardy/main Sources                      
Ign http://ppa.launchpad.net hardy/main Packages                     
Ign http://ppa.launchpad.net hardy/universe Packages                 
Ign http://ppa.launchpad.net hardy/main Packages                     
Hit http://wine.budgetdedicated.com hardy/main Sources               
Hit http://archive.ubuntu.com hardy-proposed/restricted Translation-en_GB
Hit http://archive.ubuntu.com hardy-proposed/main Translation-en_GB  
Hit http://archive.ubuntu.com hardy-proposed/multiverse Translation-en_GB
Ign http://archive.ubuntu.com hardy-proposed/universe Translation-en_GB
Hit http://archive.ubuntu.com hardy Release                          
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://wine.budgetdedicated.com hardy/main Packages              
Hit http://archive.ubuntu.com hardy-updates Release                  
Hit http://archive.ubuntu.com hardy-backports Release
Hit http://archive.ubuntu.com hardy-security Release
Ign http://ppa.launchpad.net hardy/main Packages                    
Hit http://archive.ubuntu.com hardy-proposed Release
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/universe Packages
Hit http://archive.ubuntu.com hardy/main Packages                   
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://archive.ubuntu.com hardy-updates/universe Sources
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/main Sources
Hit http://archive.ubuntu.com hardy-backports/restricted Sources
Hit http://archive.ubuntu.com hardy-backports/universe Sources
Hit http://archive.ubuntu.com hardy-backports/multiverse Sources
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://archive.ubuntu.com hardy-proposed/main Packages
Hit http://archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/universe Packages
Hit http://archive.ubuntu.com hardy-proposed/restricted Sources
Hit http://archive.ubuntu.com hardy-proposed/main Sources
Hit http://archive.ubuntu.com hardy-proposed/multiverse Sources
Hit http://archive.ubuntu.com hardy-proposed/universe Sources
Fetched 5B in 2s (2B/s)  
Reading package lists... Done
ian@Jupiter-Ubuntu:~$ 
```

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) hardy main universe
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) hardy main

---

### Post by Nossie on 2008-10-12
le sigh :-| 

I thought I could skip the problem with the new kernel release but its still bringing up the same error... I'd really rather not have to pave and rebuild because of such a small issue but I'm running out of options here

---

### Post by Pumalite on 2008-10-12
Try:
sudo apt-get clean
sudo apt-get autoremove
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Nossie on 2008-10-12
```
ian@Jupiter-Ubuntu:~$ sudo apt-get clean
sudo: unable to resolve host Jupiter-Ubuntu
[sudo] password for ian: 
ian@Jupiter-Ubuntu:~$ sudo apt-get autoremove
sudo: unable to resolve host Jupiter-Ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-image
 linux-restricted-modules-2.6.24-21-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@Jupiter-Ubuntu:~$ sudo dpkg --configure -a
sudo: unable to resolve host Jupiter-Ubuntu
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-restricted-modules-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-image
ian@Jupiter-Ubuntu:~$ sudo apt-get -f install
sudo: unable to resolve host Jupiter-Ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-image
 linux-restricted-modules-2.6.24-21-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@Jupiter-Ubuntu:~$ sudo apt-get update
sudo: unable to resolve host Jupiter-Ubuntu
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_GB               
Hit http://gb.archive.ubuntu.com hardy Release.gpg                             
Hit http://gb.archive.ubuntu.com hardy/main Translation-en_GB                  
Hit http://archive.canonical.com hardy Release                                 
Hit http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB            
Hit http://gb.archive.ubuntu.com hardy/universe Translation-en_GB              
Hit http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB            
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB          
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB    
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB      
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB    
Hit http://gb.archive.ubuntu.com hardy-backports Release.gpg                   
Ign http://gb.archive.ubuntu.com hardy-backports/main Translation-en_GB        
Ign http://gb.archive.ubuntu.com hardy-backports/restricted Translation-en_GB  
Ign http://gb.archive.ubuntu.com hardy-backports/universe Translation-en_GB    
Ign http://gb.archive.ubuntu.com hardy-backports/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com hardy-security Release.gpg                    
Ign http://gb.archive.ubuntu.com hardy-security/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com hardy-security/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com hardy-security/universe Translation-en_GB     
Ign http://gb.archive.ubuntu.com hardy-security/multiverse Translation-en_GB   
Hit http://gb.archive.ubuntu.com hardy-proposed Release.gpg                    
Hit http://gb.archive.ubuntu.com hardy-proposed/restricted Translation-en_GB
Hit http://wine.budgetdedicated.com hardy Release.gpg              
Ign http://wine.budgetdedicated.com hardy/main Translation-en_GB   
Ign http://ppa.launchpad.net hardy Release.gpg                     
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Ign http://ppa.launchpad.net hardy/universe Translation-en_GB                  
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Hit http://gb.archive.ubuntu.com hardy-proposed/main Translation-en_GB         
Hit http://gb.archive.ubuntu.com hardy-proposed/multiverse Translation-en_GB   
Ign http://gb.archive.ubuntu.com hardy-proposed/universe Translation-en_GB     
Hit http://gb.archive.ubuntu.com hardy Release                                 
Hit http://gb.archive.ubuntu.com hardy-updates Release                         
Hit http://gb.archive.ubuntu.com hardy-backports Release                       
Hit http://gb.archive.ubuntu.com hardy-security Release                        
Hit http://gb.archive.ubuntu.com hardy-proposed Release                        
Hit http://wine.budgetdedicated.com hardy Release                              
Get: 1 http://ppa.launchpad.net hardy Release [27.6kB]                         
Hit http://archive.canonical.com hardy/partner Packages             
Hit http://archive.canonical.com hardy/partner Sources              
Get: 2 http://ppa.launchpad.net hardy Release [27.6kB]              
Hit http://gb.archive.ubuntu.com hardy/main Packages                
Get: 3 http://ppa.launchpad.net hardy Release [27.6kB]              
Get: 4 http://ppa.launchpad.net hardy Release [27.6kB]              
Get: 5 http://ppa.launchpad.net hardy Release [27.6kB]              
Hit http://gb.archive.ubuntu.com hardy/restricted Packages          
Hit http://gb.archive.ubuntu.com hardy/restricted Sources           
Hit http://gb.archive.ubuntu.com hardy/main Sources                 
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources           
Hit http://gb.archive.ubuntu.com hardy/universe Sources             
Ign http://ppa.launchpad.net hardy/main Packages                    
Ign http://ppa.launchpad.net hardy/main Sources                     
Hit http://gb.archive.ubuntu.com hardy/universe Packages            
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Ign http://ppa.launchpad.net hardy/main Packages                   
Ign http://ppa.launchpad.net hardy/universe Packages               
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages       
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages   
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources    
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources          
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Sources    
Hit http://gb.archive.ubuntu.com hardy-updates/universe Sources      
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages     
Ign http://ppa.launchpad.net hardy/main Packages                     
Ign http://ppa.launchpad.net hardy/main Packages                     
Ign http://ppa.launchpad.net hardy/main Packages                     
Ign http://ppa.launchpad.net hardy/main Sources                      
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages   
Hit http://gb.archive.ubuntu.com hardy-backports/main Packages       
Ign http://wine.budgetdedicated.com hardy/main Packages              
Hit http://gb.archive.ubuntu.com hardy-backports/restricted Packages 
Hit http://gb.archive.ubuntu.com hardy-backports/universe Packages   
Hit http://gb.archive.ubuntu.com hardy-backports/multiverse Packages 
Hit http://gb.archive.ubuntu.com hardy-backports/main Sources        
Hit http://gb.archive.ubuntu.com hardy-backports/restricted Sources  
Hit http://gb.archive.ubuntu.com hardy-backports/universe Sources    
Hit http://gb.archive.ubuntu.com hardy-backports/multiverse Sources  
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://ppa.launchpad.net hardy/main Sources                      
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://wine.budgetdedicated.com hardy/main Sources               
Hit http://gb.archive.ubuntu.com hardy-security/main Packages        
Hit http://gb.archive.ubuntu.com hardy-security/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-security/restricted Sources
Hit http://gb.archive.ubuntu.com hardy-security/main Sources
Hit http://gb.archive.ubuntu.com hardy-security/multiverse Sources
Hit http://ppa.launchpad.net hardy/universe Packages                 
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://wine.budgetdedicated.com hardy/main Packages              
Hit http://gb.archive.ubuntu.com hardy-security/universe Sources     
Hit http://gb.archive.ubuntu.com hardy-security/universe Packages
Hit http://gb.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-proposed/main Packages
Hit http://gb.archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://gb.archive.ubuntu.com hardy-proposed/universe Packages
Hit http://gb.archive.ubuntu.com hardy-proposed/restricted Sources
Hit http://gb.archive.ubuntu.com hardy-proposed/main Sources
Hit http://gb.archive.ubuntu.com hardy-proposed/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy-proposed/universe Sources
Fetched 5B in 1s (4B/s)  
Reading package lists... Done
ian@Jupiter-Ubuntu:~$ sudo apt-get dist-upgrade
sudo: unable to resolve host Jupiter-Ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-21-generic (2.6.24-21.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-21-generic; however:
  Package linux-ubuntu-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.24.21.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-21-generic; however:
  Package linux-restricted-modules-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-image-generic
 linux-image
 linux-restricted-modules-2.6.24-21-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ian@Jupiter-Ubuntu:~$ 

```

The most frustrating thing is that when there are other updates... those install fine

---

### Post by Pumalite on 2008-10-12
Check /var/lib/dpkg/status
See the condition of the package

---

### Post by chongzv08 on 2008-10-12
BFV **[gate Valve](http://www.valvesupplier.net/)** also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT . the website:[www.valvesupplier.net](http://www.valvesupplier.net)

---

### Post by Nossie on 2008-10-12
sorry, check it for what? I tried looking up 'linux-restricted-modules-generic' but its only referenced to by jockey-common ...

not sure what else I'm meant to be checking the status of?

---

### Post by Pumalite on 2008-10-12
When there is no other solution; sometimes one can 'cheat' apt-get.
A package that in status appears as not installed can be changed to:
install...ok...installed. That allows you to install other programs.

---

