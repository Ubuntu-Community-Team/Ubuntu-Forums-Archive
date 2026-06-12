---
title: "/BOOT destroyed, VMLINUZ-, INITRD- all missing! how can I re-create them?"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by fizzybrain on 2008-11-25
Arg.
So in trying to install Ubuntu 8.10 alongside 8.04 I managed to completely wipe the bootloader partition which held both GRUB and my 8.04 /boot partition.

The GRUB got re-built, pointing to a /boot on my new 8.10 partition (I installed it without a separate /boot partiton). The 8.10 installation will boot (and crash and burn when trying to start X - but that's irrelevant ATM), and I can see the kernel and associated files, so I have a pretty good idea of what needs to be re-instated for my 8.04.

I think I have two courses open to me:
1 - locate the relevant files for 8.04, put them back in the bootloader partitition and get GRUB to point to them,
- or - 
2 - locate the relevant files for 8.04, put them in /boot on my 8.04 partition, and get GRUB to point to them

- I think I prefer option 2, but either way I still have to get hold of the kernel (and other files?)

Fortunately, a lot of the time I end up booting using GRUB4DOS, and the menu.lst is still intact and the relevant section looks something like:
========
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=69af626d-50ad-441e-bf67-f8998e6f25cd ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet
==========

I have never done anything like recomplile the kernel, so does that mean that I can get one from elsewhere and just drop it in? I have searched the 8.04 partition but couldn't find a copy anywhere - maybe it will be in an installation archive...?

Any thoughts (apart from "what a berk", etc.)?

Ian
(gibbering wreck)

---

### Post by caljohnsmith on 2008-11-25
So 8.04 is on sda2? If you want to install a kernel in the /boot directory in the 8.04 sda2 partition, you could do the following from either a Live CD or your 8.10 install:
```
sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
apt-get install linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic
```
And then continue with the following to reinstall Grub to sda2, and also recreate a menu.lst:
```
grub-install --recheck /dev/sda2
update-grub
ls -lR /boot
exit
```
Please post the output of all the above commands and we can work from there if you want. :)

---

### Post by fizzybrain on 2008-11-25
Cool, Thanks for that caljohnsmith, that look's promising.
I'll try it tomorrow though - it's 2AM where I am!

---

