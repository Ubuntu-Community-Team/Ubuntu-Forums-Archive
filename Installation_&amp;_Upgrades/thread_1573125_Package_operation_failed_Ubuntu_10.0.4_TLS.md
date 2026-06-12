---
title: "Package operation failed Ubuntu 10.0.4 TLS"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by naveen9885 on 2010-09-12
I am receiving this error at the time of installation and un installation what to do pls help me.

Error: "Package operation failed "The installation or removal of a software package failed.

---

### Post by mörgæs on 2010-09-13
Try booting the machine and run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
```Do any messages appear?

---

### Post by naveen9885 on 2010-09-21
This is what i got and this is the error I got Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/a/adblock-plus/xul-ext-adblock-plus_1.1.3-1build1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/a/adblock-plus/xul-ext-adblock-plus_1.1.3-1build1_all.deb) Hash Sum mismatch. quoted below is what happed after trying all the 3 commands given above
> hero@hero-laptop:~$ sudo apt-get update
[sudo] password for hero: 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Reading package lists... Done
hero@hero-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt dpkg firefox firefox-branding firefox-gnome-support hpijs hplip
  hplip-data libhpmud0 libsmbclient libwbclient0 linux-headers-2.6.32-24
  linux-image-2.6.32-24-generic samba-common samba-common-bin smbclient
  winbind xulrunner-1.9.2
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
hero@hero-laptop:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
hero@hero-laptop:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
hero@hero-laptop:~$ 

---

### Post by plucky on 2010-09-21
> E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

That usually means you have two package managers open at the same time.

i.e [Synaptic Package manager,Update Manager or Aptitude or Apt-get] 

If you use those commands in a terminal,make sure other package managers are closed first.Even running "sudo apt-get update" and then sudo apt-get upgrade" can cause this problem.Give it a minute between commands.

Good luck

---

### Post by naveen9885 on 2010-09-21
I got this after closing all the update managers and software installation. help me out.

> hero@hero-laptop:~$ sudo apt-get update
[sudo] password for hero: 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Reading package lists... Done
hero@hero-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt dpkg firefox firefox-branding firefox-gnome-support hpijs hplip
  hplip-data libhpmud0 libsmbclient libwbclient0 linux-headers-2.6.32-24
  linux-image-2.6.32-24-generic samba-common samba-common-bin smbclient
  winbind xulrunner-1.9.2
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 100MB/102MB of archives.
After this operation, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main dpkg 1.15.5.6ubuntu4.3 [2,190kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main hplip-data 3.10.2-2ubuntu2.1 [11.6MB]
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image-2.6.32-24-generic 2.6.32-24.43 [31.5MB]
Get:4 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main apt 0.7.25.3ubuntu9.3 [1,815kB]
Get:5 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main firefox 3.6.10+build1+nobinonly-0ubuntu0.10.04.1 [11.3MB]
Get:6 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main smbclient 2:3.4.7~dfsg-1ubuntu3.2 [11.5MB]
Get:7 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main winbind 2:3.4.7~dfsg-1ubuntu3.2 [4,405kB]
Get:8 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main libsmbclient 2:3.4.7~dfsg-1ubuntu3.2 [1,663kB]
Get:9 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-24 2.6.32-24.43 [9,879kB]
Get:10 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main samba-common-bin 2:3.4.7~dfsg-1ubuntu3.2 [4,817kB]
Get:11 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main xulrunner-1.9.2 1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1 [9,380kB]
Fetched 100MB in 23min 31s (70.9kB/s)                                          
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.3_i386.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.10.2-2ubuntu2.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.10.2-2ubuntu2.1_all.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.3_i386.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.10+build1+nobinonly-0ubuntu0.10.04.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.10+build1+nobinonly-0ubuntu0.10.04.1_i386.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.7~dfsg-1ubuntu3.2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.7~dfsg-1ubuntu3.2_i386.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7~dfsg-1ubuntu3.2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7~dfsg-1ubuntu3.2_i386.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.7~dfsg-1ubuntu3.2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.7~dfsg-1ubuntu3.2_i386.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24_2.6.32-24.43_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24_2.6.32-24.43_all.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.7~dfsg-1ubuntu3.2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.7~dfsg-1ubuntu3.2_i386.deb)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1_i386.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
hero@hero-laptop:~$ 

---

### Post by CharlesA on 2010-09-21
Try updating the packages again at a later time. If it still happens, post back.

---

### Post by naveen9885 on 2010-09-21
This is what I got when I tried to update again by typing tis command sudo apt-get update.

> hero@hero-laptop:~$ sudo apt-get update
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN       
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Reading package lists... Done
hero@hero-laptop:~$ 


---

### Post by CharlesA on 2010-09-21
Did you edit the sources.list file manually?

---

### Post by slakkie on 2010-09-21
Try a different mirror:

```

