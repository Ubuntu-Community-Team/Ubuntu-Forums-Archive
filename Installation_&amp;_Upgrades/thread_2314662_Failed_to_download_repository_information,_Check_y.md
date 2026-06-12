---
title: "Failed to download repository information, Check your Internet Connection"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by davidallyn68 on 2016-02-22
[ubuntu noob] Recently, I've been getting an error "Failed to download repository information...Check your internet connection", and I am positive I have internet connection (i.e. this post).  I don't think it's directly affecting anything adversely, but occasionally,I will get a red caution icon in the system tray - but no other symptoms other than the dialogue.  I suppose I can go without updates for a while, but I would like my system to run properly so I'm interested in taking care of this.

I've read other posts and answering authors often request to see the output of the /etc/apt/sources.list file:

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu trusty main universe restricted
deb http://security.ubuntu.com/ubuntu/ trusty-security universe restricted main
deb http://archive.ubuntu.com/ubuntu trusty-updates universe restricted main
deb http://archive.ubuntu.com/ubuntu trusty-proposed universe restricted main
```

Is there any other information you would like to see?  Please let me know!
Thanks for any help you can provide!
-Dave

---

### Post by v3.xx on 2016-02-23
Hi david

So did you check your connection?  In terminal:

```
ping -c 4 ubuntu.com
```

And what happens if you do a terminal update?

```
sudo apt-get update
```

followed with an upgrade

```
sudo apt-get dist-upgrade
```

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by grahammechanical on 2016-02-23
We will get that failed to download repository information message if Software Updater fails to connect to even one repository. We usually can still run the update. You seem to have a conflict. Compare

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse

> deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security universe restricted main

Are you running Ubuntu 12.04 (precise) or 14.04 (trusty)? It is the same for some of the other repositories.

Regards.

---

### Post by kurt18947 on 2016-02-23
> **grahammechanical said:**
> We will get that failed to download repository information message if Software Updater fails to connect to even one repository. We usually can still run the update. You seem to have a conflict.

................................................
Regards.

A broken or offline PPA will cause that error message as well.

---

### Post by davidallyn68 on 2016-02-23
Thank you both for your answers and directions!  

 @grahammechanical,  I'm running 14.04 trusty.  I was hunting around postings yesterday and ran a "fix" from an old post - obviously it didn't fix it - and may have made it worse.  Can I simply edit the file by hand changing "precise" to "trusty"?? Or do I need to run a command to do that?  

@v3.xx  Here are the results of your direction (although I can already see that I will need to change "precise" to "trusty" before we're "clean" enough to move on (correct?):


ping -c 4 ubuntu.com results in (I think we're good there): ```
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=43 time=154 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=43 time=153 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=43 time=155 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=4 ttl=43 time=154 ms

--- ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 153.330/154.462/155.142/0.679 ms


```

sudo apt-get update

```
david@david-GA-970A-D3:~$ sudo apt-get update
[sudo] password for david: 
Get:1 http://security.ubuntu.com trusty-security InRelease [65.9 kB]
Hit http://repo.steampowered.com precise InRelease                             
Hit http://us.archive.ubuntu.com precise-security InRelease                    
Hit http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://us.archive.ubuntu.com precise-security/main Sources                 
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://us.archive.ubuntu.com precise-security/restricted Sources           
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://us.archive.ubuntu.com precise-security/universe Sources             
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://us.archive.ubuntu.com precise-security/multiverse Sources           
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://us.archive.ubuntu.com precise-security/main amd64 Packages          
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com precise-security/restricted amd64 Packages    
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://us.archive.ubuntu.com precise-security/universe amd64 Packages      
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com precise-security/multiverse amd64 Packages    
Hit http://archive.canonical.com precise/partner Translation-en                
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://us.archive.ubuntu.com precise-security/main i386 Packages           
Ign http://ppa.launchpad.net trusty Release                                    
Ign http://archive.ubuntu.com trusty InRelease                                 
Hit http://us.archive.ubuntu.com precise-security/restricted i386 Packages     
Hit http://us.archive.ubuntu.com precise-security/universe i386 Packages       
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://us.archive.ubuntu.com precise-security/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise-security/main Translation-en          
Hit http://us.archive.ubuntu.com precise-security/multiverse Translation-en    
Get:2 http://archive.ubuntu.com trusty-updates InRelease [65.9 kB]             
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://us.archive.ubuntu.com precise-security/restricted Translation-en    
Ign https://private-ppa.launchpad.net trusty Release                           
Hit http://us.archive.ubuntu.com precise-security/universe Translation-en      
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Ign https://private-ppa.launchpad.net trusty/main amd64 Packages/DiffIndex     
Hit http://us.archive.ubuntu.com precise-updates/universe Sources              
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages           
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Ign https://private-ppa.launchpad.net trusty/main i386 Packages/DiffIndex      
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Get:3 http://us.archive.ubuntu.com precise-updates/main Translation-en [412 kB]
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Get:4 http://archive.ubuntu.com trusty-proposed InRelease [65.9 kB]            
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Get:5 http://us.archive.ubuntu.com precise-updates/multiverse Translation-en [9,806 B]
Get:6 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [3,869 B]
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Get:7 http://us.archive.ubuntu.com precise-updates/universe Translation-en [163 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://archive.ubuntu.com trusty Release.gpg                 
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Get:8 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [338 kB]
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Get:9 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:10 http://archive.ubuntu.com trusty-updates/main amd64 Packages [709 kB]   
Get:11 http://archive.ubuntu.com trusty-updates/universe i386 Packages [339 kB]
Get:12 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:13 http://archive.ubuntu.com trusty-updates/main i386 Packages [688 kB]    
Get:14 http://archive.ubuntu.com trusty-updates/main Translation-en [359 kB]   
Get:15 http://archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:16 http://archive.ubuntu.com trusty-updates/universe Translation-en [180 kB]
Get:17 http://archive.ubuntu.com trusty-proposed/universe amd64 Packages [21.6 kB]
Get:18 http://archive.ubuntu.com trusty-proposed/restricted amd64 Packages [3,276 B]
Get:19 http://archive.ubuntu.com trusty-proposed/main amd64 Packages [124 kB]  
Get:20 http://archive.ubuntu.com trusty-proposed/universe i386 Packages [21.1 kB]
Get:21 http://archive.ubuntu.com trusty-proposed/restricted i386 Packages [3,285 B]
Get:22 http://archive.ubuntu.com trusty-proposed/main i386 Packages [119 kB]   
Hit http://archive.ubuntu.com trusty-proposed/main Translation-en              
Hit http://archive.ubuntu.com trusty-proposed/restricted Translation-en        
Hit http://archive.ubuntu.com trusty-proposed/universe Translation-en          
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                   
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 3,726 kB in 53s (69.0 kB/s)                                            
W: GPG error: https://private-ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E131728675254D99
W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

