---
title: "What is latest kernel?"
date: 2015-09-09
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2015-09-09
How do I find out the latest kernel avaliable?  

Right now I have 3.13.0-51-generic, have a 64 bit cpu, and do all updates as they come out.

Also an old laptop, 32 bit, has 3.13.0-61-generic.  All updates are done.  I know there is a 3.13.0-63-generic out there.

What's going on?

---

### Post by NathanRodriguez on 2015-09-09
I think some distros prefer an earlier most stable version than the latest bleeding edge not so tested kernel version.

---

### Post by RogerDavis on 2015-09-09
I had guessed that might be it, but how do you tell what is the latest in use for that distro?

---

### Post by Bashing-om on 2015-09-09
RogerDavis; Hello;

> 
How do I find out the latest kernel available? 

Run terminal command:
```

apt-cache show linux-generic

```

You should have :
> 
sysop@1404mini:~$ uname -r
3.13.0-63-generic

also if you are fully updated.

To make sure:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` where "dist-upgrade" will install the latest kernel.

[INDENT][INDENT][INDENT]see what tale gets told
[/INDENT][/INDENT][/INDENT]

---

### Post by RogerDavis on 2015-09-09
Thanks for that good info, but what I want to do before forcing update is to make sure whether the one I have installed on both machines is not the "cutting edge", maybe unstable one, but the LTS support kernel.

Then I'll force the update.

So how do I find the "normal" automatic "software update" kernel for each Ubuntu version, not the latest, maybe unstable one?

Thanks!

---

### Post by Bashing-om on 2015-09-09
RogerDavis; Well ..
As to "
> 
So how do I find the "normal" automatic "software update" kernel for each Ubuntu version, not the latest, maybe unstable one?

there are several ways. My preference:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Fill in the appropriate search box, and select the release; here the results for "linux-generic' for "trusty" :
[http://packages.ubuntu.com/search?keywords=linux-generic&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=linux-generic&searchon=names&suite=trusty&section=all)

[INDENT][INDENT]nice things to know
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-09-09
An ordinary dist-upgrade is not 'forcing' anything. It's doing exactly what you are asking for.
If you want to avoid 'unstable' packages, then disable your '-proposed' repository. It is already disabled by default when you install.
Bashing-om's advice is both correct and appropriate.

Here. Let's show you ALL the kernels currently in the Ubuntu repositories
```
$ rmadison linux-generic
 linux-generic | 3.2.0.23.25  | precise          | amd64, i386
 linux-generic | 3.2.0.90.104 | precise-security | amd64, i386
 linux-generic | 3.2.0.90.104 | precise-updates  | amd64, i386
 linux-generic | 3.13.0.24.28 | trusty           | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.13.0.63.71 | trusty-security  | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.13.0.63.71 | trusty-updates   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.15.14 | vivid            | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.28.27 | vivid-security   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.28.27 | vivid-updates    | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.7.7    | wily             | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.9.9    | wily-proposed    | amd64, arm64, armhf, i386, ppc64el
```
See how there is only one kernel in each repository? You choose the repository based on your version of Ubuntu.
If you are using 14.04, you should enable trusty, trusty-security, and optionally trusty-updates. Anything else will promptly break your system.
trusty-security will dist-upgrade you to 3.13.0.63. Nothing else. No 'unstable' vs. 'normal'. Nothing to guess or check. Ubuntu makes it easy...if you use the 'linux-generic' package instead of hunting for individual kernel versions.

---

### Post by RogerDavis on 2015-09-09
Interesting... So then is my "updates" misbehaving, since it's happy with 3.13.0-51-generic, showing "up to date"?  Do I need to make some settings for it?  Or is the kernel something that's supposed to chased down individually?

---

### Post by Bashing-om on 2015-09-09
RogerDavis; Well -> that is a deep subject.

Have a good read:
[https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites)

And not to be overlooked:
```

man dpkg

``` now that will gt you srambling !

It boils down that 'apt-get' will not install a new package - as in a new kernel - so we need something that will .. enter "dist-upgrade" . Now the system will not second guess you as to how you want to use your system and what you want to do. 
In the realm of kernels, you have the mandate to manage the system, removing what you know you will not use.

I have not run a GUI package manager in some years, so I can not really say what the GUI sees ... from terminal :
```

sudo apt-get update ##syncs the respective data bases
sudo apt-get upgrade ## install updates NOT new software
sudo apt-get dist-upgrade ## installs new software, as in kernels for the respective release only - has nothing to do with a release upgrade ( different command)

