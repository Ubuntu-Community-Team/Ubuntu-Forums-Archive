---
title: "Ubuntu Software will not open in 20.04"
date: 2020-04-27
forum: Installation &amp; Upgrades
---

### Post by Joe_Linux on 2020-04-27
I have Ubuntu 20.04 on a 32 GB usb drive with persistence. The first time that I booted it I added some programs through Ubuntu Software, the next time that I booted it Ubuntu Software would not open. This is what I tried
```

ubuntu@ubuntu:~/Desktop$ sudo apt-get remove software-center sudo apt-get remove software-center 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'software-center' is not installed, so not removed
Package 'software-center' is not installed, so not removed
E: Unable to locate package apt-get
E: Unable to locate package remove
ubuntu@ubuntu:~/Desktop$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package software-center is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'software-center' has no installation candidate
ubuntu@ubuntu:~/Desktop$ sudo apt-get install software center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package software
E: Unable to locate package center
ubuntu@ubuntu:~/Desktop$ sudo apt-get install ubuntu-software
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  apt-config-icons gnome-software gnome-software-common
  gnome-software-plugin-snap libappstream-glib8
Suggested packages:
  apt-config-icons-hidpi gnome-software-plugin-flatpak
The following NEW packages will be installed:
  apt-config-icons gnome-software gnome-software-common
  gnome-software-plugin-snap libappstream-glib8 ubuntu-software
0 upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 6675 kB of archives.
After this operation, 13.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu focal/main amd64 apt-config-icons all 0.12.10-2 [2864 B]
Get:2 http://archive.ubuntu.com/ubuntu focal/main amd64 gnome-software-common all 3.36.0-0ubuntu3 [5559 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal/main amd64 libappstream-glib8 amd64 0.7.16-1ubuntu1 [135 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal/main amd64 gnome-software amd64 3.36.0-0ubuntu3 [895 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal/main amd64 gnome-software-plugin-snap amd64 3.36.0-0ubuntu3 [72.5 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal/universe amd64 ubuntu-software all 3.36.0-0ubuntu3 [10.7 kB]
Fetched 6675 kB in 4s (1509 kB/s)           
Selecting previously unselected package apt-config-icons.
(Reading database ... 194382 files and directories currently installed.)
Preparing to unpack .../0-apt-config-icons_0.12.10-2_all.deb ...
Unpacking apt-config-icons (0.12.10-2) ...
Selecting previously unselected package gnome-software-common.
Preparing to unpack .../1-gnome-software-common_3.36.0-0ubuntu3_all.deb ...
Unpacking gnome-software-common (3.36.0-0ubuntu3) ...
Selecting previously unselected package libappstream-glib8:amd64.
Preparing to unpack .../2-libappstream-glib8_0.7.16-1ubuntu1_amd64.deb ...
Unpacking libappstream-glib8:amd64 (0.7.16-1ubuntu1) ...
Selecting previously unselected package gnome-software.
Preparing to unpack .../3-gnome-software_3.36.0-0ubuntu3_amd64.deb ...
Unpacking gnome-software (3.36.0-0ubuntu3) ...
Selecting previously unselected package gnome-software-plugin-snap.
Preparing to unpack .../4-gnome-software-plugin-snap_3.36.0-0ubuntu3_amd64.deb ...
Unpacking gnome-software-plugin-snap (3.36.0-0ubuntu3) ...
Selecting previously unselected package ubuntu-software.
Preparing to unpack .../5-ubuntu-software_3.36.0-0ubuntu3_all.deb ...
Unpacking ubuntu-software (3.36.0-0ubuntu3) ...
Setting up libappstream-glib8:amd64 (0.7.16-1ubuntu1) ...
Setting up gnome-software-common (3.36.0-0ubuntu3) ...
Setting up apt-config-icons (0.12.10-2) ...
Setting up gnome-software (3.36.0-0ubuntu3) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu2) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.64.2-1~fakesync1) ...
Processing triggers for libc-bin (2.31-0ubuntu9) ...
Processing triggers for man-db (2.9.1-1) ...
Setting up ubuntu-software (3.36.0-0ubuntu3) ...
Setting up gnome-software-plugin-snap (3.36.0-0ubuntu3) ...
ubuntu@ubuntu:~/Desktop$ sudo apt-get remove ubuntu-software 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-software
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
After this operation, 45.1 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 194492 files and directories currently installed.)
Removing ubuntu-software (3.36.0-0ubuntu3) ...
ubuntu@ubuntu:~/Desktop$ sudo apt-get install ubuntu-software
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ubuntu-software
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/10.7 kB of archives.
After this operation, 45.1 kB of additional disk space will be used.
Selecting previously unselected package ubuntu-software.
(Reading database ... 194489 files and directories currently installed.)
Preparing to unpack .../ubuntu-software_3.36.0-0ubuntu3_all.deb ...
Unpacking ubuntu-software (3.36.0-0ubuntu3) ...
Setting up ubuntu-software (3.36.0-0ubuntu3) ...
ubuntu@ubuntu:~/Desktop$ sudo apt-get clean
ubuntu@ubuntu:~/Desktop$ sudo apt-get update
Ign:1 cdrom://Ubuntu 20.04 LTS _Focal Fossa_ - Release amd64 (20200423) focal InRelease
Hit:2 cdrom://Ubuntu 20.04 LTS _Focal Fossa_ - Release amd64 (20200423) focal Release
Hit:4 http://archive.ubuntu.com/ubuntu focal InRelease                   
Get:5 http://archive.ubuntu.com/ubuntu focal-updates InRelease [89.1 kB]       
Hit:6 http://ppa.launchpad.net/mkusb/ppa/ubuntu focal InRelease                
Get:7 http://archive.ubuntu.com/ubuntu focal/main DEP-11 48x48 Icons [98.4 kB] 
Get:8 http://archive.ubuntu.com/ubuntu focal/main DEP-11 64x64 Icons [163 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal/universe DEP-11 48x48 Icons [3016 kB]
Hit:10 http://security.ubuntu.com/ubuntu focal-security InRelease              
Get:11 http://security.ubuntu.com/ubuntu focal-security/main DEP-11 48x48 Icons [29 B]
Get:12 http://security.ubuntu.com/ubuntu focal-security/main DEP-11 64x64 Icons [29 B]
Get:13 http://security.ubuntu.com/ubuntu focal-security/universe DEP-11 48x48 Icons [29 B]
Get:14 http://security.ubuntu.com/ubuntu focal-security/universe DEP-11 64x64 Icons [29 B]
Get:15 http://archive.ubuntu.com/ubuntu focal/universe DEP-11 64x64 Icons [7794 kB]
Fetched 11.2 MB in 52s (213 kB/s)                                              
Reading package lists... Done
ubuntu@ubuntu:~/Desktop$ sudo apt-get remove gnome-software
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-software-common libappstream-glib8
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  gnome-software gnome-software-plugin-snap ubuntu-software
0 upgraded, 0 newly installed, 3 to remove and 3 not upgraded.
After this operation, 7123 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 194492 files and directories currently installed.)
Removing ubuntu-software (3.36.0-0ubuntu3) ...
Removing gnome-software-plugin-snap (3.36.0-0ubuntu3) ...
Removing gnome-software (3.36.0-0ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.64.2-1~fakesync1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu2) ...
ubuntu@ubuntu:~/Desktop$ sudo apt-get install gnome-software
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gnome-software-plugin-snap
Suggested packages:
  apt-config-icons-hidpi gnome-software-plugin-flatpak
The following NEW packages will be installed:
  gnome-software gnome-software-plugin-snap
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 968 kB of archives.
After this operation, 7078 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu focal/main amd64 gnome-software amd64 3.36.0-0ubuntu3 [895 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal/main amd64 gnome-software-plugin-snap amd64 3.36.0-0ubuntu3 [72.5 kB]
Fetched 968 kB in 2s (444 kB/s)                     
Selecting previously unselected package gnome-software.
(Reading database ... 194434 files and directories currently installed.)
Preparing to unpack .../gnome-software_3.36.0-0ubuntu3_amd64.deb ...
Unpacking gnome-software (3.36.0-0ubuntu3) ...
Selecting previously unselected package gnome-software-plugin-snap.
Preparing to unpack .../gnome-software-plugin-snap_3.36.0-0ubuntu3_amd64.deb ...
Unpacking gnome-software-plugin-snap (3.36.0-0ubuntu3) ...
Setting up gnome-software (3.36.0-0ubuntu3) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu2) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.64.2-1~fakesync1) ...
Processing triggers for man-db (2.9.1-1) ...
Setting up gnome-software-plugin-snap (3.36.0-0ubuntu3) ...
ubuntu@ubuntu:~/Desktop$ 

```  
Any help would be appreciated Thank you

---

### Post by Joe_Linux on 2020-04-27
bump

---

### Post by Dennis N on 2020-04-27
In your sequence of actions, the last thing you did was to install gnome-software. You should now find '**Software**' appearing in your application search. Open it, and you should get the Software Center.

---

### Post by Joe_Linux on 2020-04-27
Thank you

---

