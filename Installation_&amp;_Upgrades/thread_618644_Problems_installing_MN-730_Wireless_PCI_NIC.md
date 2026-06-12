---
title: "Problems installing MN-730 Wireless PCI NIC"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by ivan8r on 2007-11-20
I just installed Ubuntu Studio 7.10 Gutsy Gibbon on an older P3 tower I had laying around. I would like to use my wireless NIC (Microsoft MN-730). 

I discovered ndiswrapper software, and I'm trying to get that installed since it seems to be the most promising way to get drivers installed for my NIC. I've followed the installation directions and I am having a problem with kernel headers.

When I try to make, I get the following error:

```
Cannot find kernel version in /lib/modules/2.6.22-14-rt/build, is it configured? Stop.
```

I'm pretty new to linux, so I'm not sure what to do. I've looked at some other posts on this subject, but I haven't found anything that seems to help. What should I try next?

---

### Post by Pumalite on 2007-11-20
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

---

### Post by ivan8r on 2007-11-20
When I tried those commands I got the following responses:

```
sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential
```
```
sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-headers-2.6.22-14-rt
```

---

### Post by Pumalite on 2007-11-20
Check your /etc/apt/sources.list. Make sure you have all the repos enabled.
Post the output of:
sudo apt-get update

---

### Post by ivan8r on 2007-11-20
Here's the output of sudo apt-get update:

```
Err http://us.archive.ubuntu.com gutsy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/restricted Translation-en_US         
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/restricted Translation-en_US  
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/universe Translation-en_US    
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/universe Translation-en_US           
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/multiverse Translation-en_US  
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US         
  Could not resolve 'us.archive.ubuntu.com'
Ign http://security.ubuntu.com gutsy-security Release                       
Err http://us.archive.ubuntu.com gutsy-updates Release.gpg                  
  Could not resolve 'us.archive.ubuntu.com'
Ign http://security.ubuntu.com gutsy-security/main Packages                 
Err http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US       
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/main Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/multiverse Translation-en_US
Err http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US  
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/restricted Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/universe Translation-en_US
Err http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US    
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US  
  Could not resolve 'us.archive.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy Release                               
Ign http://us.archive.ubuntu.com gutsy-updates Release                       
Ign http://security.ubuntu.com gutsy-security/restricted Packages            
Ign http://security.ubuntu.com gutsy-security/main Sources                   
Ign http://security.ubuntu.com gutsy-security/restricted Sources             
Ign http://security.ubuntu.com gutsy-security/universe Packages              
Ign http://security.ubuntu.com gutsy-security/universe Sources               
Ign http://security.ubuntu.com gutsy-security/multiverse Packages            
Ign http://security.ubuntu.com gutsy-security/multiverse Sources             
Ign http://us.archive.ubuntu.com gutsy/main Packages                         
Ign http://us.archive.ubuntu.com gutsy/restricted Packages
Err http://security.ubuntu.com gutsy-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/main Sources
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/universe Sources                          
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy/main Sources                                     
Err http://security.ubuntu.com gutsy-security/multiverse Packages                       
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy/restricted Sources                               
Err http://security.ubuntu.com gutsy-security/multiverse Sources                        
  Could not resolve 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com gutsy/universe Packages                                
Ign http://us.archive.ubuntu.com gutsy/universe Sources      
Ign http://us.archive.ubuntu.com gutsy/multiverse Packages   
Ign http://us.archive.ubuntu.com gutsy/multiverse Sources    
Ign http://us.archive.ubuntu.com gutsy-updates/main Packages 
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Ign http://us.archive.ubuntu.com gutsy-updates/main Sources  
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Ign http://us.archive.ubuntu.com gutsy-updates/universe Packages
Ign http://us.archive.ubuntu.com gutsy-updates/universe Sources
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Err http://us.archive.ubuntu.com gutsy/main Packages         
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/restricted Packages   
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/main Sources          
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/restricted Sources    
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/universe Packages     
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

It looks like it was trying to grab files off of the internet. I can't get connected until this NIC is working.

---

### Post by Pumalite on 2007-11-20
You have a bad connection and/or a messed up sources list. There is a site in the Web where you can regenerate your sources.list if necessary.(sorry, I don't have the link)

---

