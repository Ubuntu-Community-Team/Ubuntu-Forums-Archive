---
title: "Need help understanding kernel version numbering"
date: 2016-04-06
forum: Installation &amp; Upgrades
---

### Post by ross4 on 2016-04-06
Either I can't read properly or I don't understand kernel numbering or something is not happening correctly. Back in February, I installed Xubuntu 14.04.3 LTS "Trusty Tahr" - Beta amd64 (as stated in the README.diskdefines file). At that time, the output from uname -a was:
  Linux ross-HP-EliteBook-6930p 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux.
  
  Presently, after several Software Updater updates, when I do uname -a, I get  
  Linux ross-HP-EliteBook-6930p 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

  and when I look in /boot I see (among other things):
 -rw-------  1 root root  5833568 Mar 17 15:51 vmlinuz-3.13.0-85-generic  
 -rw-------  1 root root  6574032 Jan 22 07:22 vmlinuz-3.19.0-49-generic  
 -rw-------  1 root root  6575024 Feb 26 15:32 vmlinuz-3.19.0-51-generic  
 -rw-------  1 root root  6579344 Mar 11 05:10 vmlinuz-3.19.0-56-generic  
  -rw-------  1 root root  6591152 Mar 18 14:27 vmlinuz-3.19.0-58-generic  
  

  It seems to me that I should be operating under 3.19.0-58-generic and that the other kernels should be “older” kernels, candidates for removal. Am I correct and if so, why isn't the system 'updating' kernels correctly? If I am not correct, where have I gone wrong in my thinking?
  BTW, I do not have a separate /boot partition and / is only 22% used, so I don't think it is a case of there not being enough space for a an update to occur.

---

### Post by Bashing-om on 2016-04-06
ross4; Hello;

Agreed:
> 
It seems to me that I should be operating under 3.19.0-58-generic 

Per:
```

You have searched for packages that names contain linux-image-generic in suite(s) trusty-updates, all sections, and all architectures. Found 10 matching packages. >>
Package linux-image-generic-lts-vivid

trusty-updates (kernel): Generic Linux kernel image 
3.19.0.58.41: amd64 i386

```
So, let us see what we can do to find out what is not going on.

Show us the outputs of terminal commands:
```

sudp apt update
sudo apt full-upgrade
apt-get -f install
dpkg -l | grep linux-
ls -al /vmlinuz*
ls -al /initrd*

```

Missing the meta-packaging ?? If so, that is easily remedied .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by deadflowr on 2016-04-06
Single boot or dual/multi-boot system?

---

### Post by grahammechanical on 2016-04-06
Whatever you think you are still running a 3.19 kernel. The differences between -49: -51; -56 & -58 are Ubuntu kernel team revisions containing patches of one sort or another. Of, course, you should be loading by default kernel 3.19.0-58.

The printout from uname -a is the kernel you are actually loading into. You should be able to load into any of the others by entering the Advanced options for Ubuntu sub-menu at the Grub boot menu. Test them out.

When you run those command recommended by Bashing-om you may find that some of those kernels are marked for autoremoval. That can happen to later kernel that were found to be broken in some way by other users. They may work fine on your hardware but other users may have reported bugs which prompted the developers to revert your system to default to an older kernel.

Regards.

---

### Post by ross4 on 2016-04-06
Thanks to all for quick responses!
Bashing-om: The commands produce a great deal of output. What is the easiest, most efficient way to get this output into a response? I can't figure out how to get one of those tidy 'code' boxes.

deadflowr: This is a dual boot, Xbuntu & Mint 'Rosa'

grahammechanical: The Advanced options sub-menu only provides options for 3.19.0-49-generic & 3.19.0-25-generic ...

---

### Post by Bashing-om on 2016-04-06
ross4; Hey:

> 
What is the easiest, most efficient way to get this output into a response? I can't figure out how to get one of those tidy 'code' boxes.

Like so:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Not to know is not a sin, in those cases , just ask.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by ross4 on 2016-04-06
Excellent! Thank you.

Here are the various results, in order:
                         sudo apt update
  
