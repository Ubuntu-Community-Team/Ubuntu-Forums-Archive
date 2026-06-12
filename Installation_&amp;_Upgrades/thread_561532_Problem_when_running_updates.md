---
title: "Problem when running updates"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by tgcUbuntu on 2007-09-27
Recently when some new updates became available I did the "install updates" and got the following error:

(Reading database ... 155805 files and directories currently installed.)
Preparing to replace update-manager-core 1:0.59.23 (using .../update-manager-core_1%3a0.59.25_i386.deb) ...
Unpacking replacement update-manager-core ...
Preparing to replace update-manager 1:0.59.23 (using .../update-manager_1%3a0.59.25_all.deb) ...
Unpacking replacement update-manager ...
Setting up linux-image-2.6.20-16-generic (2.6.20-16.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Failed to symbolic-link boot/initrd.img-2.6.20-16-generic to initrd.img.
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 17
Setting up update-manager-core (0.59.25) ...

Setting up update-manager (0.59.25) ...

Errors were encountered while processing:
 linux-image-2.6.20-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.20-16-generic (2.6.20-16.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Failed to symbolic-link boot/initrd.img-2.6.20-16-generic to initrd.img.
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 17

After this failure the system still seems to work okay. I rebooted and it rebooted ok. Any idea what's causing this problem?

---

### Post by Pumalite on 2007-09-27
Post the output of:
sudo apt-get update

---

### Post by tgcUbuntu on 2007-09-27
Here it is. There doesn't seem to be any problem doing this.

sudo apt-get update 
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Get:3 [http://www.virtualbox.org](http://www.virtualbox.org) feisty Release.gpg [189B]            
Ign [http://www.virtualbox.org](http://www.virtualbox.org) feisty/non-free Translation-en_US                
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://www.virtualbox.org](http://www.virtualbox.org) feisty Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Ign [http://www.virtualbox.org](http://www.virtualbox.org) feisty/non-free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                   
Hit [http://www.virtualbox.org](http://www.virtualbox.org) feisty/non-free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 5B in 1s (4B/s)  
Reading package lists... Done

---

### Post by Pumalite on 2007-09-27
You are OK then.

---

