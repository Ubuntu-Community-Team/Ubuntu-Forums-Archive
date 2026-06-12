---
title: "Unable to upgrate to Ubuntu 10.10 from Lucid 10.4"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by Goroman on 2011-02-06
Hi all, I am following the steps marked here [https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades) to upgrade ubuntu, everything looks ok until it comes to calculating the upgrade.

I get this error:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Anyone can help?

Best/

---

### Post by Goroman on 2011-02-06
> **Goroman said:**
> Hi all, I am following the steps marked here [https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades) to upgrade ubuntu, everything looks ok until it comes to calculating the upgrade.

I get this error:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Anyone can help?

Best/

Any feedback?

---

### Post by kansasnoob on 2011-02-06
Go to Synaptic and check for broken packages or go to terminal, run this command and post the output here:

```
sudo apt-get -f install
```

---

### Post by Goroman on 2011-02-06
> **kansasnoob said:**
> Go to Synaptic and check for broken packages or go to terminal, run this command and post the output here:

```
sudo apt-get -f install
```

I am getting this
goro@goro-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-22 libglew1.5 linux-headers-2.6.32-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
goro@goro-laptop:~$ ^C
goro@goro-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libglew1.5 linux-headers-2.6.32-22 linux-headers-2.6.32-22-generic
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 85.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 266093 files and directories currently installed.)
Removing libglew1.5 ...
Removing linux-headers-2.6.32-22-generic ...
Removing linux-headers-2.6.32-22 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


I removed the useless packages.

How do I proceed?

---

### Post by kansasnoob on 2011-02-06
Post the output of:

```
sudo apt-get update
```

---

### Post by Goroman on 2011-02-06
> **kansasnoob said:**
> Post the output of:

```
sudo apt-get update
```

It would be this:

goro@goro-laptop:~$ sudo apt-get update
[sudo] password for goro: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en      
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-es
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/main Translation-en             
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-es      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-es
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-es
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-es  
Hit [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/main Translation-es             
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en       
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-es       
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en       
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-es       
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [737B]                    
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en         
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/universe Translation-es
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-es
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-es
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-es
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages         
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-es
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted i386 Packages
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-es
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid Release 
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/main Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/restricted Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/universe Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/main i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/restricted i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/universe i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/multiverse i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/main i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/restricted i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/universe i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/multiverse i386 Packages
Fetched 2,281B in 3s (646B/s)
Reading package lists... Done

---

### Post by kansasnoob on 2011-02-06
You'll probably need to uncheck the Google pack repo in Software sources:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing%20&%20Disabling%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing%20&%20Disabling%20Repositories)

---

### Post by Goroman on 2011-02-06
> **kansasnoob said:**
> You'll probably need to uncheck the Google pack repo in Software sources:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing%20&%20Disabling%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing%20&%20Disabling%20Repositories)

I removed and run sudo apt-get update again, this is what I get:

goro@goro-laptop:~$ sudo apt-get update
[sudo] password for goro: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-es
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-es
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-es
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid Release.gpg
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/main Translation-en   
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-es
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-es
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Hit [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/main Translation-es   
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-es
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-es
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid/universe Translation-es
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-es
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-es
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted i386 Packages
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-es
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse i386 Packages
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-es
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid Release
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates Release
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/main Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/restricted Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/universe Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/main i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/restricted i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/universe i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid/multiverse i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/main i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/restricted i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/universe i386 Packages
Hit [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) lucid-updates/multiverse i386 Packages
Reading package lists... Done

---

### Post by ebasa on 2011-02-06
Question is why would you want to? 10.04 is LTS which means it will still be supported long after 10.10 is forgotten. No new features to speak of.

---

### Post by puzzlepaint on 2011-02-09
I got the same error and for me the solution was to run this:
```
sudo apt-get purge xserver-xorg-video-nouveau
```as recommended at the bottom of this page:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/614993](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/614993)

---

### Post by jfl on 2011-02-09
> **ebasa said:**
> Question is why would you want to? 10.04 is LTS which means it will still be supported long after 10.10 is forgotten. No new features to speak of.

One reason would be because you can only upgrade one version at a time; cannot go from 10.04 to 11.04.

Another reason is: "Because it's there":p

---

### Post by allenbina on 2011-02-14
> **puzzlepaint said:**
> I got the same error and for me the solution was to run this:
```
sudo apt-get purge xserver-xorg-video-nouveau
```as recommended at the bottom of this page:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/614993](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/614993)

worked like a charm

---

### Post by Carterclan on 2011-02-14
> **puzzlepaint said:**
> I got the same error and for me the solution was to run this:
```
sudo apt-get purge xserver-xorg-video-nouveau
```as recommended at the bottom of this page:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/614993](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/614993)


Yep worked for me also :)

---

### Post by Murdoc_of_puts on 2011-02-15
I have no idea why, but the purge work-arround works, I'm upgrading now.

---

### Post by johnDonson on 2011-02-17
Thanks guys! The purge thing works like a charm. How do you find these workarounds? ;)

---

