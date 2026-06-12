---
title: "Problem installing tasksel on 18.04.4 LTS and using berryboot RaspberryPi 4"
date: 2020-04-22
forum: Installation &amp; Upgrades
---

### Post by robin5 on 2020-04-22
Rpi initially boots SD to berryboot. It then boots Ubuntu from SSD. 18.04.4 LTS runs OK.  Then i need to install tasksel.
From the log below it seems tasksel loader is expecting to find a 'normal' boot procedure not the indirect berryboot I am using.

Is there some script somewhere that needs modication to boot indirectly fromSSD?

Here is the log ...

 $ sudo apt-get install tasksel
 ubuntu@ubuntu:~$ sudo apt-get install tasksel
 Reading package lists... Done
 Building dependency tree
 Reading state information... Done
 The following additional packages will be installed:
   laptop-detect tasksel-data
 The following NEW packages will be installed:
   laptop-detect tasksel tasksel-data
 0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
 2 not fully installed or removed.
 Need to get 40.2 kB of archives.
 After this operation, 312 kB of additional disk space will be used.
 Do you want to continue? [Y/n] y
 Do you want to continue? [Y/n] y
 Get:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic/main arm64 tasksel-data all 3.34ubuntu11 [5476 B]
 Get:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic/main arm64 tasksel all 3.34ubuntu11 [28.7 kB]
 Get:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic/main arm64 laptop-detect all 0.16 [6016 B]
 Fetched 40.2 kB in 1s (49.6 kB/s)
 Preconfiguring packages ...
 Selecting previously unselected package tasksel-data.
 (Reading database ... 89091 files and directories currently installed.)
 Preparing to unpack .../tasksel-data_3.34ubuntu11_all.deb ...
 Unpacking tasksel-data (3.34ubuntu11) ...
 Selecting previously unselected package tasksel.
 Preparing to unpack .../tasksel_3.34ubuntu11_all.deb ...
 Unpacking tasksel (3.34ubuntu11) ...
 Selecting previously unselected package laptop-detect.
 Preparing to unpack .../laptop-detect_0.16_all.deb ...
 Unpacking laptop-detect (0.16) ...

On the SSD I have

[I]ubuntu@ubuntu:/boot$ ls
System.map-4.15.0-1041-raspi2  config-4.15.0-1041-raspi2  firmware  grub
ubuntu@ubuntu:/boot$ ls firmware
bootcode.bin  config.txt  fixup_cd.dat  fixup_x.dat  start_cd.elf  start_x.elf
cmdline.txt   fixup.dat   fixup_db.dat  start.elf    start_db.elf
ubuntu@ubuntu:/boot$ ls grub[/I]
grub is empty.

 
 
 Setting up linux-firmware-raspi2 (1.20190819-0ubuntu0.18.04.1) ...
 [COLOR=#c9211e]Error: missing /boot/firmware, did you forget to mount it?[/COLOR]
 [COLOR=#c9211e]dpkg: error processing package linux-firmware-raspi2 (--configure):[/COLOR]
 [COLOR=#c9211e] installed linux-firmware-raspi2 package post-installation script subprocess returned error exit status 1[/COLOR]
 
 
 Setting up u-boot-rpi:arm64 (2019.07+dfsg-1ubuntu4~18.04.1) ...
 Error: missing /boot/firmware, did you forget to mount it?
 dpkg: error processing package u-boot-rpi:arm64 (--configure):
  installed u-boot-rpi:arm64 package post-installation script subprocess returned error exit status 1
 Setting up laptop-detect (0.16) ...
 Setting up tasksel (3.34ubuntu11) ...
 Setting up tasksel-data (3.34ubuntu11) ...
 Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
 Errors were encountered while processing:
  linux-firmware-raspi2
  u-boot-rpi:arm64
 E: Sub-process /usr/bin/dpkg returned an error code (1)
 ubuntu@ubuntu:~$

---

