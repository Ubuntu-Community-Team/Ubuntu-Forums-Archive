---
title: "linux-image-generic : Depends: linux-image-3.0.0-14-generic but it is not going to b"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by Horatio on 2011-12-28
linux-image-generic : Depends: linux-image-3.0.0-14-generic but it is not going to be installed

The above message is now given to me when I try to install something new. e.g.

```

 sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-3.0.0-14-generic but it is not going to be installed
 wine : Depends: wine1.3 but it is not going to be installed
        Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
        Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
        Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

I tried the suggested command
```

:/etc/kernel/postrm.d$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  linux-image-3.0.0-14-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 37.2 MB of archives.
After this operation, 153 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main linux-image-3.0.0-14-generic amd64 3.0.0-14.23 [37.2 MB]
Fetched 37.2 MB in 14s (2,628 kB/s)                                                                                                                                                          
(Reading database ... 236858 files and directories currently installed.)
Unpacking linux-image-3.0.0-14-generic (from .../linux-image-3.0.0-14-generic_3.0.0-14.23_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-14-generic_3.0.0-14.23_amd64.deb (--unpack):
 unable to install new version of `/lib/modules/3.0.0-14-generic/kernel/drivers/vhost/vhost_net.ko': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-14-generic_3.0.0-14.23_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and the error seems to suggest I ran out of free space in a partition, but
```

 df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7              4881408    278752   3842304   7% /
udev                   1984620         4   1984616   1% /dev
tmpfs                   811360      1220    810140   1% /run
none                      5120         0      5120   0% /run/lock
none                   2028392      1100   2027292   1% /run/shm
/dev/sdb1            961432072 331873136 580720936  37% /backups
/dev/sdd1             71466400   1706820  66129296   3% /media/raptor80
/dev/sda8              2882592     72064   2664096   3% /tmp
/dev/sda1              2882592     99256   2636904   4% /boot
/dev/sda12            14647296   1759568  10913168  14% /opt
/dev/sdc1            488379392 186260600 296048280  39% /home
/dev/sda10             2928640    796896   1584360  34% /var
/dev/sda9             24413184   6880328  14825336  32% /usr
/dev/sda13            14647296        96  12521472   1% /usr/local

```

```

Linux 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

There should not be much cruft. As I recently( this month) installed this system. Thanx

---

### Post by Horatio on 2011-12-31
Well, I stumbled across a problem with btrfs. 

[http://ubuntuforums.org/showthread.php?t=1884613](http://ubuntuforums.org/showthread.php?t=1884613)
[https://bugs.launchpad.net/ubuntu/+source/btrfs/+bug/893681](https://bugs.launchpad.net/ubuntu/+source/btrfs/+bug/893681)

perhaps I should have had my mounts to show the file systems being used.
```

/dev/sda7 on / type btrfs (rw,subvol=@)
/dev/sdd1 on /media/raptor80 type ext4 (rw,commit=0)
/dev/sda8 on /tmp type ext4 (rw,commit=0)
/dev/sda1 on /boot type ext4 (rw,commit=0)
/dev/sdb1 on /backups type ext4 (rw,commit=0)
/dev/sda12 on /opt type btrfs (rw)
/dev/sdc1 on /home type btrfs (rw,subvol=@home)
/dev/sda10 on /var type btrfs (rw)
/dev/sda9 on /usr type btrfs (rw)
/dev/sda13 on /usr/local type btrfs (rw)

```

Well, unless I'm overlooking something. Then I image my only solution will be to re-install and stick with ext3 and ext4. I was just giving btrfs a spin, as it has been around for sometime.

thanx

---

### Post by Horatio on 2012-01-02
Well, I decide to try to install wine which muon( kubuntu's GUI installer), and muon work. It also seemed to have solve what ever was causing the above problem. As I just tried 
```

thann@eisbrecher:~$ sudo apt-get -f upgrade
[sudo] password for thann: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  initscripts libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0 libwebkitgtk-3.0-common sysv-rc sysvinit-utils
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.3 MB of archives.
After this operation, 12.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main sysvinit-utils amd64 2.88dsf-13.10ubuntu4.1 [63.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main sysv-rc all 2.88dsf-13.10ubuntu4.1 [44.1 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main initscripts amd64 2.88dsf-13.10ubuntu4.1 [27.5 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main libwebkitgtk-1.0-common all 1.4.3-0ubuntu4 [566 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main libwebkitgtk-1.0-0 amd64 1.4.3-0ubuntu4 [7,032 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main libwebkitgtk-3.0-common all 1.4.3-0ubuntu4 [566 kB]                                                                          
Get:7 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main libwebkitgtk-3.0-0 amd64 1.4.3-0ubuntu4 [7,029 kB]                                                                           
Fetched 15.3 MB in 9s (1,595 kB/s)                                                                                                                                                           
Preconfiguring packages ...
(Reading database ... 240060 files and directories currently installed.)
Preparing to replace sysvinit-utils 2.88dsf-13.10ubuntu4 (using .../sysvinit-utils_2.88dsf-13.10ubuntu4.1_amd64.deb) ...
Unpacking replacement sysvinit-utils ...
Preparing to replace sysv-rc 2.88dsf-13.10ubuntu4 (using .../sysv-rc_2.88dsf-13.10ubuntu4.1_all.deb) ...
Unpacking replacement sysv-rc ...
Preparing to replace initscripts 2.88dsf-13.10ubuntu4 (using .../initscripts_2.88dsf-13.10ubuntu4.1_amd64.deb) ...
Unpacking replacement initscripts ...
Preparing to replace libwebkitgtk-1.0-common 1.4.3-0ubuntu3 (using .../libwebkitgtk-1.0-common_1.4.3-0ubuntu4_all.deb) ...
Unpacking replacement libwebkitgtk-1.0-common ...
Preparing to replace libwebkitgtk-1.0-0 1.4.3-0ubuntu3 (using .../libwebkitgtk-1.0-0_1.4.3-0ubuntu4_amd64.deb) ...
Unpacking replacement libwebkitgtk-1.0-0 ...
Preparing to replace libwebkitgtk-3.0-common 1.4.3-0ubuntu3 (using .../libwebkitgtk-3.0-common_1.4.3-0ubuntu4_all.deb) ...
Unpacking replacement libwebkitgtk-3.0-common ...
Preparing to replace libwebkitgtk-3.0-0 1.4.3-0ubuntu3 (using .../libwebkitgtk-3.0-0_1.4.3-0ubuntu4_amd64.deb) ...
Unpacking replacement libwebkitgtk-3.0-0 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up sysvinit-utils (2.88dsf-13.10ubuntu4.1) ...                                                                                                                                        
Setting up sysv-rc (2.88dsf-13.10ubuntu4.1) ...                                                                                                                                               
Setting up initscripts (2.88dsf-13.10ubuntu4.1) ...                                                                                                                                           
Installing new version of config file /etc/init.d/sendsigs ...                                                                                                                                
Installing new version of config file /etc/init.d/umountroot ...                                                                                                                              
Setting up libwebkitgtk-1.0-common (1.4.3-0ubuntu4) ...                                                                                                                                       
Setting up libwebkitgtk-1.0-0 (1.4.3-0ubuntu4) ...                                                                                                                                            
Setting up libwebkitgtk-3.0-common (1.4.3-0ubuntu4) ...                                                                                                                                       
Setting up libwebkitgtk-3.0-0 (1.4.3-0ubuntu4) ...                                                                                                                                            
Processing triggers for libc-bin ...                                                                                                                                                          
ldconfig deferred processing now taking place   

```

and no more annoying message about linux-image-generic. The sad thing is that I don't know what happened. As all I could see was the progress bar move.

Maybe a good chap can explain this? I also don't know if muon could have solve this issue without installing something¿ I just have not experimented with muon much. Although for me I'll have to consider this mysteriously solved. Yay!

---