### Post by fizzybrain on 2008-11-26
Good morning!
Still awake? [- EDIT: I guess not, I'll be back at the offending machine at about 10PM UTC, which I think is 2PM where you are :-) ]
I have booted with an Ubuntu 7.10 live CD (the 8.04 CD I have seems to only want to install - not give me a live sesion)

I have followed the first steps - and they all make sense and seem to work - but when I do

    sudo chroot /mnt /bin/bash

I get

    chroot: cannot run command `/bin/bash': No such file or directory

/bin/bash seems to exist though and it seems to be executable

Thoughts?
Ian

---

### Post by caljohnsmith on 2008-11-26
So is sda2 your Hardy partition? How about posting:
```
sudo fdisk -lu
```
And if sda2 is your Hardy partition, please also post:
```
sudo mount /dev/sda2/ /mnt
ls -l /mnt
ls -l /mnt/bin/bash
```

---

### Post by fizzybrain on 2008-11-26
> **caljohnsmith said:**
> So 8.04 is on sda2? If you want to install a kernel in the /boot directory in the 8.04 sda2 partition, you could do the following from either a Live CD or your 8.10 install:
```
sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
apt-get install linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic
```

Sorry, I was being dense and using sda2
sda2 is the bootloader partition (with GRUB) which used to hold /boot
Hardy is on sda7

Using my (only just) working 8.10 system I did all those first steps (for sda7) and got:
```

root@aluminium:/# apt-get install linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.24-16-generic is already the newest version.
linux-image-2.6.24-16-generic is already the newest version.
linux-restricted-modules-2.6.24-16-generic is already the newest version.
linux-ubuntu-modules-2.6.24-16-generic is already the newest version.

```
?!
So are they still on my system then? I'm pretty sure 8.10 is not using that kernel....

I'm not sure how relevant this is now, but
sudo fdisk -lu gives
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb0dcb0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16097129     8048533+   7  HPFS/NTFS
/dev/sda2   *    16097130    16225649       64260   83  Linux
/dev/sda3        16225650   195173684    89474017+   f  W95 Ext'd (LBA)
/dev/sda5        16225713   166594049    75184168+   7  HPFS/NTFS
/dev/sda6       166594113   168345134      875511   83  Linux
/dev/sda7       168345198   180056519     5855661   83  Linux
/dev/sda8       180056583   180940094      441756   82  Linux swap / Solaris
/dev/sda9       189727713   195173684     2722986   17  Hidden HPFS/NTFS
/dev/sda10      180940158   189727649     4393746   83  Linux

Partition table entries are not in disk order

```

hmm?
(raises eyebrows expectantly)
ian

---

### Post by caljohnsmith on 2008-11-26
OK, while you are still chrooted into sda7, how about doing:
```
grub-install --recheck /dev/sda7
update-grub
ls -lR /boot
cat /boot/grub/menu.lst
exit
```
And please post the output of everything above.

---

### Post by fizzybrain on 2008-11-26
> **caljohnsmith said:**
> OK, while you are still chrooted into sda7, how about doing:
```
grub-install --recheck /dev/sda7
update-grub
ls -lR /boot
cat /boot/grub/menu.lst
exit
```
And please post the output of everything above.

That sound awfully permanent - won't that modify the system (and if so - how)?
I am currently running from the intrepid system (/ on sda10, /boot on sda10, bootloader on sda2)

---

### Post by caljohnsmith on 2008-11-26
> **fizzybrain said:**
> That sound awfully permanent - won't that modify the system (and if so - how?)?
All those commands do is reinstall Grub, because it is unclear whether you have Grub installed correctly on your sda7 partition. They shouldn't hurt anything, because the grub-install command will install Grub to the boot sector of sda7, not your MBR (Master Boot Record), so that your 8.10 partition will stay in charge of the boot process (i.e. 8.10's menu.lst gets loaded on start up). And the update-grub command will either update the menu.lst that you might have, or it will create a new menu.lst if you don't have one. I'm only trying to help you fix the problem, not make it worse. :)

---

### Post by fizzybrain on 2008-11-26
> **caljohnsmith said:**
> All those commands do is reinstall Grub, because it is unclear whether you have Grub installed correctly on your sda7 partition. ... I'm only trying to help you fix the problem, not make it worse. :)

:) I know you're trying to help , but remember you are battling against my not-inconsiderable talents for getting things wrong (I wasn't sure I had told you everything correctly).

Anyway, I knew that GRUB wasn't there on sda7 - the whole /boot directory was empty. I ran install / update-grub and it has installed GRUB on sda7. Finding nothing of interest to put in a menu it has created an "empty" menu.lst (i.e. just comments, no entries)

So I still need to find my kernel from somewhere, I think. Where o where shall it be?

Sorry, it's late - I think I'm going a bit peculiar.

Ian

```

root@aluminium:/# grub-install --recheck /dev/sda7                              
Probing devices to guess BIOS drives. This may take a long time.                
Searching for GRUB installation directory ... found: /boot/grub                 
Installation finished. No error reported.                                       
This is the contents of the device map /boot/grub/device.map.                   
Check if this is correct or not. If any of the lines is incorrect,              
fix it and re-run the script `grub-install'.                                    

(fd0)   /dev/fd0
(hd0)   /dev/sda
root@aluminium:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default       
Testing for an existing GRUB menu.lst file ...                 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y                                                          
Searching for splash image ... none found, skipping ...                         
grep: /boot/config*: No such file or directory                                  
Updating /boot/grub/menu.lst ... done                                           

root@aluminium:/# ls -lR /boot
/boot:                        
total 4                       
drwxr-xr-x 2 root root 4096 2008-11-27 02:19 grub