```

                         [sudo] password for ross:  
  Ign http://extras.ubuntu.com trusty InRelease  
  Ign http://ca.archive.ubuntu.com trusty InRelease  
  Get:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]  
  Hit http://extras.ubuntu.com trusty Release.gpg                                 
  Get:2 http://ca.archive.ubuntu.com trusty-updates InRelease [65.9 kB]           
  Hit http://extras.ubuntu.com trusty Release                                     
  Hit http://extras.ubuntu.com trusty/main Sources                                
  Get:3 http://security.ubuntu.com trusty-security/main Sources [110 kB]          
  Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
  Hit http://ca.archive.ubuntu.com trusty-backports InRelease                    
  Hit http://extras.ubuntu.com trusty/main i386 Packages                          
  Hit http://ca.archive.ubuntu.com trusty Release.gpg                             
  Get:4 http://security.ubuntu.com trusty-security/restricted Sources [4,035 B]  
  Get:5 http://ca.archive.ubuntu.com trusty-updates/main Sources [271 kB]         
  Get:6 http://security.ubuntu.com trusty-security/universe Sources [35.2 kB]   
  Get:7 http://security.ubuntu.com trusty-security/multiverse Sources [2,750 B]   
  Get:8 http://security.ubuntu.com trusty-security/main amd64 Packages [455 kB]   
  Get:9 http://ca.archive.ubuntu.com trusty-updates/restricted Sources [5,352 B]  
  Get:10 http://ca.archive.ubuntu.com trusty-updates/universe Sources [152 kB]    
  Get:11 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]  
  Ign http://extras.ubuntu.com trusty/main Translation-en_CA                      
  Get:12 http://security.ubuntu.com trusty-security/universe amd64 Packages [126 kB]  
  Ign http://extras.ubuntu.com trusty/main Translation-en                         
  Get:13 http://ca.archive.ubuntu.com trusty-updates/multiverse Sources [5,946 B]  
  Get:14 http://ca.archive.ubuntu.com trusty-updates/main amd64 Packages [754 kB]  
  Get:15 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4,991 B]  
  Get:16 http://security.ubuntu.com trusty-security/main i386 Packages [429 kB]   
  Get:17 http://ca.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]  
  Get:18 http://ca.archive.ubuntu.com trusty-updates/universe amd64 Packages [357 kB]  
  Get:19 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]  
  Get:20 http://security.ubuntu.com trusty-security/universe i386 Packages [126 kB]  
  Get:21 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5,175 B]  
  Get:22 http://ca.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]  
  Hit http://security.ubuntu.com trusty-security/main Translation-en       
  Get:23 http://ca.archive.ubuntu.com trusty-updates/main i386 Packages [720 kB]  
  Hit http://security.ubuntu.com trusty-security/multiverse Translation-en        
  Hit http://security.ubuntu.com trusty-security/restricted Translation-en        
  Hit http://security.ubuntu.com trusty-security/universe Translation-en          
  Get:24 http://ca.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]  
  Get:25 http://ca.archive.ubuntu.com trusty-updates/universe i386 Packages [359 kB]  
  Get:26 http://ca.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]  
  Get:27 http://ca.archive.ubuntu.com trusty-updates/main Translation-en [378 kB]  
  Get:28 http://ca.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,227 B]  
  Get:29 http://ca.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]  
  Get:30 http://ca.archive.ubuntu.com trusty-updates/universe Translation-en [187 kB]  
  Hit http://ca.archive.ubuntu.com trusty-backports/main Sources                  
  Hit http://ca.archive.ubuntu.com trusty-backports/restricted Sources            
  Hit http://ca.archive.ubuntu.com trusty-backports/universe Sources              
  Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Sources            
  Hit http://ca.archive.ubuntu.com trusty-backports/main amd64 Packages           
  Hit http://ca.archive.ubuntu.com trusty-backports/restricted amd64 Packages     
  Hit http://ca.archive.ubuntu.com trusty-backports/universe amd64 Packages       
  Hit http://ca.archive.ubuntu.com trusty-backports/multiverse amd64 Packages     
  Hit http://ca.archive.ubuntu.com trusty-backports/main i386 Packages            
  Hit http://ca.archive.ubuntu.com trusty-backports/restricted i386 Packages      
  Hit http://ca.archive.ubuntu.com trusty-backports/universe i386 Packages        
  Hit http://ca.archive.ubuntu.com trusty-backports/multiverse i386 Packages      
  Hit http://ca.archive.ubuntu.com trusty-backports/main Translation-en           
  Hit http://ca.archive.ubuntu.com trusty-backports/multiverse Translation-en     
  Hit http://ca.archive.ubuntu.com trusty-backports/restricted Translation-en     
  Hit http://ca.archive.ubuntu.com trusty-backports/universe Translation-en       
  Hit http://ca.archive.ubuntu.com trusty Release                                 
  Hit http://ca.archive.ubuntu.com trusty/main Sources                            
  Hit http://ca.archive.ubuntu.com trusty/restricted Sources                      
  Hit http://ca.archive.ubuntu.com trusty/universe Sources                        
  Hit http://ca.archive.ubuntu.com trusty/multiverse Sources                      
  Hit http://ca.archive.ubuntu.com trusty/main amd64 Packages                     
  Hit http://ca.archive.ubuntu.com trusty/restricted amd64 Packages               
  Hit http://ca.archive.ubuntu.com trusty/universe amd64 Packages                 
  Hit http://ca.archive.ubuntu.com trusty/multiverse amd64 Packages               
  Hit http://ca.archive.ubuntu.com trusty/main i386 Packages                      
  Hit http://ca.archive.ubuntu.com trusty/restricted i386 Packages                
  Hit http://ca.archive.ubuntu.com trusty/universe i386 Packages                  
  Hit http://ca.archive.ubuntu.com trusty/multiverse i386 Packages                
  Hit http://ca.archive.ubuntu.com trusty/main Translation-en_CA                  
  Hit http://ca.archive.ubuntu.com trusty/main Translation-en                     
  Hit http://ca.archive.ubuntu.com trusty/multiverse Translation-en               
  Hit http://ca.archive.ubuntu.com trusty/restricted Translation-en               
  Hit http://ca.archive.ubuntu.com trusty/universe Translation-en_CA              
  Hit http://ca.archive.ubuntu.com trusty/universe Translation-en                 
  Ign http://ca.archive.ubuntu.com trusty/multiverse Translation-en_CA            
  Ign http://ca.archive.ubuntu.com trusty/restricted Translation-en_CA            
  Fetched 4,716 kB in 17s (271 kB/s)                                              
  Reading package lists... Done  
  ross@ross-HP-EliteBook-6930p:~$  
  

```
                        sudo apt full-upgrade  ```

                         ross@ross-HP-EliteBook-6930p:~$ sudo apt full-upgrade  
  Reading package lists... Done  
  Building dependency tree        
  Reading state information... Done  
  Calculating upgrade... Done  
  The following packages will be upgraded:  
    apt apt-transport-https apt-utils libapt-inst1.5 libapt-pkg4.12 libmm-glib0  
    libnautilus-extension1a modemmanager nautilus-data  
    xserver-xorg-core-lts-vivid  
  10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
  Need to get 3,844 kB of archives.  
  After this operation, 104 kB of additional disk space will be used.  
  

  Do you want to continue? [Y/n] Y  
  Get:1 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libapt-pkg4.12 amd64 1.0.1ubuntu2.12 [637 kB]  
  Get:2 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main apt amd64 1.0.1ubuntu2.12 [954 kB]  
  Get:3 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libapt-inst1.5 amd64 1.0.1ubuntu2.12 [58.6 kB]  
  Get:4 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libmm-glib0 amd64 1.0.0-2ubuntu1.1 [130 kB]  
  Get:5 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main apt-utils amd64 1.0.1ubuntu2.12 [172 kB]  
  Get:6 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main apt-transport-https amd64 1.0.1ubuntu2.12 [25.1 kB]  
  Get:7 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main libnautilus-extension1a amd64 1:3.10.1-0ubuntu9.11 [52.1 kB]  
  Get:8 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main modemmanager amd64 1.0.0-2ubuntu1.1 [473 kB]  
  Get:9 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9.11 [50.7 kB]  
  Get:10 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-core-lts-vivid amd64 2:1.17.1-0ubuntu3.1~trusty1 [1,291 kB]  
  Fetched 3,844 kB in 11s (329 kB/s)                                              
  (Reading database ... 300723 files and directories currently installed.)  
  Preparing to unpack .../libapt-pkg4.12_1.0.1ubuntu2.12_amd64.deb ...  
  Unpacking libapt-pkg4.12:amd64 (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...  
  Setting up libapt-pkg4.12:amd64 (1.0.1ubuntu2.12) ...  
  Processing triggers for libc-bin (2.19-0ubuntu6.7) ...  
  (Reading database ... 300723 files and directories currently installed.)  
  Preparing to unpack .../apt_1.0.1ubuntu2.12_amd64.deb ...  
  Unpacking apt (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...  
  Processing triggers for man-db (2.6.7.1-1ubuntu1) ...  
  Setting up apt (1.0.1ubuntu2.12) ...  
  Processing triggers for libc-bin (2.19-0ubuntu6.7) ...  
  (Reading database ... 300723 files and directories currently installed.)  
  Preparing to unpack .../libapt-inst1.5_1.0.1ubuntu2.12_amd64.deb ...  
  Unpacking libapt-inst1.5:amd64 (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...  
  Preparing to unpack .../libmm-glib0_1.0.0-2ubuntu1.1_amd64.deb ...  
  Unpacking libmm-glib0:amd64 (1.0.0-2ubuntu1.1) over (1.0.0-2ubuntu1) ...  
  Preparing to unpack .../apt-utils_1.0.1ubuntu2.12_amd64.deb ...  
  Unpacking apt-utils (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...  
  Preparing to unpack .../apt-transport-https_1.0.1ubuntu2.12_amd64.deb ...  
  Unpacking apt-transport-https (1.0.1ubuntu2.12) over (1.0.1ubuntu2.11) ...  
  Preparing to unpack .../libnautilus-extension1a_1%3a3.10.1-0ubuntu9.11_amd64.deb ...  
  Unpacking libnautilus-extension1a (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.9) ...  
  Preparing to unpack .../modemmanager_1.0.0-2ubuntu1.1_amd64.deb ...  
  modemmanager stop/waiting  
  Unpacking modemmanager (1.0.0-2ubuntu1.1) over (1.0.0-2ubuntu1) ...  
  Preparing to unpack .../nautilus-data_1%3a3.10.1-0ubuntu9.11_all.deb ...  
  Unpacking nautilus-data (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.9) ...  
  Preparing to unpack .../xserver-xorg-core-lts-vivid_2%3a1.17.1-0ubuntu3.1~trusty1_amd64.deb ...  
  Unpacking xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) over (2:1.17.1-0ubuntu3~trusty1) ...  
  Processing triggers for man-db (2.6.7.1-1ubuntu1) ...  
  Processing triggers for hicolor-icon-theme (0.13-1) ...  
  Processing triggers for ureadahead (0.100.0-16) ...  
  ureadahead will be reprofiled on next reboot  
  Processing triggers for shared-mime-info (1.2-0ubuntu3) ...  
  Processing triggers for gconf2 (3.2.6-0ubuntu2) ...  
  Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...  
  Setting up libapt-inst1.5:amd64 (1.0.1ubuntu2.12) ...  
  Setting up libmm-glib0:amd64 (1.0.0-2ubuntu1.1) ...  
  Setting up apt-utils (1.0.1ubuntu2.12) ...  
  Setting up apt-transport-https (1.0.1ubuntu2.12) ...  
  Setting up libnautilus-extension1a (1:3.10.1-0ubuntu9.11) ...  
  Setting up modemmanager (1.0.0-2ubuntu1.1) ...  
  modemmanager start/running, process 5466  
  Setting up nautilus-data (1:3.10.1-0ubuntu9.11) ...  
  Setting up xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) ...  
  Processing triggers for libc-bin (2.19-0ubuntu6.7) ...  
  ross@ross-HP-EliteBook-6930p:~$  

  
```
                        apt-get -f install  ```

                         ross@ross-HP-EliteBook-6930p:~$ sudo apt-get -f install  
  Reading package lists... Done  
  Building dependency tree        
  Reading state information... Done  
  0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
  ross@ross-HP-EliteBook-6930p:~$  

  
```
                        dpkg -l | grep linux-

