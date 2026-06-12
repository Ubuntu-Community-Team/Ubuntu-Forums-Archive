---
title: "Installing Ktorrent"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by Jordii on 2010-03-03
```
Compiling  and installing KTorrent version 3.0.0 or later  :
 tar -xvjf ktorrent-3.X.Y.tar.bz2
cd ktorrent-3.X.Y
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
sudo make install
```That's what I followed but something goes wrong:
```
jordi@jordi-laptop:~/Downloads/ktorrent-3.3.4$ mkdir build
jordi@jordi-laptop:~/Downloads/ktorrent-3.3.4$ cd build
jordi@jordi-laptop:~/Downloads/ktorrent-3.3.4/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
The program 'cmake' is currently not installed.  You can install it by typing:
sudo apt-get install cmake
cmake: command not found
jordi@jordi-laptop:~/Downloads/ktorrent-3.3.4/build$ sudo apt-get install cmake
[sudo] password for jordi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 linux-headers-2.6.31-14 liblog4j1.2-java libcommons-cli-java
  libswt-gnome-gtk-3.4-jni flac openarena-data libcommons-lang-java
  linux-headers-2.6.31-14-generic nexuiz-music java-wrappers
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cmake-data emacsen-common libxmlrpc-core-c3
The following NEW packages will be installed:
  cmake cmake-data emacsen-common libxmlrpc-core-c3
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,117kB of archives.
After this operation, 14.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://nl.archive.ubuntu.com karmic-updates/main libxmlrpc-core-c3 1.06.27-1ubuntu6.1 [89.6kB]
Get:2 http://nl.archive.ubuntu.com karmic/main emacsen-common 1.4.19ubuntu1 [19.0kB]
Get:3 http://nl.archive.ubuntu.com karmic/main cmake-data 2.6.4-1ubuntu2 [1,141kB]
Get:4 http://nl.archive.ubuntu.com karmic/main cmake 2.6.4-1ubuntu2 [3,867kB]
Fetched 5,117kB in 3s (1,568kB/s)    
Selecting previously deselected package libxmlrpc-core-c3.
(Reading database ... 186051 files and directories currently installed.)
Unpacking libxmlrpc-core-c3 (from .../libxmlrpc-core-c3_1.06.27-1ubuntu6.1_i386.deb) ...
Selecting previously deselected package emacsen-common.
Unpacking emacsen-common (from .../emacsen-common_1.4.19ubuntu1_all.deb) ...
Selecting previously deselected package cmake-data.
Unpacking cmake-data (from .../cmake-data_2.6.4-1ubuntu2_all.deb) ...
Selecting previously deselected package cmake.
Unpacking cmake (from .../cmake_2.6.4-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up libxmlrpc-core-c3 (1.06.27-1ubuntu6.1) ...

Setting up emacsen-common (1.4.19ubuntu1) ...
emacsen-common: Handling install of emacsen flavor emacs
Ignoring install-info called from maintainer script
The package emacsen-common should be rebuild with new debhelper to get trigger support

Setting up cmake-data (2.6.4-1ubuntu2) ...
emacsen-common: Handling install of emacsen flavor emacs

Setting up cmake (2.6.4-1ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jordi@jordi-laptop:~/Downloads/ktorrent-3.3.4/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
-- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/jordi/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:2 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
```Getting sick of all the errors I'm getting with just about everything I try on Ubuntu.

---

### Post by bowens44 on 2010-03-03
Why not just install from the repositories?

---

### Post by lykeion on 2010-03-03
Looks like cmake complains about a missing C++ compiler. Before compiling any package you should install the build-essential:
```
sudo apt-get install build-essential
```
You can also easily install all the build dependencies for a specific package through the build-essential meta-package like this:
```
sudo apt-get build-dep ktorrent
```
Which will automatically install all the build dependencies for compiling ktorrent.

Then try compile again (cmake... -> make -> sudo make install)