/boot/grub:
total 192  
-rw-r--r-- 1 root root    197 2008-11-27 02:16 default
-rw-r--r-- 1 root root     30 2008-11-27 02:16 device.map
-rw-r--r-- 1 root root   8056 2008-11-27 02:16 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-11-27 02:16 fat_stage1_5 
-rw-r--r-- 1 root root     16 2008-11-27 02:16 installed-version
-rw-r--r-- 1 root root   8608 2008-11-27 02:16 jfs_stage1_5     
-rw-r--r-- 1 root root   3756 2008-11-27 02:19 menu.lst         
-rw-r--r-- 1 root root   7324 2008-11-27 02:16 minix_stage1_5   
-rw-r--r-- 1 root root   9632 2008-11-27 02:16 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-27 02:16 stage1           
-rw-r--r-- 1 root root 108356 2008-11-27 02:16 stage2           
-rw-r--r-- 1 root root   9276 2008-11-27 02:16 xfs_stage1_5     
root@aluminium:/# cat /boot/grub/menu.lst                       
# menu.lst - See: grub(8), info grub, update-grub(8)            
#            grub-install(8), grub-floppy(8),                   
#            grub-md5-crypt, /usr/share/doc/grub                
#            and /usr/share/doc/grub-doc/.                      

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.              
#                                                                            
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.                          
# WARNING: If you are using dmraid do not use 'savedefault' or your           
# array will desync and will not let you boot your system.                    
default         0                                                             

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).                                          
timeout         3                                                              

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu                                             

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the  
# command 'lock'                                                              
# e.g. password topsecret                                                     
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/                        
# password topsecret                                                          

#
# examples
#         
# title         Windows 95/98/NT/2000
# root          (hd0,0)              
# makeactive                         
# chainloader   +1                   
#                                    
# title         Linux                
# root          (hd0,1)              
# kernel        /vmlinuz root=/dev/hda2 ro
#                                         

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options     
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.  
## e.g. kopt=root=/dev/hda1 ro                                    
##      kopt_2_6_8=root=/dev/hdc1 ro                              
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro                        
# kopt=root=UUID=69af626d-50ad-441e-bf67-f8998e6f25cd ro          

## Setup crashdump menu entries
## e.g. crashdump=1            
# crashdump=0                  

## default grub root device
## e.g. groot=(hd0,0)      
# groot=(hd0,1)            

## should update-grub create alternative automagic boot options
## e.g. alternative=true                                       
##      alternative=false                                      
# alternative=true                                             

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true                                 
##      lockalternative=false                                
# lockalternative=false                                      

## additional options to use with the default boot option, but not with the
## alternatives                                                            
## e.g. defoptions=vga=791 resume=/dev/hda5                                
# defoptions=quiet splash                                                  

## should update-grub lock old automagic boot options
## e.g. lockold=false                                
##      lockold=true                                 
# lockold=false                                      

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=                                                       

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0                                             

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single                     
# altoptions=(recovery mode) single                      

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by caljohnsmith on 2008-11-26
OK, so the /boot directory of sda7 is still empty of any kernels, so that's why the update-grub command didn't put any in your menu.lst. :) You probably unintentionally installed that 2.6.24-16-generic kernel into your 8.10 partition, not sda7. It would really help if you could post the output of all the commands from start to finish so I can try and catch things like that. :) How about trying again:
```
sudo mount /dev/sda7 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
apt-get install linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic
update-grub
cat /boot/grub/menu.lst
```
So if it's not too much trouble, please copy/paste the full terminal session of all the above commands so I can get a better idea of what happens.

---

### Post by fizzybrain on 2008-11-26
It did exactly the same as before - I don't get any output from the first commands (except to say that sda7 is already mounted from the previous time) , the only interesting bit is when I try to apt-get the kernel files, where it says it's already the newest version, just as before

