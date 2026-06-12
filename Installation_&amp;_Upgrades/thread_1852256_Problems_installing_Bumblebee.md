---
title: "Problems installing Bumblebee"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by TweFoju on 2011-09-29
Hi, so i read the OMG ubuntu on how to install the new Bumblebee here:

[http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/](http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/)


[LIST]
[*]**sudo apt-add-repository ppa:mj-casalogic/bumblebee**
[*]**sudo apt-get update && sudo apt-get install bumblebee**
[/LIST]
ok, i done both. this is my LOG:

> 
twefoju@Wils:~$ sudo apt-add-repository ppa:mj-casalogic/bumblebee
[sudo] password for twefoju: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 7B71FFE7D8F72DE5509A5FD3EC7305B5ECF7E0B3
gpg: requesting key ECF7E0B3 from hkp server keyserver.ubuntu.com
gpg: key ECF7E0B3: public key "Launchpad PPA for MrMEEE" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
twefoju@Wils:~$ sudo apt-get update && sudo apt-get install bumblebee
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty InRelease                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates InRelease             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty Release.gpg                   
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates Release.gpg                     
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,752 B]                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [3,072 B]          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Sources                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Sources                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages [4,211 B]   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse amd64 Packages     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main amd64 Packages   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe amd64 Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe TranslationIndex
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Translation-en_CA [10.1 kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Translation-en_CA [425 B]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_CA                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_CA            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 27.9 kB in 3s (8,642 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acpi-call-dkms virtualgl
The following NEW packages will be installed:
  acpi-call-dkms bumblebee virtualgl
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 1,596 kB of archives.
After this operation, 3,887 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/](http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/) natty/main acpi-call-dkms all 240611-1~natty [6,068 B]
Get:2 [http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/](http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/) natty/main virtualgl amd64 2.2.80-1~nattyubuntu4 [1,568 kB]
Get:3 [http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/](http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/) natty/main bumblebee amd64 2.2.0-1~nattyubuntu10 [21.7 kB]
Fetched 1,596 kB in 1s (898 kB/s)     
Selecting previously deselected package acpi-call-dkms.
(Reading database ... 160969 files and directories currently installed.)
Unpacking acpi-call-dkms (from .../acpi-call-dkms_240611-1~natty_all.deb) ...
Selecting previously deselected package virtualgl.
Unpacking virtualgl (from .../virtualgl_2.2.80-1~nattyubuntu4_amd64.deb) ...
Selecting previously deselected package bumblebee.
Unpacking bumblebee (from .../bumblebee_2.2.0-1~nattyubuntu10_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up acpi-call-dkms (240611-1~natty) ...

Creating symlink /var/lib/dkms/acpi-call/240611/source ->
                 /usr/src/acpi-call-240611

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-11-generic IGNORE_CC_MISMATCH=1 KDIR=/lib/modules/2.6.38-11-generic/build PWD=/var/lib/dkms/acpi-call/240611/build....
cleaning build area....

DKMS: build Completed.

acpi_call.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-11-generic/updates/dkms/

depmod....

DKMS: install Completed.
Setting up virtualgl (2.2.80-1~nattyubuntu4) ...
Setting up bumblebee (2.2.0-1~nattyubuntu10) ...
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in manual mode.

Setting up and Downloading Configuration... Please wait

(0%...15%...33%...50%...75%...100%)
lspci: -s: Invalid slot number
lspci: -s: Invalid slot number
FATAL: Module nvidia not found.
lspci: -s: Invalid slot number
lspci: -s: Invalid slot number
lspci: -s: Invalid slot number
/usr/bin/bumblebee-configuration: line 453: /usr/local/bin/bumblebee-disablecard: Permission denied
 Adding system startup for /etc/init.d/bumblebee ...
   /etc/rc0.d/K20bumblebee -> ../init.d/bumblebee
   /etc/rc1.d/K20bumblebee -> ../init.d/bumblebee
   /etc/rc6.d/K20bumblebee -> ../init.d/bumblebee
   /etc/rc2.d/S20bumblebee -> ../init.d/bumblebee
   /etc/rc3.d/S20bumblebee -> ../init.d/bumblebee
   /etc/rc4.d/S20bumblebee -> ../init.d/bumblebee
   /etc/rc5.d/S20bumblebee -> ../init.d/bumblebee
Adding user twefoju to group bumblebee
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
i think it failed at the end, it's saying Permission Denied, i dont know if that is bad or good..

and then Fatal error and all that, what did i do wrong there?

anyway, this is a fresh Install uBuntu 11.04 on Asus U36SD

so what am i supposed to do now? im confused

oh and also i create new profile there, and i choose the default one, i think it was something like YN, or NY or something

oh and i think when i did this command, the Nvidia Additional Driver was not activated, is that probably the case?

---

### Post by TweFoju on 2011-09-29
anyone? 

bump, really could use some help in knowing how to switch the VGA between Intel and nVidia

also after installing Bumblebee, now i have the experimental 3d support for Nvidia cards on the Additional Driver

should i activate that one or dont?

---

### Post by TweFoju on 2011-09-30
Never mind

i solved it anyways

solved

---

### Post by dirtylobster on 2011-11-28
Wouldn't hurt to tell people finding this thread by googling how you solved it..

---

