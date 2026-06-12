---
title: "upgraded but now major problems - please help"
date: 2016-07-09
forum: Installation &amp; Upgrades
---

### Post by ubuntark on 2016-07-09
(I just reposted this in the installation  and upgrades i posted it by accident in the general section)

I was getting notifications that I could not upgrade because "boot" was running out of space.
So removed the old image image folders/files ( all but the most recent one )  seemed to work.

Then upgraded via terminal sudo commands
After upgrade install
My browser still works but I get internal error popup window when ever  attempt to do much else.

What commands or information do you need me to run so I can post the proper info here to get help. 

Thank you in advance for any help.
-- example tried to open up libreoffice  and I get this in the internal error window:

crashed with signal 7 in dl_new_hash()

---

### Post by ubfan1 on 2016-07-09
Please post the outputs of
uname -a
and 
df
That should give us an idea of what's on your system.  How did you run the upgrade?
Then any specific hardware information, like video.
lshw -C video

---

### Post by ubuntark on 2016-07-09
```
Linux name-W65-67SZ 4.2.0-41-generic #48~14.04.1-Ubuntu SMP Fri Jun 24 17:09:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

df
```
Filesystem          1K-blocks      Used Available Use% Mounted on
udev                  8158904         4   8158900   1% /dev
tmpfs                 1635124      1272   1633852   1% /run
/dev/dm-0           106257496   9422948  91413904  10% /
none                        4         0         4   0% /sys/fs/cgroup
none                     5120         0      5120   0% /run/lock
none                  8175604     12552   8163052   1% /run/shm
none                   102400        48    102352   1% /run/user
/dev/sda1              240972     52742    175789  24% /boot
/home/name/.Private 106257496   9422948  91413904  10% /home/name
/dev/sdb1           961301832 392189224 520258184  43% /media/name/21bdf37d-f5d2-484a-a851-2e2bc5e88ae4
```


upgraded by sudo commands in terminal

---

### Post by ubfan1 on 2016-07-10
OK /boot has plenty of room.  Looks like you have a logical volume for /, of which I know nothing.  I'm not even sure running fsck is appropriate, which is what I'd suggest on an sda? filesystem.

---

### Post by Impavidus on 2016-07-10
> **ubuntark said:**
> 
I was getting notifications that I could not upgrade because "boot" was running out of space.
So removed the old image image folders/files ( all but the most recent one )  seemed to work.


In this case the proper thing to do is uninstalling old kernels. Simply removing old image files gives trouble. Can you post the output of```
lsb_release -r
ls /boot
dpkg --list | grep linux-image
```
Maybe you manually removed a bit too much. Where else did you remove files, apart from /boot?

---

### Post by ubuntark on 2016-07-10
> **Impavidus said:**
> In this case the proper thing to do is uninstalling old kernels. Simply removing old image files gives trouble. Can you post the output of```
lsb_release -r
ls /boot
dpkg --list | grep linux-image
```
Maybe you manually removed a bit too much. Where else did you remove files, apart from /boot?


lsb_release -r
Release:    14.04
_____
 ls /boot
abi-4.2.0-41-generic         memtest86+.bin
config-4.2.0-41-generic      memtest86+.elf
grub                         memtest86+_multiboot.bin
initrd.img-4.2.0-41-generic  System.map-4.2.0-41-generic
lost+found                   vmlinuz-4.2.0-41-generic



___________
dpkg --list | grep linux-image
rc  linux-image-4.2.0-27-generic                          4.2.0-27.32~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-35-generic                          4.2.0-35.40~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-36-generic                          4.2.0-36.42~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-38-generic                          4.2.0-38.45~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-41-generic                          4.2.0-41.48~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                    4.2.0-27.32~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-35-generic                    4.2.0-35.40~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-36-generic                    4.2.0-36.42~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-38-generic                    4.2.0-38.45~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic                    4.2.0-41.48~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily                          4.2.0.41.33                                         amd64        Generic Linux kernel image

---

### Post by Impavidus on 2016-07-10
That seems OK. What did you do exactly?

---

### Post by ubuntark on 2016-07-10
> **Impavidus said:**
> That seems OK. What did you do exactly?

sudo apt-get update


then sudo apt-get upgrade

now things do not work or open in many cases such as 
Ubuntu software center
LibreOffice writer
Libre office calc
Libre office impress
radio tray

not sure what to do except reformat and start over. 
Also had TDameritrade Think or swim platform which will not fire up either. 

Browser still works
skype still works 
vlc stillworks

_______________________

also after upgrade I did get some kind of message via terminal 

THe link /vmlinuz.old is a damed link
REmoving symbolic link vmlinuz.old
you may need to re-run your boot loader[grub]
The link /initrd.img .old is a damaged link
Removing symbolic link initrd.img .old
you may need to re-run your boot loader[grub]

which i have no idea how to re-run a boot loader
any  suggestions?

---

### Post by ubfan1 on 2016-07-10
Don't worry about the ...old links, they would just point to the previous kernel, which no longer exists, so they are reported "damaged".  You might try checking the disk and see what the report from   sudo smartctl -a  /dev/sda   says.  It may be run from a running system.  The package to install to get smartctl is the smartmontools package.   Add that output here.

---

### Post by bapoumba on 2016-07-10
In addition please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ubuntark on 2016-07-10
> **ubfan1 said:**
> Don't worry about the ...old links, they would just point to the previous kernel, which no longer exists, so they are reported "damaged".  You might try checking the disk and see what the report from   sudo smartctl -a  /dev/sda   says.  It may be run from a running system.  The package to install to get smartctl is the smartmontools package.   Add that output here.

I am having problems obtaining the smartmontools 
what is the exact command to get and install it so I can report back to you the info you are asking for.

thank you for your time.

---

### Post by ubuntark on 2016-07-10
> **bapoumba said:**
> In addition please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt-get update
sudo apt-get upgrade
```


cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)]/ trusty main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty main restricted
     6    deb-src [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    11    deb-src [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty universe
    17    deb-src [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty universe
    18    deb [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19    deb-src [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty multiverse
    27    deb-src [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty multiverse
    28    deb [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    29    deb-src [http://gt.archive.ubuntu.com/ubuntu/](http://gt.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    
    37    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    38    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    40    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    42    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    43    
    44    ## Uncomment the following two lines to add software from Canonical's
    45    ## 'partner' repository.
    46    ## This software is not part of Ubuntu, but is offered by Canonical and the
    47    ## respective vendors as a service to Ubuntu users.
    48    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    49    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    50    
    51    ## This software is not part of Ubuntu, but is offered by third-party
    52    ## developers who want to ship their latest software.
    53    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    54    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

____________________________________________

ls -la /etc/apt/sources.list.d
total 24
drwxr-xr-x 2 root root 4096 feb 19 21:12 .
drwxr-xr-x 6 root root 4096 feb 19 19:59 ..
-rw-r--r-- 1 root root  207 abr 27 23:13 webupd8team-java-trusty.list
-rw-r--r-- 1 root root  207 abr 27 23:13 webupd8team-java-trusty.list.save
-rw-r--r-- 1 root root  148 abr 27 23:13 yannubuntu-boot-repair-trusty.list
-rw-r--r-- 1 root root  148 abr 27 23:13 yannubuntu-boot-repair-trusty.list.save

____________________________________________

  tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main

==> /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list <==
deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) trusty main

==> /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list.save <==
deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) trusty main
name@name-W65-67SZ:~$ 
________________________________________________

$ sudo apt-get update
[sudo] password for name: 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Ign [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty InRelease                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en    
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty Release   
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/main Sources
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/restricted Sources
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/universe Sources
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/multiverse Sources
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/main amd64 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/restricted amd64 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/universe amd64 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/multiverse amd64 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/main i386 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://gt.archive.ubuntu.com](http://gt.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 72 B in 10s (6 B/s)                                                    
Reading package lists... Done

____________________________________________
sudo apt-get upgrade
[sudo] password for name: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libntdb1 linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic python-ntdb
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by ubfan1 on 2016-07-10
sudo apt-get install smartmontools
then run  sudo smartctl -s /dev/sda
And see what problems the disk might have.

---

### Post by ubuntark on 2016-07-10
> **ubfan1 said:**
> sudo apt-get install smartmontools
then run  sudo smartctl -s /dev/sda
And see what problems the disk might have.

sudo smartctl -s /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-4.2.0-41-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=======> INVALID ARGUMENT TO -s: /dev/sda
=======> VALID ARGUMENTS ARE: on, off, aam,[N|off], apm,[N|off], lookahead,[on|off], security-freeze, standby,[N|off|now], wcache,[on|off], rcache,[on|off], wcreorder,[on|off] <=======

Use smartctl -h to get a usage summary

---

### Post by ubfan1 on 2016-07-11
Oops typo, the -s should have been a -a (as in the earlier post)

---

### Post by ubuntark on 2016-07-11
> **ubfan1 said:**
> Oops typo, the -s should have been a -a (as in the earlier post)


Im a trader -- gave up and reformatted and reinstalled so i could trade today. 

have a great day

---

### Post by ubuntark on 2016-07-11
How to close this thread -- 

button somewhere 
or just do i just right closed or solved in the title?

---

### Post by QIII on 2016-07-11
In the tool bar just below the thread title, click "Thread tools" and choose "Mark this thread as solved"

---