```
ian@aluminium:/$ sudo mount /dev/sda7 /mnt
mount: /dev/sda7 already mounted or /mnt busy
mount: according to mtab, /dev/sda7 is already mounted on /mnt
ian@aluminium:/$ sudo mount --bind /dev /mnt/dev
ian@aluminium:/$ sudo mount --bind /proc /mnt/proc
ian@aluminium:/$ sudo mount --bind /sys /mnt/sys
ian@aluminium:/$ sudo chroot /mnt /bin/bash
root@aluminium:/# apt-get install linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic                                                               
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
linux-headers-2.6.24-16-generic is already the newest version.                  
linux-image-2.6.24-16-generic is already the newest version.                    
linux-restricted-modules-2.6.24-16-generic is already the newest version.       
linux-ubuntu-modules-2.6.24-16-generic is already the newest version.           
The following packages were automatically installed and are no longer required: 
  xserver-xorg-video-amd libdns32                                               
Use 'apt-get autoremove' to remove them.                                        
0 upgraded, 0 newly installed, 0 to remove and 251 not upgraded.                
root@aluminium:/# update-grub                                                   
Searching for GRUB installation directory ... found: /boot/grub                 
Searching for default file ... found: /boot/grub/default                        
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst       
Searching for splash image ... none found, skipping ...                         
grep: /boot/config*: No such file or directory                                  
Updating /boot/grub/menu.lst ... done                                           

root@aluminium:/# cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),       
#            grub-md5-crypt, /usr/share/doc/grub    
#            and /usr/share/doc/grub-doc/.          

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.              
#                                                                            
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.                          
# WARNING: If you are using dmraid do not use 'savedefault' or your           
# array will desync and will not let you boot your system.                    
default         0                                                             

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).                                          
timeout         3                                                              

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu                                             

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the  
# command 'lock'                                                              
# e.g. password topsecret                                                     
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/                        
# password topsecret                                                          

#
# examples
#         
# title         Windows 95/98/NT/2000
# root          (hd0,0)              
# makeactive                         
# chainloader   +1                   
#                                    
# title         Linux                
# root          (hd0,1)              
# kernel        /vmlinuz root=/dev/hda2 ro
#                                         

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options     
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.  
## e.g. kopt=root=/dev/hda1 ro                                    
##      kopt_2_6_8=root=/dev/hdc1 ro                              
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro                        
# kopt=root=UUID=69af626d-50ad-441e-bf67-f8998e6f25cd ro          

## Setup crashdump menu entries
## e.g. crashdump=1            
# crashdump=0                  

## default grub root device
## e.g. groot=(hd0,0)      
# groot=(hd0,1)            

## should update-grub create alternative automagic boot options
## e.g. alternative=true                                       
##      alternative=false                                      
# alternative=true                                             

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true                                 
##      lockalternative=false                                
# lockalternative=false                                      

## additional options to use with the default boot option, but not with the
## alternatives                                                            
## e.g. defoptions=vga=791 resume=/dev/hda5                                
# defoptions=quiet splash                                                  

## should update-grub lock old automagic boot options
## e.g. lockold=false                                
##      lockold=true                                 
# lockold=false                                      

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

### END DEBIAN AUTOMAGIC KERNELS LIST
root@aluminium:/#


```

---

### Post by caljohnsmith on 2008-11-26
OK, I think I see what is going on; 8.04 thinks you have that kernel all ready installed because it should be in your /boot partition, which unfortunately is no more. How about trying the following while you are chrooted in /mnt, and please post the output:
```
apt-get purge linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic                            
apt-get install linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic
ls -l /boot
```

---

### Post by fizzybrain on 2008-11-26
Uninstalling the kernel - ulp!

But hurrah! - it seems to have worked.

Now just to update grub and tinker with some menu.lst files...?
Tomorrow though - it's 3:30AM

