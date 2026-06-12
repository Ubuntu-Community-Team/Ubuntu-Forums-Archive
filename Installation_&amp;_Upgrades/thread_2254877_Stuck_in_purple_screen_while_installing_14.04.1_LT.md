---
title: "Stuck in purple screen while installing 14.04.1 LTS 64 Bit"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by Horusius on 2014-11-30
Hello,
I am a new Ubuntu and Linux user but I have been using computer for more than 30 years and little bit experienced  therefore I prefer to solve the problems myself. I would like to share and ask as well about an issue I face when I install Ubuntu 14.04.1 (I tried 14.10, 14.04) that is stuck in purple screen and however you wait stopping the DVD, no voice, no move, nothing.... After I tried something I found how to pass the issue.

On top of the screen there is a bar and there are some icons such as network connectivity (looks Up and Down arrows), Keyboard Layout icon, volume icon, two more...

As soon as I clicked the network icon and select "wired connection 1" on the menu DVD run and install screen showed (Languages are left side of the screen, there are two selection that are Try Ubuntu, Install Ubuntu). 

My Computer is T9400 chipset, Intel mobile chipset 4 (GM45), 2GB memory, 250GB HDD, Bluray... MiniPC. I used to use Windows 7 Pro 64Bit then installed Ubuntu, then erased everything and installed Ubuntu. 

My computer is not working properly on Ubuntu now, some applications don't run, do not install...
Thanks.

---

### Post by mörgæs on 2014-12-01
Hi, welcome to the fora.

Let's begin with a general check. Please run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and post the output in CODE tags.

---

