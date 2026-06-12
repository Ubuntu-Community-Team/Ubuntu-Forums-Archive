---
title: "remove samba"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by tommynz1975 on 2007-11-21
A time back samba and samba common were installed, Samba never got setup and I have errors so want to remove samba fully to a later date but it wont let me..

 Samba 3.0.22 is installed with samba common 3.0.22..

The update notifier says 'Error BrokenCount > 0' Synaptic package manager says one broken package on your system.

When I right click on Samba  and click 'mark for complete removal' and then click on 'apply"  I get a popup box saying....  "E: samba: subprocess pre-removal script returned error exit status 102".. so what do I do? to fully remove samba... many many thanks :)

---

### Post by tommynz1975 on 2007-11-21
I have tried the follwing commands as root to fix the system.

 'sudo dpkg --configure -a' this gave no responce just returned to the command line.

apt-get update
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper Release
Get:4 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper-updates Release [50.9kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper/restricted Sources
Get:6 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper-updates/main Packages [252kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [130kB]
Get:8 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper-updates/restricted Packages [5825B]
Get:9 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper-updates/main Sources [70.5kB]
Get:10 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper-updates/restricted Sources [979B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [7842B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [26.0kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [979B]
Fetched 596kB in 8s (72.1kB/s)
Reading package lists... Done


apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.3) but 3.0.22-1ubuntu3.5 is installed
E: Unmet dependencies. Try using -f.
root@tom-desktop:/home/tom# sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be upgraded:
  apt apt-utils samba
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1477kB/4327kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper-updates/main apt 0.6.43.3ubuntu3 [1286kB]
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) dapper-updates/main apt-utils 0.6.43.3ubuntu3 [192kB]
Fetched 1477kB in 28s (51.6kB/s)
Preconfiguring packages ...
(Reading database ... 90282 files and directories currently installed.)
Preparing to replace apt 0.6.43.3ubuntu2 (using .../apt_0.6.43.3ubuntu3_i386.deb) ...
Unpacking replacement apt ...
Setting up apt (0.6.43.3ubuntu3) ...

(Reading database ... 90282 files and directories currently installed.)
Preparing to replace apt-utils 0.6.43.3ubuntu2 (using .../apt-utils_0.6.43.3ubuntu3_i386.deb) ...
Unpacking replacement apt-utils ...
Selecting previously deselected package samba.
Preparing to replace samba 3.0.22-1ubuntu3.3 (using .../samba_3.0.22-1ubuntu3.5_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What should i do??  many thanks...........

---

