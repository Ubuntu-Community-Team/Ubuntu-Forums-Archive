---
title: "Ubuntu11.10 doesn't boot after window 7 installation"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-10-29
I have installed windows7 after ubuntu 11.10 was installed, now I can not boot linux.
I had she same problem before then some body in forum send me this
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && gksu boot-repair

but now when I run this I get the following errors.
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && gksu boot-repair.


ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && gksu boot-repairYou are about to add the following PPA to your system:
 Boot-Repair
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.YyKuvHMJlD --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 3C48D16124B50277AF10D27F32B18A1260D8DA0B
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric InRelease                      
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US             
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]                     
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [28.2 kB]             
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]          
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,748 B]                                  
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release [40.8 kB]                                
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages [14.3 kB]                   
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [1,111 B]                            
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages [14 B]                   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [14.3 kB]              
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]                      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [72 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages [1,112 B]                        
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release [32.4 kB]                           
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [1,112 B]                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                   
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [9,267 B]                        
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en [14 B]               
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages [1,226 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en   
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted amd64 Packages [8,261 B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex [3,289 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex [2,263 B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main amd64 Packages [109 kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted amd64 Packages [14 B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages [109 kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages [14 B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [70 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en [57.5 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Fetched 2,904 kB in 4s (617 kB/s)                                 
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/Release  Unable to find expected entry 'restricted/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && gksu boot-repair^C

---

### Post by garvinrick4 on 2011-10-29
Run These in your Live CD or USB.
```
sudo fdisk -l 
```(lower case L)
Pick out your linux install.
I will use sda5 for this [COLOR=Red]you use your own.[/COLOR]
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```
Boot into Ubuntu
```
sudo update-grub
```Now will have both Ubuntu and windows as menu entrys in boot loader. (grub2)

---

### Post by hoboy on 2011-10-29
> **garvinrick4 said:**
> Run These in your Live CD or USB.
```
sudo fdisk -l 
```(lower case L)
Pick out your linux install.
I will use sda5 for this [COLOR=Red]you use your own.[/COLOR]
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```
Boot into Ubuntu
```
sudo update-grub
```Now will have both Ubuntu and windows as menu entrys in boot loader. (grub2)

Thanks it worked.

---