### Post by Horusius on 2014-12-04
[COLOR=#FF0000][/COLOR]Hello Morgeas,
Thanks your wishing.

[SIZE=5][COLOR=#FF0000]**You can find its first prompt post**[/COLOR][/SIZE]

Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign [[COLOR=#1155cc]http://extras.ubuntu.com[/COLOR]]("http://extras.ubuntu.com/") trusty InRelease                                  
Ign [[COLOR=#1155cc]http://archive.canonical.com[/COLOR]]("http://archive.canonical.com/") trusty InRelease                              
Hit [[COLOR=#1155cc]http://extras.ubuntu.com[/COLOR]]("http://extras.ubuntu.com/") trusty Release.gpg                                
Hit [[COLOR=#1155cc]http://archive.canonical.com[/COLOR]]("http://archive.canonical.com/") trusty Release.gpg                            
Hit [[COLOR=#1155cc]http://extras.ubuntu.com[/COLOR]]("http://extras.ubuntu.com/") trusty Release                                    
Hit [[COLOR=#1155cc]http://archive.canonical.com[/COLOR]]("http://archive.canonical.com/") trusty Release                                
Hit [[COLOR=#1155cc]http://repository.spotify.com[/COLOR]]("http://repository.spotify.com/") stable InRelease                             
Hit [[COLOR=#1155cc]http://extras.ubuntu.com[/COLOR]]("http://extras.ubuntu.com/") trusty/main Sources                               
Ign [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty InRelease                              
Hit [[COLOR=#1155cc]http://archive.canonical.com[/COLOR]]("http://archive.canonical.com/") trusty/partner Sources                        
Hit [[COLOR=#1155cc]http://repository.spotify.com[/COLOR]]("http://repository.spotify.com/") stable/non-free Sources                      
Hit [[COLOR=#1155cc]http://extras.ubuntu.com[/COLOR]]("http://extras.ubuntu.com/") trusty/main amd64 Packages                        
Hit [[COLOR=#1155cc]http://archive.canonical.com[/COLOR]]("http://archive.canonical.com/") trusty/partner amd64 Packages                 
Hit [[COLOR=#1155cc]http://repository.spotify.com[/COLOR]]("http://repository.spotify.com/") stable/non-free amd64 Packages               
Hit [[COLOR=#1155cc]http://extras.ubuntu.com[/COLOR]]("http://extras.ubuntu.com/") trusty/main i386 Packages                         
Hit [[COLOR=#1155cc]http://repository.spotify.com[/COLOR]]("http://repository.spotify.com/") stable/non-free i386 Packages                
Hit [[COLOR=#1155cc]http://archive.canonical.com[/COLOR]]("http://archive.canonical.com/") trusty/partner i386 Packages                  
Ign [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates InRelease                      
Hit [[COLOR=#1155cc]http://archive.canonical.com[/COLOR]]("http://archive.canonical.com/") trusty/partner Translation-en                 
Ign [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports InRelease                    
Ign [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security InRelease            
Ign [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed InRelease
Ign [[COLOR=#1155cc]http://repository.spotify.com[/COLOR]]("http://repository.spotify.com/") stable/non-free Translation-en_US         
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty Release.gpg                         
Ign [[COLOR=#1155cc]http://extras.ubuntu.com[/COLOR]]("http://extras.ubuntu.com/") trusty/main Translation-en_US
Ign [[COLOR=#1155cc]http://repository.spotify.com[/COLOR]]("http://repository.spotify.com/") stable/non-free Translation-en
Ign [[COLOR=#1155cc]http://extras.ubuntu.com[/COLOR]]("http://extras.ubuntu.com/") trusty/main Translation-en
Get:1 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates Release.gpg [933 B]
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports Release.gpg
Get:2 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security Release.gpg [933 B]
Get:3 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed Release.gpg [933 B]
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty Release
Get:4 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates Release [62,0 kB]
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports Release
Get:5 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security Release [62,0 kB]
Get:6 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed Release [209 kB]
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/main Sources
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/restricted Sources
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/universe Sources
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/multiverse Sources
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/main amd64 Packages
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/restricted amd64 Packages
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/universe amd64 Packages
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/multiverse amd64 Packages
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/main i386 Packages
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/restricted i386 Packages
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/universe i386 Packages
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/multiverse i386 Packages
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/main Translation-en
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/multiverse Translation-en              
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/restricted Translation-en              
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/universe Translation-en                
Get:7 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/main Sources [144 kB]        
Get:8 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/restricted Sources [1.408 B] 
Get:9 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/universe Sources [93,0 kB]   
Get:10 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/multiverse Sources [3.534 B]
Get:11 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/main amd64 Packages [371 kB]
Get:12 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/restricted amd64 Packages [5.820 B]
Get:13 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/universe amd64 Packages [222 kB]
Get:14 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/multiverse amd64 Packages [9.359 B]
Get:15 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/main i386 Packages [363 kB] 
Get:16 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/restricted i386 Packages [5.820 B]
Get:17 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/universe i386 Packages [222 kB]
Get:18 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/multiverse i386 Packages [9.567 B]
Get:19 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/main Translation-en [170 kB]
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/multiverse Translation-en      
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/restricted Translation-en      
Get:20 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-updates/universe Translation-en [112 kB]
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/main Sources                 
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/restricted Sources           
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/universe Sources             
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/multiverse Sources           
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/main amd64 Packages          
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/restricted amd64 Packages    
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/universe amd64 Packages      
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/multiverse amd64 Packages    
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/main i386 Packages           
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/restricted i386 Packages     
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/universe i386 Packages       
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/multiverse i386 Packages     
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/main Translation-en          
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/multiverse Translation-en    
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/restricted Translation-en    
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-backports/universe Translation-en      
Get:21 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/main Sources [54,1 kB]     
Get:22 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/restricted Sources [14 B]  
Get:23 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/universe Sources [17,4 kB] 
Get:24 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/multiverse Sources [700 B] 
Get:25 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/main amd64 Packages [168 kB]
Get:26 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/restricted amd64 Packages [14 B]
Get:27 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/universe amd64 Packages [73,0 kB]
Get:28 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/multiverse amd64 Packages [1.144 B]
Get:29 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/main i386 Packages [160 kB]
Get:30 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/restricted i386 Packages [14 B]
Get:31 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/universe i386 Packages [73,2 kB]
Get:32 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/multiverse i386 Packages [1.389 B]
Get:33 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/main Translation-en [82,5 kB]
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/multiverse Translation-en     
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/restricted Translation-en     
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-security/universe Translation-en       
Get:34 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/main amd64 Packages [150 kB]
Get:35 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/restricted amd64 Packages [658 B]
Get:36 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/universe amd64 Packages [24,2 kB]
Get:37 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/multiverse amd64 Packages [14 B]
Get:38 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/main i386 Packages [141 kB]
Get:39 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/restricted i386 Packages [667 B]
Get:40 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/universe i386 Packages [24,3 kB]
Get:41 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/multiverse i386 Packages [14 B]
Get:42 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/main Translation-en [58,1 kB]
Hit [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/multiverse Translation-en     
Get:43 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/restricted Translation-en [267 B]
Get:44 [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty-proposed/universe Translation-en [19,7 kB]
Ign [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/main Translation-en_US                 
Ign [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/multiverse Translation-en_US           
Ign [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/restricted Translation-en_US           
Ign [[COLOR=#1155cc]http://us.archive.ubuntu.com[/COLOR]]("http://us.archive.ubuntu.com/") trusty/universe Translation-en_US             
Fetched 3.120 kB in 23s (133 kB/s)                                             
Reading package lists... Done

[COLOR=#FF0000][SIZE=5][B]You can find its second prompt post
[/B][/SIZE][/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev multiarch-support
  python3-distupgrade tcpdump thunderbird thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 40,1 MB of archives.
After this operation, 11,3 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed/main libc6-dev amd64 2.19-0ubuntu6.5 [1.912 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed/main libc-dev-bin amd64 2.19-0ubuntu6.5 [69,0 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed/main libc6-dbg amd64 2.19-0ubuntu6.5 [3.455 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed/main libc-bin amd64 2.19-0ubuntu6.5 [1.169 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed/main libc6 amd64 2.19-0ubuntu6.5 [4.731 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed/main multiarch-support amd64 2.19-0ubuntu6.5 [4.484 B]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed/main ubuntu-release-upgrader-gtk all 1:0.220.6 [9.238 B]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed/main ubuntu-release-upgrader-core all 1:0.220.6 [23,1 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-proposed/main python3-distupgrade all 1:0.220.6 [104 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main tcpdump amd64 4.5.1-2ubuntu1.1 [355 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main thunderbird-locale-en amd64 1:31.3.0+build1-0ubuntu0.14.04.1 [346 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main thunderbird amd64 1:31.3.0+build1-0ubuntu0.14.04.1 [27,9 MB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main thunderbird-gnome-support amd64 1:31.3.0+build1-0ubuntu0.14.04.1 [8.534 B]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main thunderbird-locale-en-us all 1:31.3.0+build1-0ubuntu0.14.04.1 [9.974 B]
Fetched 40,1 MB in 1min 3s (636 kB/s)                                          
Preconfiguring packages ...
(Reading database ... 223364 files and directories currently installed.)
Preparing to unpack .../libc6-dev_2.19-0ubuntu6.5_amd64.deb ...
Unpacking libc6-dev:amd64 (2.19-0ubuntu6.5) over (2.19-0ubuntu6.3) ...
Preparing to unpack .../libc-dev-bin_2.19-0ubuntu6.5_amd64.deb ...
Unpacking libc-dev-bin (2.19-0ubuntu6.5) over (2.19-0ubuntu6.3) ...
Preparing to unpack .../libc6-dbg_2.19-0ubuntu6.5_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.19-0ubuntu6.5) over (2.19-0ubuntu6.3) ...
Preparing to unpack .../libc-bin_2.19-0ubuntu6.5_amd64.deb ...
Unpacking libc-bin (2.19-0ubuntu6.5) over (2.19-0ubuntu6.3) ...
Preparing to unpack .../libc6_2.19-0ubuntu6.5_amd64.deb ...
Unpacking libc6:amd64 (2.19-0ubuntu6.5) over (2.19-0ubuntu6.3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libc6:amd64 (2.19-0ubuntu6.5) ...
Setting up libc-bin (2.19-0ubuntu6.5) ...
(Reading database ... 223364 files and directories currently installed.)
Preparing to unpack .../multiarch-support_2.19-0ubuntu6.5_amd64.deb ...
Unpacking multiarch-support (2.19-0ubuntu6.5) over (2.19-0ubuntu6.3) ...
Setting up multiarch-support (2.19-0ubuntu6.5) ...
(Reading database ... 223364 files and directories currently installed.)
Preparing to unpack .../ubuntu-release-upgrader-gtk_1%3a0.220.6_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:0.220.6) over (1:0.220.5) ...
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a0.220.6_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:0.220.6) over (1:0.220.5) ...
Preparing to unpack .../python3-distupgrade_1%3a0.220.6_all.deb ...
Unpacking python3-distupgrade (1:0.220.6) over (1:0.220.5) ...
Preparing to unpack .../tcpdump_4.5.1-2ubuntu1.1_amd64.deb ...
Unpacking tcpdump (4.5.1-2ubuntu1.1) over (4.5.1-2ubuntu1) ...
Preparing to unpack .../thunderbird-locale-en_1%3a31.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:31.3.0+build1-0ubuntu0.14.04.1) over (1:31.2.0+build2-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird_1%3a31.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird (1:31.3.0+build1-0ubuntu0.14.04.1) over (1:31.2.0+build2-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a31.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:31.3.0+build1-0ubuntu0.14.04.1) over (1:31.2.0+build2-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-locale-en-us_1%3a31.3.0+build1-0ubuntu0.14.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:31.3.0+build1-0ubuntu0.14.04.1) over (1:31.2.0+build2-0ubuntu0.14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up libc-dev-bin (2.19-0ubuntu6.5) ...
Setting up libc6-dev:amd64 (2.19-0ubuntu6.5) ...
Setting up libc6-dbg:amd64 (2.19-0ubuntu6.5) ...
Setting up python3-distupgrade (1:0.220.6) ...
Setting up ubuntu-release-upgrader-core (1:0.220.6) ...
Setting up ubuntu-release-upgrader-gtk (1:0.220.6) ...
Setting up tcpdump (4.5.1-2ubuntu1.1) ...
Setting up thunderbird (1:31.3.0+build1-0ubuntu0.14.04.1) ...
Setting up thunderbird-locale-en (1:31.3.0+build1-0ubuntu0.14.04.1) ...
Setting up thunderbird-gnome-support (1:31.3.0+build1-0ubuntu0.14.04.1) ...
Setting up thunderbird-locale-en-us (1:31.3.0+build1-0ubuntu0.14.04.1) ...[COLOR=#FF0000][SIZE=5][/SIZE][/COLOR]

---

### Post by Horusius on 2014-12-04
Still applications which I installed are not working properly for instance; 
I installed "Spotify", "VLC Player" "Synaptic Package Manager" then run it but its icon seems on the taskbar but window does not open,
I installed "XBMC" it causes freeze the system (you have to power off)
Pre installed applications run I have tested so far

---

### Post by mörgæs on 2014-12-04
So the package system is in order.
What happens if you try to run **vlc** from the command line?

---

### Post by Horusius on 2014-12-05
Hi Morgaes,
When I run VLC through command prompt
 the message below
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x2462058] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

Also PlexMedia Command Prompt message

'/opt/plexmediaserver/Plex Media Server' 
/opt/plexmediaserver/Plex Media Server: error while loading shared libraries: libboost_system.so.1.47.0: cannot open shared object file: No such file or directory

---

### Post by mörgæs on 2014-12-05
Terminal output looks normal. 
Does the VLC application itself appear?

---

### Post by Horusius on 2014-12-05
No just its icon on taskbar when I run the VLC

---

### Post by Horusius on 2014-12-05
I am going to install 32Bit Ubuntu and try again...

---

### Post by Horusius on 2014-12-05
Hello Again,
I solved the problem on VLC, SoftwareUpdater, PlexMediaServer. XBMC The problem was Ubuntu which detected two monitors supposed my minipc was notebook and I connected a second screen. Why? I do not know so when I disable main screen VLC, softwareUpdater, XBMC and PlexMedia appear while they are working. I think it is a kind of bug of Ubuntu.

---