BTW it seems other also have problems compiling latest KTorrent in Ubuntu:
[http://ktorrent.org/forum/viewtopic.php?f=2&t=3444]("http://ktorrent.org/forum/viewtopic.php?f=2&t=3444")

If you find it impossible-hard to compile a package, maybe you should stick to the already packaged Ubuntu version (just like bowens44 says). You can install it simply by:
```
sudo apt-get install ktorrent
```

---

### Post by drn on 2010-04-02
Hi i'm new to ubuntu os.. i did try to install ktorrent, i get 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ktorrent is already the newest version.
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ks305111:~# 
root@ks305111:~# 

this error i'm geting use to now lol  Errors were encountered while processing:
 acpid
 acpi-support

---

### Post by NightwishFan on 2010-04-02
Please run this command, followed by the next one.
```
sudo dpkg --configure -a
```
Then run:
```
sudo apt-get -f install
```

You perhaps should have posted this in a new thread, but I will help here anyway.

---

### Post by drn on 2010-04-02
thx NightwishFan , but wheni run the below i get  

root@ks305111:~# dpkg --configure -a
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support

This is a rented server, the support don't help me with the problem, if i mess it up i'm *ucked  

sudo dpkg --configure -a

---

### Post by NightwishFan on 2010-04-02
Try the second command as well.
```
sudo apt-get -f install
```

If that does not work run:
```
sudo apt-get install acpi-support && sudo apt-get -f install
```

---

### Post by drn on 2010-04-02
this apt-get -f install  gives me  that


root@ks305111:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ks305111:~# 

and this one 
apt-get install acpi-support && sudo apt-get -f install
gives me 

root@ks305111:~# apt-get install acpi-support && sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
acpi-support is already the newest version.
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ks305111:~# 

i'm going almost nuts on this

---

### Post by NightwishFan on 2010-04-02
That seems like a really broken configuration. I am not sure how to fix this. I will do some digging.

---

### Post by NightwishFan on 2010-04-02
Sorry for double post. Give this a try:
```
sudo aptitude purge acpid
```

---

### Post by drn on 2010-04-02
ok thx :)  

did this 
aptitude purge acpid 
root@ks305111:~# aptitude purge acpid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  acpi-support 
The following packages are unused and will be REMOVED:
  xserver-xorg-video-amd 
The following packages have been automatically kept back:
  openssh-server 
The following packages have been kept back:
  bind9-host dnsutils f-spot language-support-writing-en libbind9-30 
  libisccc30 libisccfg30 linux-headers-generic openssh-client 
The following packages will be REMOVED:
  acpid{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 242kB will be freed.
The following packages have unmet dependencies:
  acpi-support: Depends: acpid (>= 1.0.4-1ubuntu4) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
acpi-support
powermanagement-interface

Score is 188

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  laptop-mode-tools smartdimmer toshset xserver-xorg-video-amd 
The following packages have been automatically kept back:
  openssh-server 
The following packages will be automatically REMOVED:
  acpi-support powermanagement-interface 
The following packages have been kept back:
  bind9-host dnsutils f-spot language-support-writing-en libbind9-30 
  libisccc30 libisccfg30 linux-headers-generic openssh-client 
The following packages will be REMOVED:
  acpi-support acpid{p} powermanagement-interface 
0 packages upgraded, 0 newly installed, 7 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 1872kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 118653 files and directories currently installed.)
Removing powermanagement-interface ...
Removing acpi-support ...
(Reading database ... 118614 files and directories currently installed.)
Removing acpid ...
 * Stopping ACPI services...                                             [ OK ] 
Purging configuration files for acpid ...
(Reading database ... 118595 files and directories currently installed.)
Removing laptop-mode-tools ...
Removing smartdimmer ...
Removing toshset ...
Removing xserver-xorg-video-amd ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
root@ks305111:~#

now after all this, can i still reboot the server?  i did have some acpi probs on the other server  then I could not restart the server

---

### Post by NightwishFan on 2010-04-02
Yes, it should still work. Make sure you review all the stuff that went missing, and if you need it, install it back.

---

### Post by drn on 2010-04-02
now my ktorrent works :)  i did use add/remove.. it did remove it or update it..so it seems to work now  thx''

edit, it say stalled on status only, the torrent wont start

---

### Post by NightwishFan on 2010-04-02
So the files will not download or the interface does not start? If it is the former that likely has nothing to do with how it was installed.

---

### Post by drn on 2010-04-02
it wont start, just says stalled

---

### Post by NightwishFan on 2010-04-02
That has to do with your network connection. I am no big on p2p, so you perhaps should post a new thread.

---

### Post by drn on 2010-04-02
i did not have this prob on my other server.. and that one was exact like this one o have now

---

