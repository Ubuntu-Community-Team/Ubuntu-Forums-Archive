---
title: "Upgrade program error... I am doing my best.. but :("
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by agape0131 on 2008-12-01
I did my best to fix the problem in my upgrade program error.. but it doesn't seem to work so well. Help please!

(Reading database ... 
dpkg: serious warning: files list file for package `samba-common' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb (--unpack):
 files list file for package `liblircclient0' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

What should I do?

---

### Post by cdtech on 2008-12-01
Have you tried to run:
```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by agape0131 on 2008-12-01
Yes I have ... and this is what is shown:

jiwon@ubuntu:~$ sudo dpkg --configure -a && sudo apt-get -f install
[sudo] password for jiwon: 
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing linux-generic (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ...
Running depmod.
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/sound/core/snd-page-alloc.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/sound/core/snd-hwdep.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-tea6330t.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-i2c.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/tp_smapi.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/fsam7400.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/dm-bbr.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/appleir.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/lmpcm_usb.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/ov511/ov511_decomp.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/ov511/ov518_decomp.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-9-generic/kernel/ubuntu/lirc/lirc_ttusbir/lirc_ttusbir.ko is not an elf object
Failed to run depmod
dpkg: error processing linux-image-2.6.27-9-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-emailmerge:
 openoffice.org-emailmerge depends on python-uno; however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-emailmerge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-9-generic:
 linux-restricted-modules-2.6.27-9-generic depends on linux-image-2.6.27-9-generic; however:
  Package linux-image-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 linux-generic
 openoffice.org-writer
 linux-image-2.6.27-9-generic
 python-uno
 openoffice.org-emailmerge
 linux-restricted-modules-2.6.27-9-generic

---

### Post by sandy8925 on 2008-12-02
I think you have to upgrade your openoffice core first. That seems to be the problem.Maybe the file it downloaded was corrupted or something.

---

### Post by cdtech on 2008-12-02
Have you tried to do an "update" or even try to re "upgrade". The package manager needs to see the incomplete packages so I'm thinking an update first.

---

### Post by agape0131 on 2008-12-02
I tried to re-install it, but it doesn't seem to work because this showed up in Synaptics:

E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb: files list file for package `liblircclient0' contains empty filename


Is there a way to just delete all the broken packages and reinstall them/ re-download them?
Actually this problem happened when I tried to upgrade those packages... and the update software itself broke down. So my add/remove is not working.....:(

I spent four hours on this... I am willing to spend more time on it, but I want to know how to solve the problem!

---

### Post by cdtech on 2008-12-02
Try this:
```
sudo apt-get autoclean && sudo apt-get autoremove
```
Then try the update:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by aslamsha on 2008-12-02
> **cdtech said:**
> Try this:
```
sudo apt-get autoclean && sudo apt-get autoremove
```
Then try the update:
```
sudo apt-get update && sudo apt-get upgrade
```

Hi,
I am also having a similar problem. I have also reported a bug : [#295004]("https://bugs.launchpad.net/ubuntu/+source/lcms/+bug/295004")

They had suggested to follow instructions at [#108189]("https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189"). But, it didn't help. Is there any solution for this?

I had tried the solution given by you but 
```
sudo apt-get autoremove
```
again throws the same errors.

---

### Post by agape0131 on 2008-12-02
Thank you so much for the help! I appreciate it so much.

So here is what I got from "sudo apt-get autoclean && sudo apt-get autoremove"

jiwon@ubuntu:~$ sudo apt-get autoclean && sudo apt-get autoremove
[sudo] password for jiwon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org-calc: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-math: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  python-uno: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
E: Unmet dependencies. Try using -f.




and here is what I got from "sudo apt-get update && sudo apt-get upgrade"

jiwon@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for jiwon: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org-calc: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-math: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
  python-uno: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but 1:2.4.1-11ubuntu2 is installed
E: Unmet dependencies. Try using -f.



So as I told, I tried "apt-get -f install"

and here it is:

jiwon@ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


I'll keep looking for answers as well..

---

### Post by mangkusapi on 2008-12-02
dear all,

maybe i have almost same problem about upgrading Linux. when start tyo running update there is an error in 
E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

what should i do? thanks b 4

---

