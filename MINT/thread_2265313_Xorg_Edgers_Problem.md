---
title: "Xorg Edgers Problem"
date: 2015-02-14
forum: MINT
---

### Post by jgrimes413 on 2015-02-14
help!!!


```
cynder@cynder-Inspiron-518 ~ $ su
Password: 
cynder-Inspiron-518 cynder # sudo add-apt-repository ppa:xorg-edgers/ppa
You are about to add the following PPA to your system:
 == Xorg packages fresh from git ==

Currently supported releases are Trusty/14.04, Utopic/14.10 and Utopic/15.04

* WARNING: Do not use this PPA with the precise X backport stacks, aka if you fresh install of 12.04.2 or newer. You can switch back to a compatible one by installing xserver-xorg-lts-precise instead if you do want to use these packages but horrible things will happen if you don't.

Be sure to revert this PPA before doing a release upgrade or the upgrade will not succeed. To revert to official packages, install the ppa-purge package and run "sudo ppa-purge xorg-edgers".

== Important notice ==

This PPA is currently meant to be used as a whole. Please do _not_ individually install packages from it, add it to your sources and let your package manager pull in every update. The packages here build against each other and compile different features based on whats available at build time. Do not assume that because it lets you install a DDX with just the driver and libdrm update that it will work.  These packages are made with scripts that use the the current packages as the base, so some dependencies can be wrong and your package manager will not resolve that for you.  If you want to individually install something from here, grab the source and rebuild it in your current environment instead.

** Please do not publish instructions for how to install from this archive without linking to this page! Anyone using packages from this archive is expected to read this page first and it is recommended to check back occasionally for notice on problems that may arise. **

** Please use ppa-purge to remove this PPA. It is *particularly* recommended to do this before upgrading to a new ubuntu release! **
 More info: [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.klziJB9BzI --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 8844C542
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpg: key 8844C542: public key "Launchpad PPA for xorg crack pushers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
cynder-Inspiron-518 cynder # sudo apt-get update
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca InRelease
Ign [http://extra.linuxmint.com](http://extra.linuxmint.com) rebecca InRelease                               
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca Release.gpg [198 B]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:2 [http://extra.linuxmint.com](http://extra.linuxmint.com) rebecca Release.gpg [198 B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Get:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca Release [24.1 kB]                  
Get:4 [http://extra.linuxmint.com](http://extra.linuxmint.com) rebecca Release [3,152 B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                         
Get:5 [http://extra.linuxmint.com](http://extra.linuxmint.com) rebecca/main amd64 Packages [7,902 B]         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Get:6 [http://extra.linuxmint.com](http://extra.linuxmint.com) rebecca/main i386 Packages [7,889 B]          
Get:7 [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/main amd64 Packages [32.8 kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release                           
Get:9 [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/upstream amd64 Packages [30.0 kB]  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:10 [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/import amd64 Packages [218 kB]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages                   
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages                 
Ign [http://extra.linuxmint.com](http://extra.linuxmint.com) rebecca/main Translation-en_US                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Ign [http://extra.linuxmint.com](http://extra.linuxmint.com) rebecca/main Translation-en                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Get:12 [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/main i386 Packages [32.1 kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:13 [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/upstream i386 Packages [30.0 kB]  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Get:14 [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/import i386 Packages [219 kB]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources [15.9 kB]                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages         
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [42.4 kB]           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse amd64 Packages         
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [42.1 kB]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [17.7 kB]           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US              
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/import Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/import Translation-en                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/main Translation-en_US               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/main Translation-en                  
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/upstream Translation-en_US           
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca/upstream Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Fetched 739 kB in 11s (63.3 kB/s)                                              
Reading package lists... Done
cynder-Inspiron-518 cynder # sudo apt-get install nvidia-340
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  libcuda1-340 nvidia-opencl-icd-340 nvidia-340-uvm
The following packages will be REMOVED:
  nvidia-331 nvidia-331-uvm
The following NEW packages will be installed:
  nvidia-340
0 upgraded, 1 newly installed, 2 to remove and 269 not upgraded.
Need to get 51.4 MB of archives.
After this operation, 84.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) trusty/main nvidia-340 amd64 340.76-0ubuntu1~xedgers14.04.1 [51.4 MB]
Fetched 51.4 MB in 8min 42s (98.4 kB/s)                                        
(Reading database ... 172968 files and directories currently installed.)
Removing nvidia-331-uvm (331.113-0ubuntu0.0.4) ...
Removing all DKMS Modules
Done.
Removing nvidia-331 (331.113-0ubuntu0.0.4) ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/nvidia-331-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-331-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
INFO:Disable nvidia-331
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
stop: Unknown instance: 
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-37-generic
Warning: No support for locale: en_US.utf8
Selecting previously unselected package nvidia-340.
(Reading database ... 172712 files and directories currently installed.)
Preparing to unpack .../nvidia-340_340.76-0ubuntu1~xedgers14.04.1_amd64.deb ...
Unpacking nvidia-340 (340.76-0ubuntu1~xedgers14.04.1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up nvidia-340 (340.76-0ubuntu1~xedgers14.04.1) ...
update-alternatives: using /usr/lib/nvidia-340/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-340/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-340/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-340
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Adding system user `nvidia-persistenced' (UID 115) ...
Adding new group `nvidia-persistenced' (GID 124) ...
Adding new user `nvidia-persistenced' (UID 115) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-340-340.76 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-37-generic
Building for architecture x86_64
Building initial module for 3.13.0-37-generic
Done.