sudo apt-get dist-upgrade resulted in:```
david@david-GA-970A-D3:~$ sudo apt-get dist-upgrade
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra gir1.2-gtk-3.0 libgtk-3-bin libgtk-3-common
  libmm-glib0 libnautilus-extension1a liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libssh-4 linux-image-3.13.0-63-generic modemmanager
  nautilus nautilus-data oneconf oneconf-common oxideqt-codecs-extra
  python-oneconf python3-oneconf
19 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.4 MB/85.9 MB of archives.
After this operation, 171 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://security.ubuntu.com/ubuntu/ trusty-security/universe chromium-codecs-ffmpeg-extra amd64 48.0.2564.116-0ubuntu0.14.04.1.1111 [881 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libmm-glib0 amd64 1.0.0-2ubuntu1.1 [130 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-common all 3.10.8-0ubuntu1.6 [167 kB]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main libssh-4 amd64 0.6.1-0ubuntu3.3 [114 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-gtk-3.0 amd64 3.10.8-0ubuntu1.6 [174 kB]
Get:6 http://security.ubuntu.com/ubuntu/ trusty-security/main liboxideqt-qmlplugin amd64 1.12.7-0ubuntu0.14.04.1 [184 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-bin amd64 3.10.8-0ubuntu1.6 [18.2 kB]
Get:8 http://security.ubuntu.com/ubuntu/ trusty-security/main liboxideqtquick0 amd64 1.12.7-0ubuntu0.14.04.1 [264 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libnautilus-extension1a amd64 1:3.10.1-0ubuntu9.11 [52.1 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ trusty-updates/main modemmanager amd64 1.0.0-2ubuntu1.1 [473 kB]
Get:11 http://security.ubuntu.com/ubuntu/ trusty-security/main liboxideqtcore0 amd64 1.12.7-0ubuntu0.14.04.1 [29.5 MB]
Get:12 http://archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9.11 [50.7 kB]
Get:13 http://archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus amd64 1:3.10.1-0ubuntu9.11 [481 kB]
Get:14 http://archive.ubuntu.com/ubuntu/ trusty-updates/main oneconf-common all 0.3.7.14.04.1 [6,042 B]
Get:15 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python3-oneconf all 0.3.7.14.04.1 [19.5 kB]
Get:16 http://archive.ubuntu.com/ubuntu/ trusty-updates/main oneconf all 0.3.7.14.04.1 [5,458 B]
Get:17 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python-oneconf all 0.3.7.14.04.1 [19.7 kB]
Get:18 http://security.ubuntu.com/ubuntu/ trusty-security/main oxideqt-codecs-extra amd64 1.12.7-0ubuntu0.14.04.1 [885 kB]
Fetched 33.4 MB in 46s (714 kB/s)                                              
(Reading database ... 548733 files and directories currently installed.)
Preparing to unpack .../chromium-codecs-ffmpeg-extra_48.0.2564.116-0ubuntu0.14.04.1.1111_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (48.0.2564.116-0ubuntu0.14.04.1.1111) over (48.0.2564.82-0ubuntu0.14.04.1.1108) ...
Preparing to unpack .../libmm-glib0_1.0.0-2ubuntu1.1_amd64.deb ...
Unpacking libmm-glib0:amd64 (1.0.0-2ubuntu1.1) over (1.0.0-2ubuntu1) ...
Preparing to unpack .../libssh-4_0.6.1-0ubuntu3.3_amd64.deb ...
Unpacking libssh-4:amd64 (0.6.1-0ubuntu3.3) over (0.6.1-0ubuntu3.1) ...
Preparing to unpack .../linux-image-3.13.0-63-generic_3.13.0-63.104~precise1_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-63-generic (3.13.0-63.104~precise1) over (3.13.0-63.103) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-63-generic_3.13.0-63.104~precise1_amd64.deb (--unpack):
 trying to overwrite '/lib/modules/3.13.0-63-generic/kernel/mm/hwpoison-inject.ko', which is also in package linux-image-extra-3.13.0-63-generic 3.13.0-63.103
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
Preparing to unpack .../libgtk-3-common_3.10.8-0ubuntu1.6_all.deb ...
Unpacking libgtk-3-common (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../gir1.2-gtk-3.0_3.10.8-0ubuntu1.6_amd64.deb ...
Unpacking gir1.2-gtk-3.0 (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libgtk-3-bin_3.10.8-0ubuntu1.6_amd64.deb ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking libgtk-3-bin (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libnautilus-extension1a_1%3a3.10.1-0ubuntu9.11_amd64.deb ...
Unpacking libnautilus-extension1a (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.7) ...
Preparing to unpack .../modemmanager_1.0.0-2ubuntu1.1_amd64.deb ...
modemmanager stop/waiting
Unpacking modemmanager (1.0.0-2ubuntu1.1) over (1.0.0-2ubuntu1) ...
Preparing to unpack .../nautilus-data_1%3a3.10.1-0ubuntu9.11_all.deb ...
Unpacking nautilus-data (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.7) ...
Preparing to unpack .../nautilus_1%3a3.10.1-0ubuntu9.11_amd64.deb ...
Unpacking nautilus (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.7) ...
Preparing to unpack .../liboxideqt-qmlplugin_1.12.7-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqt-qmlplugin:amd64 (1.12.7-0ubuntu0.14.04.1) over (1.12.6-0ubuntu0.14.04.1) ...
Preparing to unpack .../liboxideqtquick0_1.12.7-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtquick0:amd64 (1.12.7-0ubuntu0.14.04.1) over (1.12.6-0ubuntu0.14.04.1) ...
Preparing to unpack .../liboxideqtcore0_1.12.7-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtcore0:amd64 (1.12.7-0ubuntu0.14.04.1) over (1.12.6-0ubuntu0.14.04.1) ...
Preparing to unpack .../oxideqt-codecs-extra_1.12.7-0ubuntu0.14.04.1_amd64.deb ...
Unpacking oxideqt-codecs-extra:amd64 (1.12.7-0ubuntu0.14.04.1) over (1.12.6-0ubuntu0.14.04.1) ...
Preparing to unpack .../oneconf-common_0.3.7.14.04.1_all.deb ...
Unpacking oneconf-common (0.3.7.14.04.1) over (0.3.7) ...
Preparing to unpack .../python3-oneconf_0.3.7.14.04.1_all.deb ...
Unpacking python3-oneconf (0.3.7.14.04.1) over (0.3.7) ...
Preparing to unpack .../oneconf_0.3.7.14.04.1_all.deb ...
Unpacking oneconf (0.3.7.14.04.1) over (0.3.7) ...
Preparing to unpack .../python-oneconf_0.3.7.14.04.1_all.deb ...
Unpacking python-oneconf (0.3.7.14.04.1) over (0.3.7) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-63-generic_3.13.0-63.104~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by davidallyn68 on 2016-02-23
> A broken or offline PPA will cause that error message as well.

Oh man... so I might have jumped down the rabbit hole a little too quickly :/

---

### Post by davidallyn68 on 2016-02-23
I fixed the public key error running sudo apt-key... command from [http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

---

### Post by davidallyn68 on 2016-02-23
So, I backed out the URL on the two "...failed to fetch..." errors to find there is no ...ubuntu/dists/trusty... directory.  Should those be pointing somewhere else?

W: Failed to fetch [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

but... [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists) does exist.

---

### Post by Bashing-om on 2016-02-23
davidallyn68; Hello;

IRT [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)
When we look : [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/)
One finds that natty was the last supported release . There has been no activity in years.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by davidallyn68 on 2016-02-23
> **Bashing-om said:**
> davidallyn68; Hello;

IRT [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)
When we look : [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/)
One finds that natty was the last supported release . There has been no activity in years.
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


Thanks for the info!  Interesting that this error just started a couple of weeks ago?  That means sometime recently that package was queued for updating somehow. Hmmm.  The mystery continues! :D

---