```

root@aluminium:/# sudo apt-get purge linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic                                                            
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
The following packages were automatically installed and are no longer required: 
  xserver-xorg-video-amd libdns32                                               
Use 'apt-get autoremove' to remove them.                                        
The following packages will be REMOVED:                                         
  linux-headers-2.6.24-16-generic* linux-image-2.6.24-16-generic*               
  linux-restricted-modules-2.6.24-16-generic*                                   
  linux-ubuntu-modules-2.6.24-16-generic*                                       
0 upgraded, 0 newly installed, 4 to remove and 251 not upgraded.                
After this operation, 132MB disk space will be freed.                           
Do you want to continue [Y/n]? y                                                
(Reading database ... 142267 files and directories currently installed.)        
Removing linux-headers-2.6.24-16-generic ...                                    
Removing linux-restricted-modules-2.6.24-16-generic ...                         
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory                                                                           
Purging configuration files for linux-restricted-modules-2.6.24-16-generic ...  
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory                                                                           
Removing linux-ubuntu-modules-2.6.24-16-generic ...                             
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory                                                                           
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic                 
Purging configuration files for linux-ubuntu-modules-2.6.24-16-generic ...      
Removing linux-image-2.6.24-16-generic ...                                      
Running postrm hook script /sbin/update-grub.                                   
Searching for GRUB installation directory ... found: /boot/grub                 
Searching for default file ... found: /boot/grub/default                        
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst       
Searching for splash image ... none found, skipping ...                         
grep: /boot/config*: No such file or directory                                  
Updating /boot/grub/menu.lst ... done                                           

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz     
 you may need to re-run your boot loader[grub]
The link /vmlinuz.old is a damaged link       
Removing symbolic link vmlinuz.old            
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link        
Removing symbolic link initrd.img             
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link    
Removing symbolic link initrd.img.old         
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.24-16-generic ...
Running postrm hook script /sbin/update-grub.                    
Searching for GRUB installation directory ... found: /boot/grub  
Searching for default file ... found: /boot/grub/default         
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...                  
grep: /boot/config*: No such file or directory                           
Updating /boot/grub/menu.lst ... done                                    

root@aluminium:/# sudo apt-get install linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic                                                          
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
The following packages were automatically installed and are no longer required: 
  xserver-xorg-video-amd libdns32                                               
Use 'apt-get autoremove' to remove them.                                        
Suggested packages:                                                             
  linux-doc-2.6.24 linux-source-2.6.24 avm-fritz-firmware-2.6.24-16 nvidia-glx  
  nvidia-glx-legacy nvidia-glx-new                                              
The following NEW packages will be installed:                                   
  linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic                 
  linux-restricted-modules-2.6.24-16-generic                                    
  linux-ubuntu-modules-2.6.24-16-generic                                        
0 upgraded, 4 newly installed, 0 to remove and 251 not upgraded.                
Need to get 41.5MB of archives.                                                 
After this operation, 132MB of additional disk space will be used.              
Get:1 http://gb.archive.ubuntu.com hardy/main linux-image-2.6.24-16-generic 2.6.24-16.30 [18.4MB]                                                               
Get:2 http://gb.archive.ubuntu.com hardy/main linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.23 [4617kB]                                                      
Get:3 http://gb.archive.ubuntu.com hardy/main linux-headers-2.6.24-16-generic 2.6.24-16.30 [642kB]                                                              
Get:4 http://gb.archive.ubuntu.com hardy/restricted linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34 [17.9MB]                                         
Fetched 41.5MB in 6min56s (99.7kB/s)                                            
Selecting previously deselected package linux-image-2.6.24-16-generic.          
(Reading database ... 134101 files and directories currently installed.)        
Unpacking linux-image-2.6.24-16-generic (from .../linux-image-2.6.24-16-generic_2.6.24-16.30_i386.deb) ...                                                      
Done.                                                                           
Selecting previously deselected package linux-ubuntu-modules-2.6.24-16-generic. 
Unpacking linux-ubuntu-modules-2.6.24-16-generic (from .../linux-ubuntu-modules-2.6.24-16-generic_2.6.24-16.23_i386.deb) ...                                    
Selecting previously deselected package linux-headers-2.6.24-16-generic.        
Unpacking linux-headers-2.6.24-16-generic (from .../linux-headers-2.6.24-16-generic_2.6.24-16.30_i386.deb) ...                                                  
Selecting previously deselected package linux-restricted-modules-2.6.24-16-generic.
Unpacking linux-restricted-modules-2.6.24-16-generic (from .../linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb) ...
Setting up linux-image-2.6.24-16-generic (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-16-generic
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done


Setting up linux-ubuntu-modules-2.6.24-16-generic (2.6.24-16.23) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

Setting up linux-headers-2.6.24-16-generic (2.6.24-16.30) ...

Setting up linux-restricted-modules-2.6.24-16-generic (2.6.24.12-16.34) ...

root@aluminium:/# ls -l /boot
total 18736
-rw-r--r-- 1 root root  422607 2008-04-10 17:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root   79964 2008-04-10 17:51 config-2.6.24-16-generic
drwxr-xr-x 2 root root    4096 2008-11-27 03:20 grub
-rw-r--r-- 1 root root 7910065 2008-11-27 03:20 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7910104 2008-11-27 03:20 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root  899892 2008-04-10 17:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 17:51 vmlinuz-2.6.24-16-generic
root@aluminium:/#


```

