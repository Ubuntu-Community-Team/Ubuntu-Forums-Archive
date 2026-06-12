---
title: "Please help! : - ( error processing package linux-image-extra-3.13.0-24-generic"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by virginia2 on 2014-08-03
Hi, I get this message in the terminal. I tried everything but I am not able to fix it. Could somebody help me please? Thanks!):P:KS

Virginia

dpkg: error processing package linux-image-extra-3.13.0-24-generic (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 linux-image-extra-3.13.0-24-generic

---

### Post by coffeecat on 2014-08-03
Welcome to the forum!

Please tell us what terminal command gave you that error message. I'll assume you are running Ubuntu 14.04. Please confirm.

Assuming you were not in the middle of an upgrade from one release to another (it doesn't look like it), run this command and post the output:

```
sudo apt-get update
```

It will be lengthy. You can highlight with the mouse, right-click -> copy and then paste it into your post.

Once that has finished, post the output of this command:

```
sudo apt-get -s dist-upgrade
```

There have been four versions of the kernel later than 3.13.0-24 and probably the easiest thing to do is simply to install the latest kernel, skipping the -24 one. But before you do that it would be useful to see if there are any other problems revealed by the output of the above commands.

---

### Post by virginia2 on 2014-08-03
Thank you so much for answering me! I paste everything below. Virginia

Result of the command sudo apt-get update:
```

virginia@virginia-1015PEM:~$ sudo apt-get update
[sudo] password for virginia: 
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty InRelease
Hit [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty Release                                
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/main Sources                           
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/universe Sources                       
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/multiverse Sources                     
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/multiverse i386 Packages               
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/main Translation-en                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/restricted Translation-en              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59,7 kB]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/main Sources                   
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14,0 kB]                        
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/universe Sources             
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US              
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/main i386 Packages  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [25,2 kB]             
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/restricted Translation-en
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [36,3 kB]        
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty-backports/universe Translation-en      
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/main Translation-en_US        
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/restricted Translation-en_US  
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) trusty/universe Translation-en_US    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [8 431 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [697 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [115 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [39,1 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1 402 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Fetched 301 kB in 3s (77,1 kB/s)
Reading package lists... Done
```


Result for sudo apt-get -s dist-upgrade:
```

virginia@virginia-1015PEM:~$ sudo apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Conf linux-image-extra-3.13.0-24-generic (3.13.0-24.47 Ubuntu:14.04/trusty-updates [i386])
virginia@virginia-1015PEM:~$
```

---

### Post by virginia2 on 2014-08-03
And yes, I am running Ubuntu 14.04.

---

### Post by coffeecat on 2014-08-03
I was hoping that dist-upgrade would offer to install the latest kernel, bypassing the earlier broken package, but alas no! So...

Try this:

```
sudo apt-get --reinstall install linux-image-extra-3.13.0-24-generic 
```

If that errors, post the error output. If it completes happily, then try running this again:

```
sudo apt-get -s dist-upgrade
```

That won't actually do anything, the -s option is a simulate option. If it shows that it will install the 3.13.0-32 kernel packages now, then let it run without the -s option. It would best to get your system up-to-date.

---

### Post by virginia2 on 2014-08-03
I don't think I get error:

```
virginia@virginia-1015PEM:~$ sudo apt-get --reinstall install linux-image-extra-3.13.0-24-generic
[sudo] password for virginia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/37,0 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 161973 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-3.13.0-24-generic_3.13.0-24.47_i386.deb ...
Unpacking linux-image-extra-3.13.0-24-generic (3.13.0-24.47) over (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Setting up linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-24.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-24.47 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda2
done
```

And this is what happens when I try the second comman first with -s and then without:

```
virginia@virginia-1015PEM:~$ sudo apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
virginia@virginia-1015PEM:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
I think there is something wrong, am I right?

---

### Post by coffeecat on 2014-08-03
The first command does seem to have re-installed the broken 3.13.0-24 package, which hopefully has fixed the problem you started with. I guess my assumption was wrong that you also needed to install later kernels - I have 3.13.0-27, 3.13.0-29, 3.13.0-30, and 3.13.0-32 on my system - but perhaps they are already installed. I don't know why I made that assumption. The output of dist-upgrade certainly suggests that your system is up-to-date.

Reboot, and when you are back into the desktop, post the output of this command:

```
uname -a
```

That will tell us which kernel you are running.

---

### Post by virginia2 on 2014-08-03
Linux virginia-1015PEM 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux

Anyway, I think is fixed now! Thank you so much!!!

---

### Post by coffeecat on 2014-08-03
Yes, you have the 3.13.0-32 kernel, so everything seems to be up to date now.

Good luck!

---