```

 [SIZE=2]ross@ross-HP-EliteBook-6930p:~$ dpkg -l | grep 'linux-' [/SIZE] 

  [SIZE=2]ii  linux-firmware                              1.127.20                                all          Firmware for Linux kernel drivers [/SIZE] 
  [SIZE=2]ii  linux-generic                               3.13.0.85.91                            amd64        Complete Generic Linux kernel and headers [/SIZE] 
  [SIZE=2]ii  linux-generic-lts-vivid                     3.19.0.58.41                            amd64        Complete Generic Linux kernel and headers [/SIZE] 
  [SIZE=2]ii  linux-headers-3.13.0-83                     3.13.0-83.127                           all          Header files related to Linux kernel version 3.13.0 [/SIZE] 
  [SIZE=2]ii  linux-headers-3.13.0-83-generic             3.13.0-83.127                           amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-headers-3.13.0-85                     3.13.0-85.129                           all          Header files related to Linux kernel version 3.13.0 [/SIZE] 
  [SIZE=2]ii  linux-headers-3.13.0-85-generic             3.13.0-85.129                           amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-headers-3.19.0-49                     3.19.0-49.55~14.04.1                    all          Header files related to Linux kernel version 3.19.0 [/SIZE] 
  [SIZE=2]ii  linux-headers-3.19.0-49-generic             3.19.0-49.55~14.04.1                    amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-headers-3.19.0-51                     3.19.0-51.58~14.04.1                    all          Header files related to Linux kernel version 3.19.0 [/SIZE] 
  [SIZE=2]ii  linux-headers-3.19.0-51-generic             3.19.0-51.58~14.04.1                    amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-headers-3.19.0-56                     3.19.0-56.62~14.04.1                    all          Header files related to Linux kernel version 3.19.0 [/SIZE] 
  [SIZE=2]ii  linux-headers-3.19.0-56-generic             3.19.0-56.62~14.04.1                    amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-headers-3.19.0-58                     3.19.0-58.64~14.04.1                    all          Header files related to Linux kernel version 3.19.0 [/SIZE] 
  [SIZE=2]ii  linux-headers-3.19.0-58-generic             3.19.0-58.64~14.04.1                    amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-headers-generic                       3.13.0.85.91                            amd64        Generic Linux kernel headers [/SIZE] 
  [SIZE=2]ii  linux-headers-generic-lts-vivid             3.19.0.58.41                            amd64        Generic Linux kernel headers [/SIZE] 
  [SIZE=2]ii  linux-image-3.13.0-85-generic               3.13.0-85.129                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]rc  linux-image-3.19.0-25-generic               3.19.0-25.26~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-3.19.0-49-generic               3.19.0-49.55~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-3.19.0-51-generic               3.19.0-51.58~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-3.19.0-56-generic               3.19.0-56.62~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-3.19.0-58-generic               3.19.0-58.64~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-extra-3.13.0-85-generic         3.13.0-85.129                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]rc  linux-image-extra-3.19.0-25-generic         3.19.0-25.26~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-extra-3.19.0-49-generic         3.19.0-49.55~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-extra-3.19.0-51-generic         3.19.0-51.58~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-extra-3.19.0-56-generic         3.19.0-56.62~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-extra-3.19.0-58-generic         3.19.0-58.64~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP [/SIZE] 
  [SIZE=2]ii  linux-image-generic                         3.13.0.85.91                            amd64        Generic Linux kernel image [/SIZE] 
  [SIZE=2]ii  linux-image-generic-lts-vivid               3.19.0.58.41                            amd64        Generic Linux kernel image [/SIZE] 
  [SIZE=2]ii  linux-libc-dev:amd64                        3.13.0-85.129                           amd64        Linux Kernel Headers for development [/SIZE] 
  [SIZE=2]ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems [/SIZE] 
  [SIZE=2]ross@ross-HP-EliteBook-6930p:~$ [/SIZE] 
  

```
ls -al /vmlinuz*
```
ross@ross-HP-EliteBook-6930p:~$ ls -al /vmlinuz* 
lrwxrwxrwx 1 root root 30 Apr  5 14:57 /vmlinuz -> boot/vmlinuz-3.19.0-58-generic 
lrwxrwxrwx 1 root root 30 Apr  5 14:56 /vmlinuz.old -> boot/vmlinuz-3.13.0-85-generic 
ross@ross-HP-EliteBook-6930p:~$ 

```
ls -al /initrd*
```
ross@ross-HP-EliteBook-6930p:~$ ls -al /initrd* 
lrwxrwxrwx 1 root root 33 Apr  5 14:57 /initrd.img -> boot/initrd.img-3.19.0-58-generic 
lrwxrwxrwx 1 root root 33 Apr  5 14:56 /initrd.img.old -> boot/initrd.img-3.13.0-85-generic 
ross@ross-HP-EliteBook-6930p:~$ 

```
Hope you can make sense out of some of this.