```
will get the job done, nicely .

so, yeah, you tell the system to install that new kernel that becomes available - in our terminal world.
Your system - on 3.13.0-51-generic - is up-to-date .. when you "dist-upgrade" to the latest kernel - presently 3.13.0-63-generic - then the system is no longer up-to-date, but the system will make it so ; because you told it to !

Out of all the things that impress me about linux, the package management system impresses me the most. The more I mess with it the more I learn the more I am impressed. There was a time when installing any software one had to chase down all the contributing libraries and related files and install them 1st .. try try again to get it right .. and try some more . --- them guys in sweaters and long beards done a good thing !


 [INDENT][INDENT]Package management .... what a concept 
[/INDENT][/INDENT]

---

### Post by RogerDavis on 2015-09-09
That's lots of info, I'll have to postpone reading it for a few days since I'm already late somewhere else.

I'll try to absorb it, or as much as I can, and reply if (probably when) I get stuck again.

Thanks!

---

### Post by dino99 on 2015-09-10
Simply be sure to get "linux-generic" installed :
****
This package will always depend on the latest complete generic Linux kernel and headers.
******

---

### Post by efflandt on 2015-09-13
Read **man apt-get** about the difference between **upgrade** and **dist-upgrade**. Some people seem to be intent on using **upgrade**, but that can hold some packages back and not upgrade everything if they need additional new packages or dependencies that do not have a version already installed. **dist-upgrade** is smarter about coordinating additional packages or changing dependencies.

---

### Post by RogerDavis on 2015-09-13
I'm slowly soaking this in, and some of this leads to a question:  Given that the packages and updates are carefully selected, I note that none of the possibles given here or at [http://packages.ubuntu.com/search?keywords=linux-generic&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=linux-generic&searchon=names&suite=trusty&section=all)  matches what my system and the updates are happy at, 3.13.0-51-generic .

This leads to a few questions:
- Why is automatic or selected software update (from desktop or applications>system tools>administration>software updater)  satisfied with 3.13.0-51-generic , when it doesn't match what I'm supposed to have by any source?  Why isn't it 3.13.0.63.71 ?
- Is my update malfunctioning?  Do I need to repair it, or ?
- What will I gain with 3.13.0.63.71 ?
- Am I risking anything from installing, or if I use 3.13.0.63.71 ?
- If I do install 3.13.0.63.71, will it foul up my updates in any way?

---

### Post by Bashing-om on 2015-09-13
RogerDavis; Well; ......

1) " - Why is automatic or selected software update (from desktop or applications>system tools>administration>software updater) satisfied with 3.13.0-51-generic " : -> package manager has no problem with  3.13.0-51 all of it's depends are currently satisfied.

2) "- Is my update malfunctioning? Do I need to repair it, or ? " -> Very distinct possibility:
```

sysop@1404mini:~$ uname -r
3.13.0-63-generic
sysop@1404mini:~$

