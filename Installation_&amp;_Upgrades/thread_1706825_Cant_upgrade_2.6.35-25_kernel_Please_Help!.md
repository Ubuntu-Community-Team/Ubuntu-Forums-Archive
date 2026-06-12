---
title: "Cant upgrade 2.6.35-25 kernel Please Help!"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by Sebde on 2011-03-14
Hello everybody!

I am quite a noob in linux so if anyone can help me I would very grateful. I dont know how to put this that somobody would understand my problem but here we go. I have problem like said in title.I am unable to upgrade my kernel. Sunaptics says that I have 2.6.35-28 installed. I tried to reinstall 2.6.35-28 via synaptics but it gives me error.

Thats what uname -a says:

pekka@pekka-laptop:~$ uname -a
Linux pekka-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

Tried to install 2.6.35-27 via terminal thats what I get:

```
pekka@pekka-laptop:~$ sudo apt-get install linux-image-2.6.35-27
[sudo] password for pekka: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-2.6.35-27-generic' for regex 'linux-image-2.6.35-27'
Note, selecting 'linux-image-2.6.35-27-generic-pae' for regex 'linux-image-2.6.35-27'
Note, selecting 'linux-image-2.6.35-27-virtual' for regex 'linux-image-2.6.35-27'
Suggested packages:
  fdutils linux-doc-2.6.35 linux-source-2.6.35 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.35-27-generic linux-image-2.6.35-27-generic-pae
  linux-image-2.6.35-27-virtual
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 79,3MB of archives.
After this operation, 241MB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/) maverick/main linux-image-2.6.35-27-generic i386 2.6.35-27.48+kamal~mjgbacklight1 [34,1MB]
Get:2 [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/) maverick/main linux-image-2.6.35-27-generic-pae i386 2.6.35-27.48+kamal~mjgbacklight1 [34,4MB]
Get:3 [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/) maverick/main linux-image-2.6.35-27-virtual i386 2.6.35-27.48+kamal~mjgbacklight1 [10,7MB]
Fetched 79,3MB in 5min 36s (236kB/s)                                           
Selecting previously deselected package linux-image-2.6.35-27-generic.
(Reading database ... 156237 files and directories currently installed.)
Unpacking linux-image-2.6.35-27-generic (from .../linux-image-2.6.35-27-generic_2.6.35-27.48+kamal~mjgbacklight1_i386.deb) ...
Done.
Selecting previously deselected package linux-image-2.6.35-27-generic-pae.
Unpacking linux-image-2.6.35-27-generic-pae (from .../linux-image-2.6.35-27-generic-pae_2.6.35-27.48+kamal~mjgbacklight1_i386.deb) ...
Done.
Selecting previously deselected package linux-image-2.6.35-27-virtual.
Unpacking linux-image-2.6.35-27-virtual (from .../linux-image-2.6.35-27-virtual_2.6.35-27.48+kamal~mjgbacklight1_i386.deb) ...
Done.
Setting up linux-image-2.6.35-28-generic (2.6.35-28.49+kamal~mjgbacklight3) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-28-generic-pae (2.6.35-28.49+kamal~mjgbacklight3) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-28-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-28-virtual (2.6.35-28.49+kamal~mjgbacklight3) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-28-virtual (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48+kamal~mjgbacklight1) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.35-27-generic-pae (2.6.35-27.48+kamal~mjgbacklight1) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-27-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.35-27-virtual (2.6.35-27.48+kamal~mjgbacklight1) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-27-virtual (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.35-28-generic
 linux-image-2.6.35-28-generic-pae
 linux-image-2.6.35-28-virtual
 linux-image-2.6.35-27-generic
 linux-image-2.6.35-27-generic-pae
 linux-image-2.6.35-27-virtual
E: Sub-process /usr/bin/dpkg returned an error code (1)
pekka@pekka-laptop:~$ 


Tried another way error again...:

pekka@pekka-laptop:~$ sudo apt-get install linux linux-image
[sudo] password for pekka: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-generic
The following packages will be REMOVED:
  linux-image-2.6.35-25-generic
The following NEW packages will be installed:
  linux linux-image linux-image-generic
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 16,3kB of archives.
After this operation, 107MB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/main linux-image-generic i386 2.6.35.28.36 [5*456B]
Get:2 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/main linux-image i386 2.6.35.28.36 [5*440B]
Get:3 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/main linux i386 2.6.35.28.36 [5*434B]
Fetched 16,3kB in 5s (3*195B/s)
(Reading database ... 161278 files and directories currently installed.)
Removing linux-image-2.6.35-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-25-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.35-25-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
pekka@pekka-laptop:~$ 
```


Anyone have any suggestions where to start solving this puzzle? Many thanks in advance!