---

### Post by Bashing-om on 2016-04-06
ross4; Well, well ... well ...

All that appears to be in order .
You are set to boot:
```

/vmlinuz -> boot/vmlinuz-3.19.0-58-generic 

```

So why are you not ???

show us the results:
```

cat /etc/default/grub
sudo update-grub

```
See if that gives us a hint of where to look.
(/boot/grub/grub.cfg ) ??

[INDENT][INDENT]they's a rat in the woodpile
[INDENT][INDENT][INDENT]somewhere
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2016-04-06
One more request :)

```
cat /var/run/reboot-required.pkgs
```

Whats that print out?

---

### Post by ross4 on 2016-04-06
Ok, let's see

```

ross@ross-HP-EliteBook-6930p:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
ross@ross-HP-EliteBook-6930p:~$ 

```

and 
```

ross@ross-HP-EliteBook-6930p:~$ sudo update-grub
[sudo] password for ross: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-58-generic
Found initrd image: /boot/initrd.img-3.19.0-58-generic
Found linux image: /boot/vmlinuz-3.19.0-56-generic
Found initrd image: /boot/initrd.img-3.19.0-56-generic
Found linux image: /boot/vmlinuz-3.19.0-51-generic
Found initrd image: /boot/initrd.img-3.19.0-51-generic
Found linux image: /boot/vmlinuz-3.19.0-49-generic
Found initrd image: /boot/initrd.img-3.19.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-85-generic
Found initrd image: /boot/initrd.img-3.13.0-85-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint 17.3 Rosa (17.3) on /dev/sda6
done
ross@ross-HP-EliteBook-6930p:~$ 


```

