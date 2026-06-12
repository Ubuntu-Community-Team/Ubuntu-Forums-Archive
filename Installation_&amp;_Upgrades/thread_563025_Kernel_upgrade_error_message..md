---
title: "Kernel upgrade: error message."
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by NT4usB on 2007-09-29
I installed the updates today in Feisty.```
Upgraded the following packages:
app-install-data-commercial (7.2) to 7.3
libpq5 (8.2.4-0ubuntu0.7.04) to 8.2.5-0ubuntu0.7.04.1
libssl0.9.8 (0.9.8c-4build1) to 0.9.8c-4ubuntu0.1
linux-headers-2.6.20-16 (2.6.20-16.31) to 2.6.20-16.32
linux-headers-2.6.20-16-generic (2.6.20-16.31) to 2.6.20-16.32
linux-image-2.6.20-16-generic (2.6.20-16.31) to 2.6.20-16.32
linux-libc-dev (2.6.20-16.31) to 2.6.20-16.32
openssl (0.9.8c-4build1) to 0.9.8c-4ubuntu0.1
update-manager (1:0.59.23) to 1:0.59.25
update-manager-core (1:0.59.23) to 1:0.59.25
``` I got this error```
E: linux-image-2.6.20-16-generic: subprocess post-installation script returned error exit status 2
```
Anything to worry about?

---

### Post by Pumalite on 2007-09-29
Let's check. Post the output of:

sudo apt-get update

---

### Post by NT4usB on 2007-09-29
```
ct@dapperpvr:~$ sudo apt-get update
Password:
Get:1 http://medibuntu.sos-sts.com feisty Release.gpg [189B]        
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US              
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US
Hit http://medibuntu.sos-sts.com feisty Release
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security Release               
Ign http://medibuntu.sos-sts.com feisty/free Packages                
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages          
Hit http://us.archive.ubuntu.com feisty/main Sources                 
Hit http://security.ubuntu.com feisty-security/main Packages
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources             
Hit http://us.archive.ubuntu.com feisty/multiverse Packages          
Hit http://us.archive.ubuntu.com feisty/multiverse Sources           
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://medibuntu.sos-sts.com feisty/free Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://medibuntu.sos-sts.com feisty/non-free Sources
Fetched 4B in 2s (2B/s)  
Reading package lists... Done
```

---

### Post by Pumalite on 2007-09-29
You are OK. it seems.

---

### Post by NT4usB on 2007-09-30
Thanks,
I saw this in another post, with the same 'post the output of sudo apt-get update' , and the same looks OK.
What are we looking for that would tell us there was a problem?
This is the first time I have got an error upgrading the kernel.

---

### Post by Pumalite on 2007-09-30
I think, at least to me, would be to ensure I still have an apt-get that works and is not stuck.

---

### Post by NT4usB on 2007-09-30
Ok, I have had a broke apt-get before. 
I was more worried that the kernel didn't install properly...

---

### Post by Pumalite on 2007-09-30
If your kernel hadn't install properly, you wouldn't have been able to boot.

---

### Post by rdsii64 on 2007-09-30
> **NT4usB said:**
> ```
ct@dapperpvr:~$ sudo apt-get update
Password:
Get:1 http://medibuntu.sos-sts.com feisty Release.gpg [189B]        
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US              
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US
Hit http://medibuntu.sos-sts.com feisty Release
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security Release               
Ign http://medibuntu.sos-sts.com feisty/free Packages                
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages          
Hit http://us.archive.ubuntu.com feisty/main Sources                 
Hit http://security.ubuntu.com feisty-security/main Packages
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources             
Hit http://us.archive.ubuntu.com feisty/multiverse Packages          
Hit http://us.archive.ubuntu.com feisty/multiverse Sources           
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://medibuntu.sos-sts.com feisty/free Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://medibuntu.sos-sts.com feisty/non-free Sources
Fetched 4B in 2s (2B/s)  
Reading package lists... Done
```

how come some of those say hit and others say Ign??

---

### Post by NT4usB on 2007-10-09
Looks like apt-get (and synaptic) are still broke... I get:
E: linux-image-2.6.20-16-generic: subprocess post-installation script returned error exit status 2
and anything I install fails...

ed: /boot/ was too full. Two kernels and two backups of kernels didn't leave enough room for whatever hoodoo the kernel do when it installs stuff. 
Removed the backups and the old kernel and all is well. (until I reboot, then we'll see...)

---