nvidia_340:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-37-generic/kernel/drivers/char/drm/

depmod....

DKMS: install completed.
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-37-generic
Warning: No support for locale: en_US.utf8
cynder-Inspiron-518 cynder # lspci -vnn | grep -i VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [GeForce GT 520] [10de:1040] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device [3842:1526]
    Subsystem: eVga.com. Corp. Device [3842:1526]
cynder-Inspiron-518 cynder # dpkg -l | grep fglrx
cynder-Inspiron-518 cynder # dpkg -l | grep nvidia
rc  nvidia-331                                  331.113-0ubuntu0.0.4                                amd64        NVIDIA binary driver - version 331.113
ii  nvidia-340                                  340.76-0ubuntu1~xedgers14.04.1                      amd64        NVIDIA binary driver - version 340.76
rc  nvidia-libopencl1-331                       331.113-0ubuntu0.0.4                                amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                       331.113-0ubuntu0.0.4                                amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.6.2linuxmint1                                     amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver
cynder-Inspiron-518 cynder # cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
cynder-Inspiron-518 cynder # cd cat /etc/X11/xorg.conf
bash: cd: cat: No such file or directory
cynder-Inspiron-518 cynder # sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GF119 [GeForce GT 520]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:44 memory:fb000000-fbffffff memory:c8000000-cfffffff memory:d6000000-d7ffffff ioport:af00(size=128) memory:d0000000-d007ffff
cynder-Inspiron-518 cynder #
```

---

### Post by Elfy on 2015-02-14
*Thread moved to **MINT**.*
Please do not hijack other people's threads - especially so if you're not even using the same OS.

---

### Post by mc4man on 2015-02-14
> **jgrimes413 said:**
> help!!!

With what?
If it's reading help then - 

> == Important notice ==

This PPA is currently meant to be used as a whole. Please do _not_ individually install packages from it, add it to your sources and let your package manager pull in every update. The packages here build against each other and compile different features based on whats available at build time. Do not assume that because it lets you install a DDX with just the driver and libdrm update that it will work.  These packages are made with scripts that use the the current packages as the base, so some dependencies can be wrong and your package manager will not resolve that for you.  If you want to individually install something from here, grab the source and rebuild it in your current environment instead.


---