And finally for v3.xx:
```

ross@ross-HP-EliteBook-6930p:~$ cat /var/run/reboot-required.pkgs
cat: /var/run/reboot-required.pkgs: No such file or directory
ross@ross-HP-EliteBook-6930p:~$ 


```

What do we learn from this?

---

### Post by Bashing-om on 2016-04-06
ross4; Hummm ...

@ v3.xx :)
Again, one of those times, we meet like this .


Again I see nothing amiss !
even:
```

sysop@1404mini:~$ cat /var/run/reboot-required.pkgs
cat: /var/run/reboot-required.pkgs: No such file or directory
sysop@1404mini:~$

```
Is also my output.

Can we make heads or tails from grub's boot config file ?
show:
```

cat /boot/grub/grub.cfg

```
Also kinda strange that the back up kernel for booting is set to the 3.13 kernel ... hummmm .. most likely because the 3.13 meta packaging remains on the system . Even here I would expect an older 3.19 kernel to be selected by default...

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by ross4 on 2016-04-06
Lots of stuff in this. Someday I'll try learn how to read more of it.

```

ross@ross-HP-EliteBook-6930p:~$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
else
  search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
    else
      search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
    fi
    linux    /boot/vmlinuz-3.19.0-58-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.19.0-58-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
    menuentry 'Ubuntu, with Linux 3.19.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-58-generic-advanced-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.19.0-58-generic ...'
        linux    /boot/vmlinuz-3.19.0-58-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-58-generic-recovery-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.19.0-58-generic ...'
        linux    /boot/vmlinuz-3.19.0-58-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-56-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-56-generic-advanced-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.19.0-56-generic ...'
        linux    /boot/vmlinuz-3.19.0-56-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-56-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-56-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-56-generic-recovery-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.19.0-56-generic ...'
        linux    /boot/vmlinuz-3.19.0-56-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-56-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-51-generic-advanced-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.19.0-51-generic ...'
        linux    /boot/vmlinuz-3.19.0-51-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-51-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-51-generic-recovery-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.19.0-51-generic ...'
        linux    /boot/vmlinuz-3.19.0-51-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-51-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-49-generic-advanced-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.19.0-49-generic ...'
        linux    /boot/vmlinuz-3.19.0-49-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-49-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-49-generic-recovery-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.19.0-49-generic ...'
        linux    /boot/vmlinuz-3.19.0-49-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-49-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-advanced-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.13.0-85-generic ...'
        linux    /boot/vmlinuz-3.13.0-85-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-85-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-recovery-c6c7fe1d-76aa-4608-b456-ea8b25812849' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
        else
          search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
        fi
        echo    'Loading Linux 3.13.0-85-generic ...'
        linux    /boot/vmlinuz-3.13.0-85-generic root=UUID=c6c7fe1d-76aa-4608-b456-ea8b25812849 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-85-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
    else
      search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  c6c7fe1d-76aa-4608-b456-ea8b25812849
    else
      search --no-floppy --fs-uuid --set=root c6c7fe1d-76aa-4608-b456-ea8b25812849
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Linux Mint 17.3 Rosa (17.3) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-abd0db27-366a-472b-9dc9-a81a41938d98' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  abd0db27-366a-472b-9dc9-a81a41938d98
    else
      search --no-floppy --fs-uuid --set=root abd0db27-366a-472b-9dc9-a81a41938d98
    fi
    linux /boot/vmlinuz-3.19.0-32-generic root=UUID=abd0db27-366a-472b-9dc9-a81a41938d98 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.19.0-32-generic
}
submenu 'Advanced options for Linux Mint 17.3 Rosa (17.3) (on /dev/sda6)' $menuentry_id_option 'osprober-gnulinux-advanced-abd0db27-366a-472b-9dc9-a81a41938d98' {
    menuentry 'Linux Mint 17.3 Cinnamon 64-bit (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-32-generic--abd0db27-366a-472b-9dc9-a81a41938d98' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  abd0db27-366a-472b-9dc9-a81a41938d98
        else
          search --no-floppy --fs-uuid --set=root abd0db27-366a-472b-9dc9-a81a41938d98
        fi
        linux /boot/vmlinuz-3.19.0-32-generic root=UUID=abd0db27-366a-472b-9dc9-a81a41938d98 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.19.0-32-generic
    }
    menuentry 'Linux Mint 17.3 Cinnamon 64-bit, with Linux 3.19.0-32-generic (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-32-generic--abd0db27-366a-472b-9dc9-a81a41938d98' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  abd0db27-366a-472b-9dc9-a81a41938d98
        else
          search --no-floppy --fs-uuid --set=root abd0db27-366a-472b-9dc9-a81a41938d98
        fi
        linux /boot/vmlinuz-3.19.0-32-generic root=UUID=abd0db27-366a-472b-9dc9-a81a41938d98 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.19.0-32-generic
    }
    menuentry 'Linux Mint 17.3 Cinnamon 64-bit, with Linux 3.19.0-32-generic (recovery mode) (on /dev/sda6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.19.0-32-generic-root=UUID=abd0db27-366a-472b-9dc9-a81a41938d98 ro recovery nomodeset-abd0db27-366a-472b-9dc9-a81a41938d98' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  abd0db27-366a-472b-9dc9-a81a41938d98
        else
          search --no-floppy --fs-uuid --set=root abd0db27-366a-472b-9dc9-a81a41938d98
        fi
        linux /boot/vmlinuz-3.19.0-32-generic root=UUID=abd0db27-366a-472b-9dc9-a81a41938d98 ro recovery nomodeset
        initrd /boot/initrd.img-3.19.0-32-generic
    }
}

set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
ross@ross-HP-EliteBook-6930p:~$ 


```