---

### Post by caljohnsmith on 2008-11-26
That's great, it finally worked. It even said it updated the menu.lst, so while you are still chrooted in /mnt check it with:
```
cat /boot/grub/menu.lst
```
And make sure it lists the new kernel. If it does, then exit the chroot environment and do:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following lines to your 8.10 menu.lst:
```
title Ubuntu 8.04 Grub Menu
configfile (hd0,6)/boot/grub/menu.lst
```
And you should hopefully be able to boot into Ubuntu 8.04 after that. Let me know how it goes.

---

### Post by fizzybrain on 2008-11-26
Yes, the kernel is there (writing this from a different machine, so can't quote it here)
I had forgotten about linking to one grub menu from another - that will come in extremely handy.
It still doesn't work though, but I think it's just a problem of identifying partitions properly (the menu.lst on sda7 was trying to point to (hd0,1) )
I'm sure it will be a trivial matter tomorrow morning.

A demain,
Ian

---

### Post by fizzybrain on 2008-11-27
FINALLY!
For info:
Using the method described got the kernel (etc.) files installed and a new GRUB menu.lst was created. However the relevant entry looked like this 
```

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=69af626d-50ad-441e-bf67-f8998e6f25cd ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

```
 - presumably because it was made under chroot

So a quick change to -
```

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=69af626d-50ad-441e-bf67-f8998e6f25cd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

``` 

- and hurrah! a working system
Thanks for your help, now I must find some other excuse not to do any work ....

---

### Post by caljohnsmith on 2008-11-27
That's great news, glad it's working. I'm a little surprised that update-grub assigned the wrong (hdX,Y) to your 8.04 partition, because I thought we set up the chroot environment with everything the update-grub command would need to figure things out; obviously not though. At least it wasn't too hard to correct. Cheers and have fun with Ubuntu. :)

---

### Post by meierfra. on 2008-11-27
> I'm a little surprised that update-grub assigned the wrong (hdX,Y) to your 8.04 partition, 

fizzybrain: Is /dev/sda2 still mounted  at /boot in your Ubuntu 8.04 /etc/fstab?

---

### Post by fizzybrain on 2008-11-27
> **caljohnsmith said:**
> That's great news, glad it's working. I'm a little surprised that update-grub assigned the wrong (hdX,Y) to your 8.04 partition, because I thought we set up the chroot environment with everything the update-grub command would need to figure things out

I think that, not realising that apt-get had updated grub itself, I did it manually. I think I was still in chroot though.

> **meierfra. said:**
> fizzybrain: Is /dev/sda2 still mounted  at /boot in your Ubuntu 8.04 /etc/fstab?

Good point - yes it is, I'll have to change that, won't I? (Just comment out the /boot line in fstab?). Though I wouldn't have thought that that would have anything to do with root being wrong in grub - I did all the modifications while in 8.10 (and I didn't use fstab for them).

Ian

---

### Post by meierfra. on 2008-11-27
> I'll have to change that, won't I? 

Yes.

> (Just comment out the /boot line in fstab?).


That should do it.


> did all the modifications while in 8.10

No.  After "chroot /mnt /bin/bash"  all your commands were executed by 8.04.

> (and I didn't use fstab for them).

"update-grub" looks at fstab to determine the "root" line.

---

