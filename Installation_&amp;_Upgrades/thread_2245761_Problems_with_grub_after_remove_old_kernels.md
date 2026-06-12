---
title: "Problems with grub after remove old kernels"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by Luis_Silva on 2014-09-25
Good Nights from Mexico, I need your help. Delete some old kernel and after reboot my lap-top gives me an error like this 

[http://gyazo.com/3b75ac965315cbefae25bcdc9cfd447d](http://gyazo.com/3b75ac965315cbefae25bcdc9cfd447d) 

Just that my machine is toshiba and here shows a Samsung .. 

I went back to configure grub from a bootable usb but I did not solve the problem, right now I just try to boot-repair application and this is the file that I generate.

[http://paste.ubuntu.com/8429733/](http://paste.ubuntu.com/8429733/)
 
  Thank you for your help

---

### Post by Luis_Silva on 2014-09-26
I need their help to recover my system.

---

### Post by oldfred on 2014-09-26
Did the Ubuntu install not finish correctly?

All you grub entries seem to be missing the initrd line which is normally right after the linux line.

Do not reinstall without fully backing up Windows first. I think bug is with UEFI and you are BIOS, but auto installer may say it is overwriting Ubuntu but erases entire drive. Only use Something Else or manual install if you decide to reinstall.

You may need to chroot into your system from the live installer and run sudo dpkg &#8211;reconfigure.

Boot-Repair may in effect run that if you run the full un-install and reinstall of grub as that may also add the latest kernel and run updates. I would try that first.

These are mostly just showing a manual uninstall & reinstall of grub, but when in the chroot you can run any commands on your installed system.

 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

      
 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

### Post by Luis_Silva on 2014-09-27
hello oldfred
  Thanks for your help.
  just now perform Reinstall Grub 2 from the Live CD with chroot
  all goes well, without any error, but when I restart my machine still does not load any kernel, and still receive the same error

this is what I did

sudo fdisk -l
sudo mount -t ext4 /dev/sda3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-mkconfig -o /boot/grub/grub.cfg

grub-install /dev/sda
sudo grub-install --recheck /dev/sda

unmount all mounted partitions

sudo reboot

What else can I do?

---

### Post by oldfred on 2014-09-27
You need to download kernel and run repairs.
Did you run the additional commands I posted particularly?

apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

### Post by Luis_Silva on 2014-09-27
Sorry. How I can download and run the kernel?

and I got back to try this look by adding the commands that tell me

and when I'm like
sudo chroot / mnt

apt-get autoclean
apt-get update
apt-get upgrade
apt-get dist-upgrade
f install apt-get
dpkg --configure -a

and then

grub-or-mkconfig /boot/grub/grub.cfg

grub-install /dev/sda
--recheck sudo grub-install /dev/sda

unmount all mounted partitions

sudo reboot

but it still the same error checking :(

---

### Post by oldfred on 2014-09-27
the apt-get  dist-upgrade should have downloaded a new kernel.

Are you getting any error messages?

If not you can also run this which should download newest kernel. 
You may need to rerun the other command as you did in post #6.

 sudo apt-get install linux-image

---

### Post by Luis_Silva on 2014-09-27
[B]This just did oldfred

```
ubuntu@ubuntu:~$ sudo fdisk -l[/B]

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x3a762216

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2         3074048  1051647999   524286976    7  HPFS/NTFS/exFAT
/dev/sda3      1051650048  1211650047    80000000   83  Linux
/dev/sda4      1211652094  1465147391   126747649    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1211652096  1463148543   125748224   83  Linux
/dev/sda6      1463150592  1465147391      998400   82  Linux swap / Solaris

Disk /dev/sdb: 7803 MB, 7803174912 bytes
255 heads, 63 sectors/track, 948 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xccd4ebea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15240512     7620225    b  W95 FAT32

```[B]
```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo chroot /mnt

root@ubuntu:/# apt-get autoclean[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done

**root@ubuntu:/# apt-get update**
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports InRelease                    
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]             
Get:3 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring InRelease                                  
Get:4 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty Release                                
Get:5 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates Release [59.7 kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [45.3 kB]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:7 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports Release [59.7 kB]          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/main Sources                           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-es                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/restricted Sources                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [10.8 kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [700 B]   
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [144 kB] 
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [14 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [48.9 kB]
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [1,148 B]
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [136 kB]  
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/main Translation-en                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/main Translation-es                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/multiverse Translation-es              
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [48.8 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/restricted Translation-es              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,398 B]
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.6 kB]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/universe Translation-es                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:21 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/main Sources [121 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:22 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/restricted Sources [1,408 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:23 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/universe Sources [85.1 kB]  
Get:24 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/multiverse Sources [3,527 B]
Get:25 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/main amd64 Packages [324 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-es                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:26 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [5,820 B]
Get:27 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/universe amd64 Packages [205 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Get:28 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [9,373 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:29 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/main i386 Packages [318 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:30 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:31 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [11.5 kB]           
Get:32 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/universe i386 Packages [206 kB]
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [11.5 kB]            
Get:34 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,545 B]
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/main Translation-en            
Get:35 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [4,157 B]           
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:36 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/main Sources [4,760 B]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:37 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/restricted Sources [14 B] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:38 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/universe Sources [13.3 kB]
Get:39 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/multiverse Sources [1,315 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:40 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/main amd64 Packages [6,356 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:41 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [14 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:42 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/universe amd64 Packages [16.5 kB]
Get:43 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [943 B]
Get:44 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/main i386 Packages [6,379 B]
Get:45 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:46 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/universe i386 Packages [16.5 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:47 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [945 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) trusty/universe Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-es
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-es
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-es
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-es
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-es
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-es
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-es
Fetched 2,023 kB in 1min 13s (27.7 kB/s)
Reading package lists... Done

**root@ubuntu:/# apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  xautomation
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**root@ubuntu:/# apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  xautomation
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**root@ubuntu:/# apt-get install linux-image **
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image is a virtual package provided by:
  linux-image-3.13.0-36-lowlatency 3.13.0-36.63
  linux-image-3.13.0-36-generic 3.13.0-36.63
  linux-image-3.13.0-35-lowlatency 3.13.0-35.62
  linux-image-3.13.0-35-generic 3.13.0-35.62
  linux-image-3.13.0-34-lowlatency 3.13.0-34.60
  linux-image-3.13.0-34-generic 3.13.0-34.60
  linux-image-3.13.0-33-lowlatency 3.13.0-33.58
  linux-image-3.13.0-33-generic 3.13.0-33.58
  linux-image-3.13.0-32-lowlatency 3.13.0-32.57
  linux-image-3.13.0-32-generic 3.13.0-32.57
  linux-image-3.13.0-30-lowlatency 3.13.0-30.55
  linux-image-3.13.0-30-generic 3.13.0-30.55
  linux-image-3.13.0-29-lowlatency 3.13.0-29.53
  linux-image-3.13.0-29-generic 3.13.0-29.53
  linux-image-3.13.0-27-lowlatency 3.13.0-27.50
  linux-image-3.13.0-27-generic 3.13.0-27.50
  linux-image-3.13.0-24-lowlatency 3.13.0-24.47
  linux-image-3.13.0-24-generic 3.13.0-24.47
You should explicitly select one to install.

E: Package 'linux-image' has no installation candidate
**root@ubuntu:/# apt-get install linux-image-3.13.0-36-generic 3.13.0-36.63**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.13.0-36.63
E: Couldn't find any package by regex '3.13.0-36.63'

**root@ubuntu:/# apt-get install linux-image-3.13.0-36-generic 3.13.0-34.60**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.13.0-34.60
E: Couldn't find any package by regex '3.13.0-34.60'

**root@ubuntu:/# apt-get install linux-image-3.13.0-33-generic 3.13.0-33.58**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.13.0-33.58
E: Couldn't find any package by regex '3.13.0-33.58'
root@ubuntu:/# f install apt-get
f: command not found

**root@ubuntu:/# apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  xautomation
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[B]root@ubuntu:/# dpkg --configure -a
 [/B]
**root@ubuntu:/# grub-mkconfig -o /boot/grub/grub.cfg**
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-33-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
done

**root@ubuntu:/# grub-install /dev/sda**
Installing for i386-pc platform.
Installation finished. No error reported.
root@ubuntu:/# sudo grub-install --recheck /dev/sda
^[[Dsudo: unable to resolve host ubuntu
Installing for i386-pc platform.
Installation finished. No error reported.

**root@ubuntu:/# exit**

**ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt**
**ubuntu@ubuntu:~$ sudo reboot**

```
but it still the same error checking :sad:

---

### Post by oldfred on 2014-09-27
I tried adding code tags, but something about the bolded line confuses it and it adds extra. But please use code tags for longer text output.

I think this line:
[FONT=arial]apt-get install linux-image-3.13.0-36-generic 3.13.0-36.63
Should be just this: it is looking then for the chars after the space  3.13.0.36.63 which does not exist.
apt-get install linux-image-3.13.0-36-generic

But I still do not know why your updates are not working. 

I found this:
[/FONT]  SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist 
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)
"If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."

If not rerun Boot-Info report and post new link. Maybe it is something else now?

[FONT=arial][/FONT]

---

### Post by Luis_Silva on 2014-09-28
thank you very much.

The solution was, as you indicated.
Install a kernel oldest, and with that I could enter my system
the next thing I did was uninstall and re-install kernels and everything went perfect ..

I thanks very much for your help

---