sudo perl -p -i.orig -e 's/in.arch/pk.arch/' /etc/apt/sources.list
sudo aptitude update
sudo aptitude keep-all # this is because you used apt-get
sudo aptitude safe-upgrade

```

---

### Post by naveen9885 on 2010-09-21
This is what i got when I upgraded manually now what to do.Help me

> hero@hero-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt dpkg firefox firefox-branding firefox-gnome-support hpijs hplip
  hplip-data libhpmud0 libsmbclient libwbclient0 linux-headers-2.6.32-24
  linux-image-2.6.32-24-generic samba-common samba-common-bin smbclient
  winbind xulrunner-1.9.2
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 100MB/102MB of archives.
After this operation, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main dpkg 1.15.5.6ubuntu4.3 [2,190kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main hplip-data 3.10.2-2ubuntu2.1 [11.6MB]
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image-2.6.32-24-generic 2.6.32-24.43 [31.5MB]
Get:4 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main apt 0.7.25.3ubuntu9.3 [1,815kB]
Get:5 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main firefox 3.6.10+build1+nobinonly-0ubuntu0.10.04.1 [11.3MB]
Get:6 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main smbclient 2:3.4.7~dfsg-1ubuntu3.2 [11.5MB]
Get:7 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main winbind 2:3.4.7~dfsg-1ubuntu3.2 [4,405kB]
Get:8 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main libsmbclient 2:3.4.7~dfsg-1ubuntu3.2 [1,663kB]
Get:9 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-24 2.6.32-24.43 [9,879kB]
Get:10 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main samba-common-bin 2:3.4.7~dfsg-1ubuntu3.2 [4,817kB]
Get:11 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main xulrunner-1.9.2 1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1 [9,380kB]
Fetched 100MB in 23min 5s (72.2kB/s)                                           
Preconfiguring packages ...
(Reading database ... 148344 files and directories currently installed.)
Preparing to replace dpkg 1.15.5.6ubuntu4.1 (using .../dpkg_1.15.5.6ubuntu4.3_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
Setting up dpkg (1.15.5.6ubuntu4.3) ...

(Reading database ... 148344 files and directories currently installed.)
Preparing to replace hpijs 3.10.2-2ubuntu2 (using .../hpijs_3.10.2-2ubuntu2.1_i386.deb) ...
Unpacking replacement hpijs ...
Preparing to replace hplip 3.10.2-2ubuntu2 (using .../hplip_3.10.2-2ubuntu2.1_i386.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.10.2-2ubuntu2 (using .../libhpmud0_3.10.2-2ubuntu2.1_i386.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.10.2-2ubuntu2 (using .../hplip-data_3.10.2-2ubuntu2.1_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace linux-image-2.6.32-24-generic 2.6.32-24.42 (using .../linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-24-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Preparing to replace apt 0.7.25.3ubuntu9.1 (using .../apt_0.7.25.3ubuntu9.3_i386.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up apt (0.7.25.3ubuntu9.3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 148344 files and directories currently installed.)
Preparing to replace firefox-gnome-support 3.6.9+build1+nobinonly-0ubuntu0.10.04.1 (using .../firefox-gnome-support_3.6.10+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox-branding 3.6.9+build1+nobinonly-0ubuntu0.10.04.1 (using .../firefox-branding_3.6.10+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement firefox-branding ...
Preparing to replace firefox 3.6.9+build1+nobinonly-0ubuntu0.10.04.1 (using .../firefox_3.6.10+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace smbclient 2:3.4.7~dfsg-1ubuntu3.1 (using .../smbclient_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace winbind 2:3.4.7~dfsg-1ubuntu3.1 (using .../winbind_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb) ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Unpacking replacement winbind ...
Preparing to replace samba-common 2:3.4.7~dfsg-1ubuntu3.1 (using .../samba-common_2%3a3.4.7~dfsg-1ubuntu3.2_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace libwbclient0 2:3.4.7~dfsg-1ubuntu3.1 (using .../libwbclient0_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace libsmbclient 2:3.4.7~dfsg-1ubuntu3.1 (using .../libsmbclient_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace linux-headers-2.6.32-24 2.6.32-24.42 (using .../linux-headers-2.6.32-24_2.6.32-24.43_all.deb) ...
Unpacking replacement linux-headers-2.6.32-24 ...
Preparing to replace samba-common-bin 2:3.4.7~dfsg-1ubuntu3.1 (using .../samba-common-bin_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace xulrunner-1.9.2 1.9.2.9+build1+nobinonly-0ubuntu0.10.04.1 (using .../xulrunner-1.9.2_1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Removing obsolete conffile /etc/gre.d/1.9.2.9.system.conf ...
Unpacking replacement xulrunner-1.9.2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
Setting up crossplatformui (1.0.27) ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart acpid
acpid start/running, process 6970
package libqtgui4 exist
QT_VERSION = 4
cd: 156: can't cd to /usr/local/bin/ztemtApp/zteusbserial/2.6.32
dpkg: error processing crossplatformui (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libhpmud0 (3.10.2-2ubuntu2.1) ...

Setting up hpijs (3.10.2-2ubuntu2.1) ...

Setting up hplip-data (3.10.2-2ubuntu2.1) ...

Setting up hplip (3.10.2-2ubuntu2.1) ...
Creating/updating hplip user account...

Setting up linux-image-2.6.32-24-generic (2.6.32-24.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.42 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.42 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic

Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.2) ...

Setting up libwbclient0 (2:3.4.7~dfsg-1ubuntu3.2) ...

Setting up smbclient (2:3.4.7~dfsg-1ubuntu3.2) ...
Setting up winbind (2:3.4.7~dfsg-1ubuntu3.2) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 

Setting up libsmbclient (2:3.4.7~dfsg-1ubuntu3.2) ...

Setting up linux-headers-2.6.32-24 (2.6.32-24.43) ...
Setting up samba-common-bin (2:3.4.7~dfsg-1ubuntu3.2) ...

Setting up xulrunner-1.9.2 (1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: using /usr/bin/xulrunner-1.9.2 to provide /usr/bin/xulrunner (xulrunner) in auto mode.

Setting up firefox-branding (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...
Setting up firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Please restart all running instances of firefox, or you will experience problems.

Setting up firefox-gnome-support (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 crossplatformui
E: Sub-process /usr/bin/dpkg returned an error code (1)
hero@hero-laptop:~$ 


---

### Post by naveen9885 on 2010-09-21
I did not  edit it.> **CharlesA said:**
> Did you edit the sources.list file manually?

---

### Post by naveen9885 on 2010-09-21
Now the system was updated. But still receiving this error while uninstalling.

> installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 148345 files and directories currently installed.) 
Removing youtube-dl ... 
Processing triggers for man-db ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct 
Setting up crossplatformui (1.0.27) ... 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service acpid restart 
 
Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the restart(8) utility, e.g. restart acpid 
acpid start/running, process 2085 
package libqtgui4 exist 
QT_VERSION = 4 
cd: 156: can't cd to /usr/local/bin/ztemtApp/zteusbserial/2.6.32 
dpkg: error processing crossplatformui (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Errors were encountered while processing: 
 crossplatformui 
Setting up crossplatformui (1.0.27) ... 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service acpid restart 
 
Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the restart(8) utility, e.g. restart acpid 
acpid start/running, process 2143 
package libqtgui4 exist 
QT_VERSION = 4 
cd: 156: can't cd to /usr/local/bin/ztemtApp/zteusbserial/2.6.32 
dpkg: error processing crossplatformui (--configure): 
 subprocess installed post-installation script returned error exit status 2 


While Installing i got this error but software was installed what happend why this error coming.

> nstallArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Selecting previously deselected package tesseract-ocr-eng. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 148341 files and directories currently installed.) 
Unpacking tesseract-ocr-eng (from .../tesseract-ocr-eng_2.00-1_all.deb) ... 
Selecting previously deselected package tesseract-ocr. 
Unpacking tesseract-ocr (from .../tesseract-ocr_2.04-2_i386.deb) ... 
Selecting previously deselected package tucan. 
Unpacking tucan (from .../archives/tucan_0.3.9-1_all.deb) ... 
Processing triggers for man-db ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Rebuilding /usr/share/applications/desktop.en_IN.ISO8859-1.cache... 
WARNING: System locale is invalid 
Processing triggers for python-support ... 
Setting up crossplatformui (1.0.27) ... 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service acpid restart 
 
Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the restart(8) utility, e.g. restart acpid 
acpid start/running, process 2380 
package libqtgui4 exist 
QT_VERSION = 4 
cd: 156: can't cd to /usr/local/bin/ztemtApp/zteusbserial/2.6.32 
dpkg: error processing crossplatformui (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up tesseract-ocr-eng (2.00-1) ... 
Setting up tesseract-ocr (2.04-2) ... 
Setting up tucan (0.3.9-1) ... 
Errors were encountered while processing: 
 crossplatformui 
Setting up crossplatformui (1.0.27) ... 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service acpid restart 
 
Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the restart(8) utility, e.g. restart acpid 
acpid start/running, process 2439 
package libqtgui4 exist 
QT_VERSION = 4 
cd: 156: can't cd to /usr/local/bin/ztemtApp/zteusbserial/2.6.32 
dpkg: error processing crossplatformui (--configure): 
 subprocess installed post-installation script returned error exit status 2 


---

### Post by lenin.leishangthem on 2010-10-17
i recently upgraded ubuntu 10.04 to 10.10 beta and now when i updated or install new software i get the same error log.  
perlperl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C")..................

---

### Post by danielsouzat on 2010-10-26
I'm with the same problem. I tried ```
sudo dpkg-reconfigure locales
``` but it crashs every time.

---

### Post by mörgæs on 2010-10-27
If none of the advice in this thread works, then this one is a guaranteed solution:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