---

### Post by Bashing-om on 2016-04-06
ross4; Sheeshhh ...

I am at a loss, I see no fault here either.

I am at the end of my skill set .. Now. I think, it is up to what hooks are called when the initiate system calls initramfs to build the on-disk image. I do not know how to look and trace these calls (hooks) made from within the kernel space. 
I could be in error here, and others' opinions are welcomed.

Now I too
[INDENT][INDENT][INDENT]have my learning cap on
[/INDENT][/INDENT][/INDENT]

---

### Post by ross4 on 2016-04-06
Well, first, thank you very much for your help so far. And second, I was feeling totally befuddled by the whole experience. I did do a lot of googling on various ways of describing the problem and got lots of information but ended up being more confused than ever so it is ever so nice to find that the solution is not so obvious. I have it in the back of my mind that there is a 'switch' somewhere in some panel that I haven't set. All I need is the correct potion of reveal to find it. At any rate, thank you again. And if anyone else has suggestions please make them.
Cheers,
R.

---

### Post by QLee on 2016-04-07
> **Bashing-om said:**
> ross4; Sheeshhh ...

I am at a loss, I see no fault here either.

I am at the end of my skill set .. Now. I think, it is up to what hooks are called when the initiate system calls initramfs to build the on-disk image. I do not know how to look and trace these calls (hooks) made from within the kernel space. 
I could be in error here, and others' opinions are welcomed.

