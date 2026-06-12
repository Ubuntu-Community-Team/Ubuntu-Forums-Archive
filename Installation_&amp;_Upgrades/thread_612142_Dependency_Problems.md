---
title: "Dependency Problems"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by stuart62 on 2007-11-13
Upgraded to Gutsy and every time i do an update I get an error status 1 message with Dependency Problems also my Totem player since upgrading just displays silhouettes in a reddish pink colour, other media players show videos correctly but Totem is default so have no option but to use it.

---

### Post by stuart62 on 2007-11-14
The Full message I get is:

E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

Get this when Update Manager updates every time

---

### Post by stuart62 on 2007-11-16
when doing a sudo apt-get -f install I get this:
stuart@stuart-laptop:~$ sudo apt-get -f install 
[sudo] password for stuart: 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  feisty-wallpapers libstlport5.1 libswfdec0.3 libflac++5c2 liboggflac3 
  libjack0.100.0-0 libpostproc0d libgpod1 libavformat0d 
  linux-headers-2.6.20-16-generic libslab0 linux-headers-2.6.20-16 
  feisty-session-splashes libavcodec0d libgs-esp8 libquicktime0 libgdiplus 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
4 not fully installed or removed. 
Need to get 0B of archives. 
After unpacking 0B of additional disk space will be used. 
Setting up acpid (1.0.4-5ubuntu8) ... 
 * Loading ACPI modules...                                               [ OK ]  
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed. 
dpkg: error processing acpid (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of acpi-support: 
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however: 
  Package acpid is not configured yet. 
dpkg: error processing acpi-support (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of powermanagement-interface: 
 powermanagement-interface depends on acpi-support (>= 0.17); however: 
  Package acpi-support is not configured yet. 
dpkg: error processing powermanagement-interface (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ubuntu-desktop: 
 ubuntu-desktop depends on acpi-support; however: 
  Package acpi-support is not configured yet. 
 ubuntu-desktop depends on acpid; however: 
  Package acpid is not configured yet. 
 ubuntu-desktop depends on powermanagement-interface; however: 
  Package powermanagement-interface is not configured yet. 
dpkg: error processing ubuntu-desktop (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 acpid 
 acpi-support 
 powermanagement-interface 
 ubuntu-desktop 
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Ex0dus36 on 2007-12-03
I have the same error message. and plus it happens when i try to install ktorrent or uninstall it.

---

### Post by shamrock_uk on 2008-01-06
What happens when you run ```
sudo aptitude remove --purge acpid && sudo aptitude install ubuntu-desktop
``` please?

---

### Post by stuart62 on 2008-01-07
> **shamrock_uk said:**
> What happens when you run ```
sudo aptitude remove --purge acpid && sudo aptitude install ubuntu-desktop
``` please?

I don't haven't run this as don't have the dependency problems anymore, however, still get problems playing video, always showing silhouettes in a reddish background. Have only had this problem since upgrading. Screenshots show image correctly.

---

### Post by zvacet on 2008-01-07
```
sudo apt-get install --reinstall acpid
```

---

### Post by stuart62 on 2008-01-08
> **zvacet said:**
> ```
sudo apt-get install --reinstall acpid
```

Just done that, no effect

---

### Post by PmDematagoda on 2008-01-08
Try:-
```
sudo dpkg --configure -a
```

---

