---
title: "After Install Problem with Update"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Zoja on 2008-05-26
Hi i've just installed the 8.04 version of Ubuntu 

and i've got an automatic update of some packages ... and to my amusement it failed with some of them 

if i try to install anything it gives me also the same error's

here are the packages :
 foomatic-filters 
 linux-image-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-generic
 linux-generic

what should i do ?

---

### Post by Pumalite on 2008-05-26
Copy and paste here the complete output of:
sudo apt-get update
sudo apt-get upgrade

---

### Post by Zoja on 2008-05-26
sudo apt-get update : 

```
Hit http://pl.archive.ubuntu.com hardy Release.gpg
Ign http://pl.archive.ubuntu.com hardy/main Translation-en_US              
Ign http://pl.archive.ubuntu.com hardy/restricted Translation-en_US         
Ign http://pl.archive.ubuntu.com hardy/universe Translation-en_US           
Ign http://pl.archive.ubuntu.com hardy/multiverse Translation-en_US         
Hit http://pl.archive.ubuntu.com hardy-updates Release.gpg                  
Ign http://pl.archive.ubuntu.com hardy-updates/main Translation-en_US       
Ign http://pl.archive.ubuntu.com hardy-updates/restricted Translation-en_US 
Ign http://pl.archive.ubuntu.com hardy-updates/universe Translation-en_US   
Ign http://pl.archive.ubuntu.com hardy-updates/multiverse Translation-en_US 
Hit http://pl.archive.ubuntu.com hardy Release                              
Hit http://pl.archive.ubuntu.com hardy-updates Release                      
Hit http://pl.archive.ubuntu.com hardy/main Packages                        
Hit http://pl.archive.ubuntu.com hardy/restricted Packages          
Hit http://pl.archive.ubuntu.com hardy/main Sources                 
Hit http://pl.archive.ubuntu.com hardy/restricted Sources           
Hit http://pl.archive.ubuntu.com hardy/universe Packages            
Hit http://pl.archive.ubuntu.com hardy/universe Sources             
Hit http://pl.archive.ubuntu.com hardy/multiverse Packages          
Hit http://pl.archive.ubuntu.com hardy/multiverse Sources           
Hit http://security.ubuntu.com hardy-security Release.gpg           
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://pl.archive.ubuntu.com hardy-updates/main Packages
Hit http://pl.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://pl.archive.ubuntu.com hardy-updates/main Sources
Hit http://pl.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://pl.archive.ubuntu.com hardy-updates/universe Packages
Hit http://pl.archive.ubuntu.com hardy-updates/universe Sources
Hit http://pl.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://pl.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Reading package lists... Done

```

sudo apt-get upgrade :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.17.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Pumalite on 2008-05-26
Try:
sudo apt-get -f install

---

### Post by Zoja on 2008-05-26
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.17.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Pumalite on 2008-05-26
sudo dpkg --configure linux-restricted-modules-generic

---

### Post by Zoja on 2008-05-27
```
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-generic
```

---

### Post by zvacet on 2008-05-27
```
sudo dpkg --configure linux-image-2.6.24-17-generic
```

rest should follow.

---

### Post by Zoja on 2008-05-27
nope , still not the case , 
output:
```
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 linux-image-2.6.24-17-generic

```

---

### Post by Zoja on 2008-05-27
can anybody help me ?

---

### Post by zvacet on 2008-05-27
```
sudo dpkg --configure -a
```

---

### Post by Zoja on 2008-05-27
```
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.17.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-generic
 linux-generic

```

---

### Post by Zoja on 2008-05-27
May it be caused by my AMD64 and the Ubuntu i386 version "disagreement" ?

---

### Post by NeoFax on 2008-05-27
I have the same problem and do not have a amd64 chip.  It is due to receiving error 10 during the update of grub.

---

### Post by Zoja on 2008-05-28
so is there a way to fix this ?

---

### Post by FSalem on 2008-05-28
Any update about to so fix this issue ? same thing happen with me on HP Pavilion dv6000

---

### Post by NeoFax on 2008-06-01
Zoja; What version of grub are you using?

---

### Post by Zoja on 2008-06-02
I'm using 2.6.24-16-generic

---

### Post by VenKamikaze on 2008-06-28
Hi,

Came across this problem recently after having some HDD issues - not really sure how it happened though.
I got around it by modifying the /etc/kernel-img.conf and commenting out these two lines:
postinst_hook = update-grub
postrm_hook   = update-grub

so they now read:
#postinst_hook = update-grub
#postrm_hook   = update-grub

After doing this I re-ran 'dpkg --configure -a' twice (as linux-kernel-img only configured near the middle of the list of dependencies that required it), but you can probably just instead re-run: 'apt-get upgrade' once.

NOTE: that if you do this, your /boot/grub/menu.lst file will NOT be updated after installing a new linux kernel, you will have to manually edit this file to boot a new kernel, if you wish to. In my case, I was upgrading from 2.6.24-16-server to 2.6.24-19-server, so I backed up menu.lst first:
cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Then opened /boot/grub/menu.lst and copied these 5 lines near the end of the file:

title           Ubuntu 8.04, kernel 2.6.24-16-server
root            (hd3,1)
kernel          /boot/vmlinuz-2.6.24-16-server root=UUID=e95451a7-27ff-4f45-8276-675a703792d0 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-server
quiet

and pasted and then modified it to read:

title           Ubuntu 8.04, kernel 2.6.24-19-server
root            (hd3,1)
kernel          /boot/vmlinuz-2.6.24-19-server root=UUID=e95451a7-27ff-4f45-8276-675a703792d0 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-server
quiet

Be VERY CAREFUL modifying your /boot/grub/menu.lst as a mistake could render your system UNBOOTABLE. If this happens you'll have to boot a liveCD of some type, mount the partition with grub on it, and copy your /boot/grub/menu.lst.old back over the top of /boot/grub/menu.lst

Good luck.

PS. Another, better way to do this might be to run 'update-grub' manually and generate your own new /boot/grub/menu.lst file as I _think_ that's the file causing this trouble. You'll need to know what you're doing to do this successfully though.

---