Now I too
[INDENT][INDENT][INDENT]have my learning cap on
[/INDENT][/INDENT][/INDENT]

Well, I doubt that you are at the end of your skill set, maybe reframe how we are looking at this. There was a hint back in post 3.  Might things be different if the Mint installation was controlling the boot? We've only looked at grub.cfg on the Ubuntu installation, eh?

---

### Post by deadflowr on 2016-04-07
> **QLee said:**
> Well, I doubt that you are at the end of your skill set, maybe reframe how we are looking at this. There was a hint back in post 3.  Might things be different if the Mint installation was controlling the boot? We've only looked at grub.cfg on the Ubuntu installation, eh?
Indeed.
Though, I'm not sure it is the case, but you never know.
Just for peace of mind the OP could try
```
sudo grub-install /dev/sda
```
followed by the 
```
sudo update-grub
```
command.
Then see what happens.

---

### Post by Bashing-om on 2016-04-07
et al ; :)

sounds good to me .

[INDENT][INDENT]right wrong or otherwise
[INDENT][INDENT][INDENT]do something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ross4 on 2016-04-07
Ok, I'll give those a try.
First:
```

ross@ross-HP-EliteBook-6930p:~$ sudo grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
ross@ross-HP-EliteBook-6930p:~$

```

and

```

ross@ross-HP-EliteBook-6930p:~$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-58-generic
Found initrd image: /boot/initrd.img-3.19.0-58-generic
Found linux image: /boot/vmlinuz-3.19.0-56-generic
Found initrd image: /boot/initrd.img-3.19.0-56-generic
Found linux image: /boot/vmlinuz-3.19.0-51-generic
Found initrd image: /boot/initrd.img-3.19.0-51-generic
Found linux image: /boot/vmlinuz-3.19.0-49-generic
Found initrd image: /boot/initrd.img-3.19.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-85-generic
Found initrd image: /boot/initrd.img-3.13.0-85-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint 17.3 Rosa (17.3) on /dev/sda6
done
ross@ross-HP-EliteBook-6930p:~$ 


```

---

### Post by Bashing-om on 2016-04-07
ross4; Annnddd ....

After a reboot, what returns now:
```
 uname -a
```

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by ross4 on 2016-04-07
Hi! The obvious thing to do after issuing those commands was to re-boot, which I did. The Boot menu looked completely different, with the first option now being Xubuntu, then Xubuntu advanced items (which showed all of the loaded Xubuntu kernals), mem tests (I think) and finally Mint, Upon booting Xubuntu, I issued uname -r and :P
this is what I got:
```

ross@ross-HP-EliteBook-6930p:~$ uname -r
3.19.0-58-generic
ross@ross-HP-EliteBook-6930p:~$ 

```

I'll mark this thread as solved but I would really appreciate it if someone would explain what was likely going on there. That, to me, would be very useful information to add to my (very, very limited) store of Linux knowledge.

Thank you very much Bashing-om for all the time you spent on this and thank you QLee and deadflowr for re-focussing the problem in a way which lead to its solution. The Ubuntu forum is truly an amazing resource,
Cheers and thanks again to all,
Ross

---