```

3) " - What will I gain with 3.13.0.63.71 ? " -> security patches ; hardware support

4) "- Am I risking anything from installing, or if I use 3.13.0.63.71 ? " -> possible, that is why one always keeps a known good working kernel as a back up

5) " - If I do install 3.13.0.63.71, will it foul up my updates in any way? " If the installed PPAs do not have any problems should be OK .
---------------
The only way to know is to install ( whatever that takes to fix the package manager ) and see .

[INDENT][INDENT]Keep it updated 
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-09-13
> **RogerDavis said:**
> - Is my update malfunctioning? 

We can answer that after you show us the complete output of the following commands:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by RogerDavis on 2015-09-14
```
roger@roger-desktop:~$ sudo apt-get update
[sudo] password for roger: 
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://dl.google.com stable InRelease                                      
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://dl.google.com stable Release.gpg                                    
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://downloads.sourceforge.net all InRelease                             
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/main Sources                    
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://archive.canonical.com trusty Release                                
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/universe Sources                
Get:2 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]            
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://downloads.sourceforge.net all/main amd64 Packages                   
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://downloads.sourceforge.net all/main i386 Packages                    
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://downloads.sourceforge.net all/main Translation-en_US                
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://downloads.sourceforge.net all/main Translation-en                   
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en  
Ign http://extras.ubuntu.com trusty/main Translation-en            
Hit http://ppa.launchpad.net trusty/main amd64 Packages            
Hit http://us.archive.ubuntu.com trusty/universe Translation-en    
Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [234 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                     
Get:4 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,725 B] 
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [135 kB]    
Get:6 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,143 B] 
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [619 kB]
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:9 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [312 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.9 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_US              
Get:11 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [601 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en   
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [313 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 2,342 kB in 7s (296 kB/s)                                              
Reading package lists... Done

```

```
roger@roger-desktop:~$ sudo apt-get upgrade
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  python-pexpect python-renderpm python-reportlab python-reportlab-accel
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  gir1.2-gtk-3.0 libgail-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libnautilus-extension1a nautilus nautilus-data oneconf oneconf-common
  python-oneconf python3-oneconf
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,974 kB of archives.
After this operation, 6,144 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-common all 3.10.8-0ubuntu1.6 [167 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgail-3-0 amd64 3.10.8-0ubuntu1.6 [20.2 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-0 amd64 3.10.8-0ubuntu1.6 [1,960 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-gtk-3.0 amd64 3.10.8-0ubuntu1.6 [174 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-bin amd64 3.10.8-0ubuntu1.6 [18.2 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnautilus-extension1a amd64 1:3.10.1-0ubuntu9.9 [52.0 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9.9 [50.5 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus amd64 1:3.10.1-0ubuntu9.9 [481 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main oneconf-common all 0.3.7.14.04.1 [6,042 B]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-oneconf all 0.3.7.14.04.1 [19.5 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main oneconf all 0.3.7.14.04.1 [5,458 B]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python-oneconf all 0.3.7.14.04.1 [19.7 kB]
Fetched 2,974 kB in 1min 13s (40.7 kB/s)                                       
(Reading database ... 869490 files and directories currently installed.)
Preparing to unpack .../libgtk-3-common_3.10.8-0ubuntu1.6_all.deb ...
Unpacking libgtk-3-common (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libgail-3-0_3.10.8-0ubuntu1.6_amd64.deb ...
Unpacking libgail-3-0:amd64 (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libgtk-3-0_3.10.8-0ubuntu1.6_amd64.deb ...
Unpacking libgtk-3-0:amd64 (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../gir1.2-gtk-3.0_3.10.8-0ubuntu1.6_amd64.deb ...
Unpacking gir1.2-gtk-3.0 (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libgtk-3-bin_3.10.8-0ubuntu1.6_amd64.deb ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking libgtk-3-bin (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libnautilus-extension1a_1%3a3.10.1-0ubuntu9.9_amd64.deb ...
Unpacking libnautilus-extension1a (1:3.10.1-0ubuntu9.9) over (1:3.10.1-0ubuntu9.7) ...
Preparing to unpack .../nautilus-data_1%3a3.10.1-0ubuntu9.9_all.deb ...
Unpacking nautilus-data (1:3.10.1-0ubuntu9.9) over (1:3.10.1-0ubuntu9.7) ...
Preparing to unpack .../nautilus_1%3a3.10.1-0ubuntu9.9_amd64.deb ...
Unpacking nautilus (1:3.10.1-0ubuntu9.9) over (1:3.10.1-0ubuntu9.7) ...
Preparing to unpack .../oneconf-common_0.3.7.14.04.1_all.deb ...
Unpacking oneconf-common (0.3.7.14.04.1) over (0.3.7) ...
Preparing to unpack .../python3-oneconf_0.3.7.14.04.1_all.deb ...
Unpacking python3-oneconf (0.3.7.14.04.1) over (0.3.7) ...
Preparing to unpack .../oneconf_0.3.7.14.04.1_all.deb ...
Unpacking oneconf (0.3.7.14.04.1) over (0.3.7) ...
Preparing to unpack .../python-oneconf_0.3.7.14.04.1_all.deb ...
Unpacking python-oneconf (0.3.7.14.04.1) over (0.3.7) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up libgtk-3-common (3.10.8-0ubuntu1.6) ...
Setting up libgtk-3-0:amd64 (3.10.8-0ubuntu1.6) ...
Setting up libgail-3-0:amd64 (3.10.8-0ubuntu1.6) ...
Setting up gir1.2-gtk-3.0 (3.10.8-0ubuntu1.6) ...
Setting up libgtk-3-bin (3.10.8-0ubuntu1.6) ...
Setting up libnautilus-extension1a (1:3.10.1-0ubuntu9.9) ...
Setting up nautilus-data (1:3.10.1-0ubuntu9.9) ...
Setting up nautilus (1:3.10.1-0ubuntu9.9) ...
Setting up oneconf-common (0.3.7.14.04.1) ...
Setting up python3-oneconf (0.3.7.14.04.1) ...
Setting up oneconf (0.3.7.14.04.1) ...
Setting up python-oneconf (0.3.7.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for menu (2.1.46ubuntu1) ...
roger@roger-desktop:~$ 

```

It paused for a long moment at the "Unknown media type" stuff

---

### Post by ian-weisser on 2015-09-14
Seems like your package manager is working fine.

Do you have the 'linux-generic' package installed, for kernel updates?
For the 'Unknown media type' warnings, see [http://askubuntu.com/questions/39852/how-to-remove-warnings-like-unknown-media-type](http://askubuntu.com/questions/39852/how-to-remove-warnings-like-unknown-media-type)

---

### Post by RogerDavis on 2015-09-14
> **ian-weisser said:**
> Seems like your package manager is working fine.
Good to know...


Do you have the 'linux-generic' package installed, for kernel updates?
Apparently so:
```
roger@roger-desktop:~$ apt-cache show linux-generic
Package: linux-generic
Priority: optional
Section: kernel
Installed-Size: 29
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 3.13.0.63.71
Depends: linux-image-generic (= 3.13.0.63.71), linux-headers-generic (= 3.13.0.63.71)
Filename: pool/main/l/linux-meta/linux-generic_3.13.0.63.71_amd64.deb
Size: 1780
MD5sum: 879b2de341824ee5edf5111cab96138b
SHA1: 34deb126f054b8528694224392f9b79f052b4ccb
SHA256: a0aa55e4a2c445fc8e6c7e17a182ed5f283c70977eece4244ee1a1b17db78b7e
Description-en: Complete Generic Linux kernel and headers
 This package will always depend on the latest complete generic Linux kernel
 and headers.
Description-md5: 000d0a6187a93215f75bba542cc6df27
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y

``` 
So what does this tell me about what kernel I should have?  Do I need to change anything?


For the 'Unknown media type' warnings, see [http://askubuntu.com/questions/39852/how-to-remove-warnings-like-unknown-media-type](http://askubuntu.com/questions/39852/how-to-remove-warnings-like-unknown-media-type)
I can't find any of the below on my system.
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'

I have /usr/share/mime/packages, but nothing like these in there, or anywhere - I can't find them at all.  Should they be there and are missing, or ???

---

### Post by ian-weisser on 2015-09-14
> **RogerDavis said:**
> Apparently so
Er, not that way.
Apt-cache simply reads the package database. It doesn't tell you if the package is installed.
Lots of not-installed packages are in that database.

Try 'dpkg --list linux-generic' instead.


> **RogerDavis said:**
> I can't find any of the below on my system.
...
Should they be there and are missing, or ???

Yes, you already asked that. Did you see the link when I answered?

---

### Post by RogerDavis on 2015-09-14
> **ian-weisser said:**
> Er, not that way.
Apt-cache simply reads the package database. It doesn't tell you if the package is installed.
Lots of not-installed packages are in that database.

Try 'dpkg --list linux-generic' instead.

```
roger@roger-desktop:~$ dpkg --list linux-generic
dpkg-query: no packages found matching linux-generic
roger@roger-desktop:~$ 

```
Now I'm REALLY confused !  What about this:
```
roger@roger-desktop:~$ apt-cache show linux-generic
Package: linux-generic
Priority: optional
Section: kernel
Installed-Size: 29
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 3.13.0.63.71
Depends: linux-image-generic (= 3.13.0.63.71), linux-headers-generic (= 3.13.0.63.71)
Filename: pool/main/l/linux-meta/linux-generic_3.13.0.63.71_amd64.deb
Size: 1780
MD5sum: 879b2de341824ee5edf5111cab96138b
SHA1: 34deb126f054b8528694224392f9b79f052b4ccb
SHA256: a0aa55e4a2c445fc8e6c7e17a182ed5f283c70977eece4244ee1a1b17db78b7e
Description-en: Complete Generic Linux kernel and headers
 This package will always depend on the latest complete generic Linux kernel
 and headers.
Description-md5: 000d0a6187a93215f75bba542cc6df27
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```
And this:
```
roger@roger-desktop:~$ uname -r
3.13.0-51-generic
roger@roger-desktop:~$ 

```


Yes, you already asked that. Did you see the link when I answered?
If you mean ```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
I'm trying to understand what's going on assuming :
1) My update is working correctly
2) Update likes 3.13.0-51-generic just fine
3) Why I have to request the update to the kernel, it's not pushed by update?
4) Might I have something on here that is telling update to not update the kernel, and might cause problems if the kernel is updated?
Thanks!

---

### Post by ian-weisser on 2015-09-15
Please do not put your comments within someone else's quote. It confuses terribly, and it's a bit rude.


Now we seem to have enough information for a likely answer.
The simplest answer to why-am-I-not getting-kernel-updates is really simple.

1) Your package manager is not broken. It's properly updating the packages on your system.

2) You have the wrong kernel packages installed. I don't know (nor care) how you accomplished it - there are several ways. Most include a strident warning that you apparently missed.

There is NOT an update for the package 'linux-image-3.13.0.63-generic" and there never will be. The package name alone should tell you why.
There ARE frequent updates for the package 'linux-image-generic'. If you want kernel updates, you should install that package. 
Simply reinstall the 'linux-image-generic' package, and your kernel will start upgrading again.

---

### Post by RogerDavis on 2015-09-16
Sorry about the "code" stuff, still don't have the rules down clearly.

If I understand correctly, my best course of action is to :

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

which should update my kernel, and make future upgrades automatic?

Or should I just use Synaptic, selecting the generic kernel Version: 3.13.0.63.71, and it will handle the rest, dependencies, etc.?

Or how?

Thanks!

---

### Post by ian-weisser on 2015-09-16
> **RogerDavis said:**
> If I understand correctly, my best course of action is to :

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

which should update my kernel, and make future upgrades automatic?

No.
Reread post #21. Near the bottom. "Simply..."

---

### Post by RogerDavis on 2015-09-16
OK, I'm trying to take it a step at a time, and I'm still learning...  

I need to reinstall the 'linux-image-generic' package so the kernel will start upgrading again.  I'm trying to make really sure how to do that, so I don't end up with a dead or screwed-up system.

Some of the things I'm just not dead sure about :
- Is linux-image-generic (3.13.0.63.71)  exactly the same thing as Generic Linux kernel image?  Looks like it to me, but not exactly the same name...
- I'm pretty sure it applies to Trusty 14.04, but the page [http://packages.ubuntu.com/trusty/kernel/linux-image-generic](http://packages.ubuntu.com/trusty/kernel/linux-image-generic) shows linux-image-3.13.0-63-generic, Linux kernel image for version 3.13.0 on 64 bit x86 SMP  as a dependency.  Why is it a dependency if it is the real thing - so this is really confusing.
- What is the easiest, safest way to reinstall it - Synaptic, which seems to cover for my lack of precise knowledge, or by command line, where I'm not sure of the best right way?
- Do I also need linux-image-extra-3.13.0-63-generic, Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP ?  If so, what is the best way to reinstall this?  Or will this install as an update?

BTW, as you can see I'm quite cautious, so it's clear that I wouldn't go against a strident warning, so I have no idea on how I got into this situation.

Thanks for the help!

---

### Post by ian-weisser on 2015-09-16
The linux-image-generic is a *metapackage*.
A metapackage contains no code. Just a list dependencies to pull in.
Metapackages are handy because the dependencies can be changed or upgraded. The package manager will do all the changes automatically.

In this case, the kernel package name changes frequently. So Ubuntu uses a metapackage (name doesn't change) to control which kernel package (name frequently changes) should be installed.

Let's look at it the other way - every few weeks, a fresh version of the Linux kernel gets released. Each new version gets packaged...with a new version number.
Historically, some users didn't want to update the kernel. And different versions of Ubuntu use different versions of the kernel. So the version number is important! 
A metapackage is how the system ties the abstract concept of 'kernel' to the specific 'kernel version 1.2.3.4'  for your release of Ubuntu.


You can easily use Synaptic ...or ANY package manager application... to install linux-image-generic. Any package manager (except dpkg) will automatically pull in all the proper dependencies (including linux-image-extra-generic). You don't need to specify anything else beyond linux-image-generic - let the package manager do it's job. Usurping the package manager's job is the most common way to get into this situation.

---

### Post by RogerDavis on 2015-09-23
Success!!!

roger@roger-desktop:~$ uname -r
3.13.0-63-generic

Synaptic made it painless, once I was sure exactly what to do, though it was a bit confusing with the several versions of 3.13.0-63-generic.  I selected the "trusty" version.

Thanks, General!

---

### Post by ricardo39 on 2015-09-23
Thanks!

[Foros de Ubuntu]("http://www.fiuxy.com/")

---