---

### Post by uRock on 2011-03-14
Running **sudo apt-get update && sudo apt-get dist-upgrade** doesn't upgrade your kernel to the newest?

---

### Post by Sebde on 2011-03-14
Thank for your reply! But no that didn't work all I get is this:


```
pekka@pekka-laptop:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for pekka: 
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick Release.gpg
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Hit [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/main Translation-fi          
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Hit [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-fi    
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Hit [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-fi    
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Hit [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick/universe Translation-fi      
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-fi  
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-fi
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-fi
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-fi
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-fi   
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-fi
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-fi   
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-fi
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en          
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-fi
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-proposed Release.gpg                 
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en 
Hit [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-fi 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                         
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Hit [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-fi
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Hit [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-fi
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Hit [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-fi
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                      
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/) maverick/main Translation-fi
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-backports Release.gpg                
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-fi
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-fi
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-fi
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-fi
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-fi          
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-fi       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-fi
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-fi
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-fi
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates Release                      
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports Release                       
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-proposed Release                     
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-backports Release                    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-fi              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-fi          
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                     
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en       
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1*347B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-fi                
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/restricted i386 Packages             
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick/multiverse i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main Sources                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages                   
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted Sources           
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe Sources             
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse Sources           
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/main i386 Packages           
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports/main Sources                  
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports/restricted Sources            
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports/universe Sources              
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports/multiverse Sources            
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports/restricted i386 Packages      
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports/universe i386 Packages        
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) lucid-backports/multiverse i386 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-proposed/restricted i386 Packages    
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-proposed/main i386 Packages          
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages    
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-proposed/universe i386 Packages      
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-backports/restricted i386 Packages   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-backports/main i386 Packages         
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-backports/multiverse i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) maverick-backports/universe i386 Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1*070B]                  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-fi            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Fetched 2*686B in 4s (605B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 33,9MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-image-2.6.35-25-generic i386 2.6.35-25.44 [33,9MB]
Fetched 33,9MB in 2min 22s (238kB/s)                                           
Selecting previously deselected package linux-image-2.6.35-25-generic.
(Reading database ... 161279 files and directories currently installed.)
Preparing to replace linux-image-2.6.35-25-generic 2.6.35-25.44 (using .../linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.35-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48+kamal~mjgbacklight1) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-27-generic-pae (2.6.35-27.48+kamal~mjgbacklight1) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-27-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-27-virtual (2.6.35-27.48+kamal~mjgbacklight1) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-27-virtual (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.35-28-generic (2.6.35-28.49+kamal~mjgbacklight3) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.35-28-generic-pae (2.6.35-28.49+kamal~mjgbacklight3) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-28-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.35-28-virtual (2.6.35-28.49+kamal~mjgbacklight3) ...
Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-28-virtual (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.35-25-generic
 linux-image-2.6.35-27-generic
 linux-image-2.6.35-27-generic-pae
 linux-image-2.6.35-27-virtual
 linux-image-2.6.35-28-generic
 linux-image-2.6.35-28-generic-pae
 linux-image-2.6.35-28-virtual
E: Sub-process /usr/bin/dpkg returned an error code (1)
pekka@pekka-laptop:~$ uname -a
Linux pekka-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux
pekka@pekka-laptop:~$ 

```

Could there be something fishy in that sentence because this thing go wrong every time..? 

Running depmod.
sh: /usr/sbin/update-initramfs: not found
Failed to create initrd image.

---

### Post by oldos2er on 2011-03-14
Can you run **ls /usr/sbin/update-*** and post the output here?

---

### Post by Sebde on 2011-03-14
Sorry dont know how to take screenshot in ubuntu. Here is output:

```
pekka@pekka-laptop:~$ ls /usr/sbin/update-*
/usr/sbin/update-alternatives         
/usr/sbin/update-apt-xapian-index     
/usr/sbin/update-binfmts              
/usr/sbin/update-bootsystem-insserv   
/usr/sbin/update-ca-certificates      
/usr/sbin/update-catalog              
/usr/sbin/update-default-aspell       
/usr/sbin/update-default-ispell       
/usr/sbin/update-default-wordlist     
/usr/sbin/update-dictcommon-aspell    
/usr/sbin/update-dictcommon-hunspell  
/usr/sbin/update-fonts-alias          
/usr/sbin/update-fonts-dir            
/usr/sbin/update-fonts-scale         
/usr/sbin/update-grub                 
/usr/sbin/update-grub2                
/usr/sbin/update-gsfontmap
/usr/sbin/update-icon-caches
/usr/sbin/update-inetd
/usr/sbin/update-info-dir
/usr/sbin/update-initramfs
/usr/sbin/update-initramfs.old
/usr/sbin/update-locale
/usr/sbin/update-mime
/usr/sbin/update-openoffice-dicts
/usr/sbin/update-pangox-aliases
/usr/sbin/update-passwd
/usr/sbin/update-python-modules
/usr/sbin/update-rc.d
/usr/sbin/update-rc.d-insserv
/usr/sbin/update-software-center
/usr/sbin/update-usbids
/usr/sbin/update-xmlcatalog
pekka@pekka-laptop:~$ 
```