### Post by deadflowr on 2016-04-07
> [COLOR=#000000]I'll mark this thread as solved but I would really appreciate it if someone would explain what was likely going on there.[/COLOR]

Both xubuntu and mint have grub, but only one controls the bootloader at a time.
It seems the version used in mint might have been the one in charge.
running the grub-install command while booted in xubuntu
makes the version it has in charge.

Something that happens sometimes is that when a system gets a rare update to grub, the update re-runs that command, in a way,
which makes that system the one in charge of grub.
It's rare on a non-development release, but happens from time to time.
For mint, it would be extremely rare, and if that was the case, I would assume it had to do with the [grub-password bug]("http://www.ubuntu.com/usn/usn-2836-1/").

Of course that is pure speculation and it could have been just a configuration problem with the grub setup for Xubuntu...
Either way, glad it worked out.

---

### Post by ross4 on 2016-04-07
Thank you very much for that explanation. I actually intend to remove the Mint as soon as I have time because I have not been happy with its performance on this machine. The screen occasionally jumps jaggedly around and I haven't had time to research how to fix that. Since I was otherwise happy with Xubuntu (other than this kernel problem, I mean), I think I'll just ignore Mint until a rainy day comes (beautiful sunshine here in Vancouver today) and then perhaps re-install Xubuntu to be the only Linux on my working machine. I just got a used Lenovo and I am looking forward to doing all sorts of things on it without worrying about what mistakes I make. Perhaps I'll mess around with grub on that one to begin with. I don't and I won't run windows on either of my laptops. 
It is interesting how similar symptoms can have different causes. I did a lot of searching on "kernel retention" and couldn't find anything like the final solution I found here. 
Once again, thanks to everyone for the great help. 
Cheers,
Ross

---

### Post by QLee on 2016-04-08
> **ross4 said:**
> ... I actually intend to remove the Mint as soon as I have time because I have not been happy with its performance on this machine. ... 

Since I was otherwise happy with Xubuntu (other than this kernel problem, I mean), I think I'll just ignore Mint until a rainy day comes (beautiful sunshine here in Vancouver today) and then perhaps re-install Xubuntu to be the only Linux on my working machine. I just got a used Lenovo and I am looking forward to doing all sorts of things on it without worrying about what mistakes I make. Perhaps I'll mess around with grub on that one to begin with. ... 

I did a lot of searching on "kernel retention" and couldn't find anything like the final solution I found here. 
...

That is because it really didn't have anything to do with kernel retention. The kernels were being retained correctly by Xubuntu, just not where GRUB was looking for them.

When your system is booting up the BIOS looks at the MBR (master boot record) of the first drive and that sends it to a partition to look for /boot/grub/ and then continues on from there to display the menu. (simplified but basically correct)

On your system, both your Mint and Xubuntu partitions have a /boot/grub/ so it depends on where the pointer in the MBR is set, to determine which partition's GRUB menu is used. When you issued the command "grub-install /dev/sda", with sudo as root, while you were working in Xubuntu (on the Xubuntu partition), that set the mbr to look at the Xbuntu partition where the files necessary to boot Xubuntu with upgraded kernels existed. You can think of it as, the operating system on the partition that "controls" booting is at the top of the menu.

Since you clearly want to learn, one place to start reading about GRUB is at the Community Help Wiki, here are some pages about GRUB to get you started:

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

Good for you for choosing to get a system to test with, it's easier to learn if you're not risking anything mission-critical when you try things. And, there are plenty of people here to help you when you have questions, not to mention all the wiki articles and searchable previous posts.

Good luck and enjoy what looks like, from the forecast, another sunny day in Vancouver.



You will not need to reinstall Xubuntu in order to remove Mint. Now that Xubuntu is "controlling" which menu is used for booting, even if you wipe or delete the partition that Mint is on, your Xubuntu will boot and, if, after wiping or deleting the Mint, you again run "update-grub" your menu will no longer even show Mint as a choice. Then you could choose to use that partition as a separate storage for data or the space could be merged with your Xubuntu partition or you could even install some other Linux operating system.

---

### Post by ross4 on 2016-04-23
Thank you for those links. I had on my to-do list to create my own notes etc. on GRUB but I hadn't got around to it yet. Those will be very helpful. I actually came back to this thread to remind myself of how to update grub because I wanted to delete Mint and so your comments are spot on. Now, for a bit of newbie humour: I couldn't remember the order in which I finally installed Xubuntu and Mint because I actually did several installations and my notes were not as good as they should have been. As a result, I wasn't sure which partition each was on. I must have spent several hours searching on a way to determine this. After spending that time, I finally felt very confident that I knew where Mint was. Then, for some reason I read the boot menu again, very carefully. One of the choices was: Linux Mint 17.3 Rosa (17.3) (on /dev/sda6). Arrrgh, two seconds to find out what had taken me several hours.
Again, thanks everyone for your help
Ross

---

