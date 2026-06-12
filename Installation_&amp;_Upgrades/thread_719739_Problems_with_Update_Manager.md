---
title: "Problems with Update Manager"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by kiroro on 2008-03-09
Every time I run update manager, a pop-up window tells me: 'Not all updates can be installed', 'Partial Upgrade' etc. When I click 'Check' for new updates, an error message shows:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

So I run 'sudo dpkg --configure -a', i got this:

```
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of realplay:
 realplay depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing realplay (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

```


Then I tried 'sudo apt-get update', i got:

```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:2 http://packages.medibuntu.org gutsy Release.gpg [189B]         
Ign http://packages.medibuntu.org gutsy/free Translation-en_US               
Get:3 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US  
Hit http://packages.medibuntu.org gutsy Release                     
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]  
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com gutsy-security/main Packages          
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release 
Ign http://packages.medibuntu.org gutsy/free Packages                          
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://security.ubuntu.com gutsy-security/main Sources           
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Ign http://packages.medibuntu.org gutsy/non-free Packages            
Hit http://us.archive.ubuntu.com gutsy/main Packages                 
Hit http://us.archive.ubuntu.com gutsy/restricted Packages           
Hit http://us.archive.ubuntu.com gutsy/main Sources                  
Hit http://security.ubuntu.com gutsy-security/universe Packages      
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://packages.medibuntu.org gutsy/free Packages                
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://packages.medibuntu.org gutsy/non-free Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 4B in 1s (3B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```


Now I can't even install updates... How can I fix this? Thanks a lot for your help!

---

### Post by kiroro on 2008-03-16
Please help me..

---

### Post by diablo75 on 2008-03-17
I'm having the exact same problem!  I'm attempting to install Ubuntu (and the I tried Xubuntu, same problem happened) on an HP N3310.  It has an AMD K6-2, with about 180 megs of ram.

---

### Post by kiroro on 2008-03-19
I don't think it's related to the hardware...I have Q6600, 4G Ram. It did not happen at the beginning when I install Ubuntu.

---

### Post by Sef on 2008-03-19
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

From the terminal, type or copy this code:

```
sudo dpkg --configure -a
```

That should correct the problem.  Please report back if it does or does not.  Thank you.

---