All of these are highlighted in blue:

/usr/sbin/update-alternatives
/usr/sbin/update-default-aspell
/usr/sbin/update-software-center


This one is highlighted in black (text is red)

/usr/sbin/update-initramfs

Cheers!

---

### Post by coffeecat on 2011-03-14
I find it rather worrying that in your apt-get output you have hits for maverick-proposed and lucid-backports. If you have enabled the proposed repository, I suggest you read this:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

In particular:

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.Post the output of:

```
cat /etc/apt/sources.list
```Please post this between [noparse]```
 and 
```[/noparse] tags for legibility.

---

### Post by Sebde on 2011-03-14
And here is the screenshot. :D

---

### Post by Sebde on 2011-03-14
Here we go. Should I now disable proposed and backports?


```
pekka@pekka-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-backports restricted main multiverse universe
pekka@pekka-laptop:~$
```

---

### Post by coffeecat on 2011-03-14
> **Sebde said:**
> Here we go. Should I now disable proposed and backports?

I think that would be a good idea. You have lines for both Maverick and Lucid backports, as well as Maverick proposed and Lucid partner in your sources.list. I wouldn't be surprised if that's causing some sort of inconsistency that's interfering with updates. Try and disable all of those in Synaptic > Settings > Repositories.  Then either click on reload in Synaptic or run 'sudo apt-get update' again. Then see if you can apply upgrades.

The latest regular Maverick kernel is 2.6.35-27, so I don't know where that Synaptic message about a 2.6.35-28 kernel comes from. Perhaps the -28 kernel is in the proposed repository which, for reasons I posted earlier, you'd be advised to avoid. Not all kernel upgrades tested in proposed get to be approved for release to normal updates.

---

### Post by Sebde on 2011-03-15
I disabled all of those in synaptic but theres no use. All I get is error. Do you have any idea how could I get rid of that 2.6.35-28? Now when I try to upgrade 2.6.35-25, 2.6.35-28 is upgraded also although it shouldn't be installed anymore and that gives error.

Is the any way to delete that kernel permanently? I have already tried via synaptics...

UPDATE!

I was able to remove other kernels from cd /boot by removing them manually using sudo rm and then updating grub. Now I get rid of those "ghost" kernels but I am still unable to update my kernel to 2.6.35-27. 

I get 2.6.35-27 to the grub boot menu but when i chose it, it gave me kernel panic and freeze. 2.6.35-25 is working allright though...

It seems that this system is trying to install new kernel update somewhere else but not on the top of old kernel. If you know what I mean? Any ideas?

---

### Post by thokchom on 2011-03-22
i have faced the same problem, unable to update/upgrade to generic 2.6.35.28, here is the errors/logs by giving the command apt-get update

~$ sudo apt-get upgrade
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@james-Presario:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@james-Presario:~$ sudo apt-get update
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg                         
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37), connection timed out
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release       
  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2)  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37), connection timed out

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/Release](http://in.archive.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by ppeterb on 2011-03-22
This is more "shared experience" than a fix - but maybe it'll help.

I use two 10.10 systems. Both created on the same day - one full desktop system and another configured for a special purpose. Most maintenance actions (e.g., run update manager) are done close to same time. Both have been backed up to usb flash using Remastersys and unetbootin, and restored to a dual-boot HD.

First - an odd patch keeps the restores from being complete. (I think the patch is 43disable_updateinitramfs ?) It decides the media is read-only, which is true, and then deletes update-initramfs script. I have no idea why, and defeating the patch doesn't work - it just keeps coming back like malware.

The work-around is to do the restore (internet disconnected) and then copy /user/sbin/update-initramfs.distrib without the .distrib.

Second - my problem. Both systems were restored to a brand new HD. One restore was correct and a long update was done without any errors. I screwed up the other 10.10 system restore and ran update manager before the update-initramfs fix. Just once. The kernel update failed because the update-initramfs script was not found.

Since then there have been two kernel updates installed correctly on the first 10.10 system. The other system ignores the kernel updates without any error reports, but takes other updates such as the daily Firefox betas without a grumble.

Nothing I've tried has unstuck this. I don't know what (if any) other updates maybe similarly omitted. All ideas appreciated.

---

