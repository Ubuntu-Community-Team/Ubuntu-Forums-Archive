---
title: "upgrade from 14.04 to 14.10 creates dependency/configure problems"
date: 2014-11-03
forum: Installation &amp; Upgrades
---

### Post by ubuntubrian on 2014-11-03
I ran the GUI software updater to upgrade from 14.04 to14.10. At the end of the upgrade I got a message that the upgrade was complete but that there were errors. I then ran 
```
apt-get update && apt-get upgrade && apt-get dist-upgrade
```

I got lots of error messages and the upgrade aborted. I then increased the number of errors accepted to 1000 and the upgrade completed but with tons of errors and unconfigured packages:
```
ubuntu@ubuntu-laptop:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease                                      
Ign http://security.ubuntu.com utopic-security InRelease                       
Ign http://us.archive.ubuntu.com utopic InRelease                    
Ign http://archive.canonical.com utopic InRelease                    
Ign http://us.archive.ubuntu.com utopic-updates InRelease            
Hit http://security.ubuntu.com utopic-security Release.gpg           
Get:1 http://dl.google.com stable Release.gpg [198 B]                
Get:2 http://dl.google.com stable Release [1,338 B]                  
Hit http://security.ubuntu.com utopic-security Release                         
Hit http://us.archive.ubuntu.com utopic Release.gpg                            
Ign http://archive.canonical.com utopic InRelease                              
Hit http://us.archive.ubuntu.com utopic-updates Release.gpg                    
Hit http://archive.canonical.com utopic Release.gpg                    
Hit http://us.archive.ubuntu.com utopic Release  
Hit http://us.archive.ubuntu.com utopic-updates Release
Hit http://archive.canonical.com utopic Release.gpg
Hit http://archive.canonical.com utopic Release  
Get:3 http://dl.google.com stable/main amd64 Packages [469 B]           
Hit http://archive.canonical.com utopic Release                                
Hit http://security.ubuntu.com utopic-security/restricted Sources    
Get:4 http://dl.google.com stable/main i386 Packages [464 B]                   
Hit http://us.archive.ubuntu.com utopic/restricted Sources                     
Hit http://security.ubuntu.com utopic-security/main Sources                    
Hit http://us.archive.ubuntu.com utopic/main Sources                           
Hit http://security.ubuntu.com utopic-security/multiverse Sources              
Hit http://us.archive.ubuntu.com utopic/multiverse Sources                     
Hit http://security.ubuntu.com utopic-security/universe Sources                
Hit http://archive.canonical.com utopic/partner Sources                        
Hit http://us.archive.ubuntu.com utopic/universe Sources                       
Hit http://security.ubuntu.com utopic-security/main amd64 Packages             
Hit http://archive.canonical.com utopic/partner amd64 Packages                 
Hit http://us.archive.ubuntu.com utopic/main amd64 Packages                    
Hit http://security.ubuntu.com utopic-security/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com utopic/restricted amd64 Packages              
Hit http://security.ubuntu.com utopic-security/universe amd64 Packages         
Hit http://archive.canonical.com utopic/partner i386 Packages                  
Hit http://us.archive.ubuntu.com utopic/universe amd64 Packages                
Hit http://security.ubuntu.com utopic-security/multiverse amd64 Packages       
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://archive.canonical.com utopic/partner Translation-en                 
Hit http://us.archive.ubuntu.com utopic/multiverse amd64 Packages              
Hit http://security.ubuntu.com utopic-security/main i386 Packages              
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com utopic/main i386 Packages                     
Hit http://security.ubuntu.com utopic-security/restricted i386 Packages        
Hit http://archive.canonical.com utopic/partner amd64 Packages     
Hit http://us.archive.ubuntu.com utopic/restricted i386 Packages   
Hit http://security.ubuntu.com utopic-security/universe i386 Packages
Hit http://archive.canonical.com utopic/partner i386 Packages                  
Hit http://us.archive.ubuntu.com utopic/universe i386 Packages                 
Hit http://security.ubuntu.com utopic-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com utopic/multiverse i386 Packages               
Hit http://security.ubuntu.com utopic-security/main Translation-en             
Hit http://archive.canonical.com utopic/partner Translation-en
Hit http://security.ubuntu.com utopic-security/multiverse Translation-en
Hit http://security.ubuntu.com utopic-security/restricted Translation-en
Hit http://us.archive.ubuntu.com utopic/main Translation-en
Hit http://us.archive.ubuntu.com utopic/multiverse Translation-en
Hit http://us.archive.ubuntu.com utopic/restricted Translation-en
Hit http://security.ubuntu.com utopic-security/universe Translation-en
Hit http://us.archive.ubuntu.com utopic/universe Translation-en
Hit http://us.archive.ubuntu.com utopic-updates/restricted Sources
Hit http://us.archive.ubuntu.com utopic-updates/main Sources
Hit http://us.archive.ubuntu.com utopic-updates/multiverse Sources
Hit http://us.archive.ubuntu.com utopic-updates/universe Sources
Hit http://us.archive.ubuntu.com utopic-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com utopic-updates/main i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com utopic-updates/main Translation-en
Hit http://us.archive.ubuntu.com utopic-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com utopic-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com utopic-updates/universe Translation-en        
Fetched 2,469 B in 19s (124 B/s)                                               
Reading package lists... Done
ubuntu@ubuntu-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libvmime0
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
617 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 142986 package 'virtualbox-3.0':
 error in 'Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 142987 package 'virtualbox-3.0':
 error in 'Config-Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
Setting up sysv-rc (2.88dsf-41ubuntu18) ...
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 142986 package 'virtualbox-3.0':
 error in 'Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg-divert: warning: parsing file '/var/lib/dpkg/status' near line 142987 package 'virtualbox-3.0':
 error in 'Config-Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
info: Reordering boot system, log to /var/lib/insserv/run-20141103T0954.log
error: Something failed while migrating.

error: Unable to migrate to dependency based boot sequencing.

See http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot for
more information about dependency based boot sequencing. To
reattempt the migration process run 'dpkg --configure sysv-rc'.

dpkg: error processing package sysv-rc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on sysv-rc | file-rc; however:
  Package sysv-rc is not configured yet.
  Package file-rc is not installed.

dpkg: error processing package initscripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of e2fsprogs:
 e2fsprogs depends on util-linux (>= 2.15~rc1-1); however:
  Package util-linux is not configured yet.

dpkg: error processing package e2fsprogs (--configure):
 dependency problems - leaving unconfigured
Setting up x11-common (1:7.7+7ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package x11-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of procps:
 procps depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package procps (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up gpsd (3.10+dev3~d6b65b48-2) ...
Creating/updating gpsd user account...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package gpsd (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up kmod (18-1ubuntu2) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package kmod (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of module-init-tools:
 module-init-tools depends on kmod; however:
  Package kmod is not configured yet.

dpkg: error processing package module-init-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of upstart-bin:
 upstart-bin depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package upstart-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ifupdown:
 ifupdown depends on initscripts (>= 2.88dsf-25); however:
  Package initscripts is not configured yet.

dpkg: error processing package ifupdown (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up grub-common (2.02~beta2-15) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of udev:
 udev depends on util-linux (>= 2.16); however:
  Package util-linux is not configured yet.
 udev depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on module-init-tools; however:
  Package module-init-tools is not configured yet.
 initramfs-tools depends on udev (>= 147~-5); however:
  Package udev is not configured yet.
 initramfs-tools depends on util-linux (>> 2.15~rc1); however:
  Package util-linux is not configured yet.

dpkg: error processing package initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mountall:
 mountall depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package mountall (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 plymouth depends on mountall (>= 2.0); however:
  Package mountall is not configured yet.
 plymouth depends on udev (>= 166-0ubuntu4); however:
  Package udev is not configured yet.

dpkg: error processing package plymouth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of upstart:
 upstart depends on upstart-bin (= 1.13.2-0ubuntu2); however:
  Package upstart-bin is not configured yet.
 upstart depends on initscripts; however:
  Package initscripts is not configured yet.
 upstart depends on mountall; however:
  Package mountall is not configured yet.
 upstart depends on ifupdown (>= 0.6.10ubuntu5); however:
  Package ifupdown is not configured yet.

dpkg: error processing package upstart (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of friendly-recovery:
 friendly-recovery depends on upstart | systemd-sysv; however:
  Package upstart is not configured yet.
  Package systemd-sysv is not installed.

dpkg: error processing package friendly-recovery (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on udev (>= 204); however:
  Package udev is not configured yet.
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
 mdadm depends on util-linux (>= 2.15-1); however:
  Package util-linux is not configured yet.
 mdadm depends on initscripts (>= 2.88dsf-13.3); however:
  Package initscripts is not configured yet.

dpkg: error processing package mdadm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up dbus (1.8.8-1ubuntu2) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package dbus (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of consolekit:
 consolekit depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.

dpkg: error processing package consolekit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of brltty:
 brltty depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.

dpkg: error processing package brltty (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of bluez:
 bluez depends on module-init-tools; however:
  Package module-init-tools is not configured yet.
 bluez depends on udev (>= 170-1); however:
  Package udev is not configured yet.
 bluez depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing package bluez (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up cron (3.0pl1-124.1ubuntu1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: stop runlevel arguments (1) do not match cron Default-Stop values (none)
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cron (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of resolvconf:
 resolvconf depends on initscripts (>= 2.88dsf-13.10); however:
  Package initscripts is not configured yet.

dpkg: error processing package resolvconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of accountsservice:
 accountsservice depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing package accountsservice (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on dbus; however:
  Package dbus is not configured yet.
 language-selector-common depends on accountsservice (>= 0.6.29-1ubuntu6); however:
  Package accountsservice is not configured yet.

dpkg: error processing package language-selector-common (--configure):
 dependency problems - leaving unconfigured
Setting up cgmanager (0.32-4ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Service mountkernfs has to be enabled to start service cgmanager
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cgmanager (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of systemd-shim:
 systemd-shim depends on cgmanager (>= 0.32); however:
  Package cgmanager is not configured yet.

dpkg: error processing package systemd-shim (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of systemd:
 systemd depends on util-linux (>= 2.19.1-2); however:
  Package util-linux is not configured yet.
 systemd depends on initscripts (>= 2.88dsf-17); however:
  Package initscripts is not configured yet.
 systemd depends on sysv-rc; however:
  Package sysv-rc is not configured yet.
 systemd depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package systemd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd (= 208-8ubuntu8); however:
  Package systemd is not configured yet.
 libpam-systemd:amd64 depends on dbus; however:
  Package dbus is not configured yet.
 libpam-systemd:amd64 depends on systemd-shim (>= 6-4) | systemd-sysv; however:
  Package systemd-shim is not configured yet.
  Package systemd-sysv is not installed.

dpkg: error processing package libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up uuid-runtime (2.25.1-3ubuntu4) ...
No apport report written because MaxReports is reached already
                                                              insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package uuid-runtime (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up cups-browsed (1.0.61-0ubuntu2) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cups-browsed (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg: dependency problems prevent configuration of cups-daemon:
 cups-daemon depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing package dbus-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libice6:amd64:
 libice6:amd64 depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package libice6:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libice6:i386:
 libice6:i386 depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package libice6:i386 (--configure):
 dependency problems - leaving unconfigurNo apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 ed
dpkg: dependency problems prevent configuration of libsm6:amd64:
 libsm6:amd64 depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.

dpkg: error processing package libsm6:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsm6:i386:
 libsm6:i386 depends on libice6 (>= 1:1.0.0); however:
  Package libice6:i386 is not configured yet.

dpkg: error processing package libsm6:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:i386:
 libqtgui4:i386 depends on libice6 (>= 1:1.0.0); however:
  Package libice6:i386 is not configured yet.
 libqtgui4:i386 depends on libsm6; however:
  Package libsm6:i386 is not configured yet.

dpkg: error processing package libqtgui4:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:i386:
 libqt4-declaratiNo apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           ve:i386 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:i386 is not configured yet.

dpkg: error processing package libqt4-declarative:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:amd64:
 libqtgui4:amd64 depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 libqtgui4:amd64 depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package libqtgui4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:amd64:
 libqt4-declarative:amd64 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqt4-declarative:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration ofNo apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
               libqt4-designer:amd64:
 libqt4-designer:amd64 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqt4-designer:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:i386:
 libqt4-designer:i386 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:i386 is not configured yet.

dpkg: error processing package libqt4-designer:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-help:amd64:
 libqt4-help:amd64 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqt4-help:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of libqt4-scripttools:amd64:
 libqt4-scripttools:amd64 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqt4-scripttools:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-scripttools:i386:
 libqt4-scripttools:i386 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:i386 is not configured yet.

dpkg: error processing package libqt4-scripttools:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of libqt4-svg:amd64:
 libqt4-svg:amd64 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqt4-svg:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:i386:
 libqt4-svg:i386 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:i386 is not configured yet.

dpkg: error processing package libqt4-svg:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of python-qt4:
 python-qt4 depends on libqt4-declarative (>= 4:4.8.0-1~); however:
  Package libqt4-declarative:amd64 is not configured yet.
 python-qt4 depends on libqt4-designer (>= 4:4.8.0-1~); however:
  Package libqt4-designer:amd64 is not configured yet.
 python-qt4 depends on libqt4-help (>= 4:4.8.0-1~); however:
  Package libqt4-help:amd64 is not configured yet.
 python-qt4 depends on libqt4-scripttools (>= 4:4.8.0-1~); however:
  Package libqt4-scripttools:amd64 is not configured yet.
 python-qt4 depends on libqt4-svg (>= 4:4.8.0-1~); however:
  Package libqt4-svg:amd64 is not configured yet.
 python-qt4 depends on libqtgui4 (>= 4:4.8.0-1~); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-qt4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdbusmenu-qt2:amd64:
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                             libdbusmenu-qt2:amd64 depends on libqtgui4 (>= 4:4.7.0~beta2); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libdbusmenu-qt2:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdbusmenu-qt2:i386:
 libdbusmenu-qt2:i386 depends on libqtgui4 (>= 4:4.7.0~beta2); however:
  Package libqtgui4:i386 is not configured yet.

dpkg: error processing package libdbusmenu-qt2:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkdeui5:
 libkdeui5 depends on libdbusmenu-qt2; however:
  Package libdbusmenu-qt2:amd64 is not configured yet.
 libkdeui5 depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 libkdeui5 depends on libqt4-svg (>= 4:4.8.0); however:
  Package libqt4-svg:amd64 is not configured yet.
 libkdeui5 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.
 libkdeui5 depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package libkdeui5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkcmutils4:
 libkcmutils4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkcmutils4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkcmutils4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkdeclarative5:
 libkdeclarative5 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkdeclarative5 depends on libqt4-declarative (>= 4:4.8.0); however:
  Package libqt4-declarative:amd64 is not configured yet.
 libkdeclarative5 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkdeclarative5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libsolid4:
 libsolid4 depends on udev; however:
  Package udev is not configured yet.
 libsolid4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libsolid4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkio5:
 libkio5 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkio5 depends on libqt4-svg (>= 4:4.8.0); however:
  Package libqt4-svg:amd64 is not configured yet.
 libkio5 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.
 libkio5 depends on libsolid4 (= 4:4.14.1-0ubuntu1); however:
  Package libsolid4 is not configured yet.

dpkg: error processing package libkio5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkparts4:
 libkparts4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkparts4 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libkparts4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkparts4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkdewebkit5:
 libkdewebkit5 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkdewebkit5 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libkdewebkit5 depends on libkparts4 (= 4:4.14.1-0ubuntu1); however:
  Package libkparts4 is not configured yet.
 libkdewebkit5 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkdewebkit5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkdnssd4:
 libkdnssd4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.

dpkg: error processing package libkdnssd4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libknewstuff3-4:
 libknewstuff3-4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libknewstuff3-4 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libknewstuff3-4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libknewstuff3-4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libphonon4:amd64:
 libphonon4:amd64 depends on libqtgui4 (>= 4:4.8.1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libphonon4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:amd64:
 libqt4-opengl:amd64 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:amd64 is not configured yet.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing package libqt4-opengl:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:i386:
 libqt4-opengl:i386 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:i386 is not configured yet.

dpkg: error processing package libqt4-opengl:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libplasma3:
 libplasma3 depends on libkcmutils4 (= 4:4.14.1-0ubuntu1); however:
  Package libkcmutils4 is not configured yet.
 libplasma3 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libplasma3 depends on libkdewebkit5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdewebkit5 is not configured yet.
 libplasma3 depends on libkdnssd4 (= 4:4.14.1-0ubuntu1); however:
  Package libkdnssd4 is not configured yet.
 libplasma3 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libplasma3 depends on libknewstuff3-4 (= 4:4.14.1-0ubuntu1); however:
  Package libknewstuff3-4 is not configured yet.
 libplasma3 depends on libphonon4 (>= 4:4.6.0really4.3.80); however:
  Package libphonon4:amd64 is not configured yet.
 libplasma3 depends on libqt4-declarative (>= 4:4.8.0); however:
  Package libqt4-declarative:amd64 is not configured yet.
 libplasma3 depends on libqt4-opengl (>= 4:4.8.0); h
dpkg: error processing package libplasma3 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkactivities-bin:
 libkactivities-bin depends on libkcmutils4 (>= 4:4.13.2); however:
  Package libkcmutils4 is not configured yet.
 libkactivities-bin depends on libkdeclarative5 (>= 4:4.7.0); however:
  Package libkdeclarative5 is not configured yet.
 libkactivities-bin depends on libkdeui5 (>= 4:4.13.2); however:
  Package libkdeui5 is not configured yet.
 libkactivities-bin depends on libplasma3 (>= 4:4.13.2); however:
  Package libplasma3 is not configured yet.
 libkactivities-bin depends on libqt4-declarative (>= 4:4.7.0~rc1); however:
  Package libqt4-declarative:amd64 is not configured yet.
 libkactivities-bin depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkactivities-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libktexteditor4:
 libktexteditor4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libktexteditor4 depends on libkparts4 (= 4:4.14.1-0ubuntu1); however:
  Package libkparts4 is not configured yet.
 libktexteditor4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libktexteditor4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkatepartinterfaces4:
 libkatepartinterfaces4 depends on libkcmutils4 (>= 4:4.14.1); however:
  Package libkcmutils4 is not configured yet.
 libkatepartinterfaces4 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libkatepartinterfaces4 depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 libkatepartinterfaces4 depends on libknewstuff3-4 (>= 4:4.14.1); however:
  Package libknewstuff3-4 is not configured yet.
 libkatepartinterfaces4 depends on libkparts4 (>= 4:4.14.1); however:
  Package libkparts4 is not configured yet.
 libkatepartinterfaces4 depends on libktexteditor4 (>= 4:4.14.1); however:
  Package libktexteditor4 is not configured yet.
 libkatepartinterfaces4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkatepartinterfaces4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of katepart:
 katepart depends on libkatepartinterfaces4 (= 4:4.14.1-0ubuntu1); however:
  Package libkatepartinterfaces4 is not configured yet.
 katepart depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 katepart depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 katepart depends on libkparts4 (>= 4:4.14.1); however:
  Package libkparts4 is not configured yet.
 katepart depends on libktexteditor4 (>= 4:4.14.1); however:
  Package libktexteditor4 is not configured yet.
 katepart depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package katepart (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkjsembed4:
 libkjsembed4 depends on libqt4-svg (>= 4:4.8.0); however:
  Package libqt4-svg:amd64 is not configured yet.
 libkjsembed4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkjsembed4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkrosscore4:
 libkrosscore4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkrosscore4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkrosscore4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 kdelibs-bin depends on libkjsembed4 (= 4:4.14.1-0ubuntu1); however:
  Package libkjsembed4 is not configured yet.
 kdelibs-bin depends on libkrosscore4 (= 4:4.14.1-0ubuntu1); however:
  Package libkrosscore4 is not configured yet.
 kdelibs-bin depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package kdelibs-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kdoctools:
 kdoctools depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 kdoctools depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package kdoctools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt4-qt3support:amd64:
 libqt4-qt3support:amd64 depends on libqt4-designer (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-designer:amd64 is not configured yet.
 libqt4-qt3support:amd64 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqt4-qt3support:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt4-qt3support:i386:
 libqt4-qt3support:i386 depends on libqt4-designer (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-designer:i386 is not configured yet.
 libqt4-qt3support:i386 depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:i386 is not configured yet.

dpkg: error processing package libqt4-qt3support:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkde3support4:
 libkde3support4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkde3support4 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libkde3support4 depends on libkparts4 (= 4:4.14.1-0ubuntu1); however:
  Package libkparts4 is not configured yet.
 libkde3support4 depends on libqt4-qt3support (>= 4:4.8.0); however:
  Package libqt4-qt3support:amd64 is not configured yet.
 libkde3support4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkde3support4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkemoticons4:
 libkemoticons4 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libkemoticons4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkemoticons4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkfile4:
 libkfile4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkfile4 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libkfile4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.
 libkfile4 depends on libsolid4 (= 4:4.14.1-0ubuntu1); however:
  Package libsolid4 is not configured yet.

dpkg: error processing package libkfile4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkhtml5:
 libkhtml5 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkhtml5 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libkhtml5 depends on libkparts4 (= 4:4.14.1-0ubuntu1); however:
  Package libkparts4 is not configured yet.
 libkhtml5 depends on libktexteditor4 (= 4:4.14.1-0ubuntu1); however:
  Package libktexteditor4 is not configured yet.
 libkhtml5 depends on libphonon4 (>= 4:4.6.0really4.4.3); however:
  Package libphonon4:amd64 is not configured yet.
 libkhtml5 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkhtml5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpolkit-qt-1-1:
 libpolkit-qt-1-1 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.
 libpolkit-qt-1-1 depends on consolekit; however:
  Package consolekit is not configured yet.

dpkg: error processing package libpolkit-qt-1-1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of kdelibs5-plugins:
 kdelibs5-plugins depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
 kdelibs5-plugins depends on katepart; however:
  Package katepart is not configured yet.
 kdelibs5-plugins depends on kdelibs-bin (= 4:4.14.1-0ubuntu1); however:
  Package kdelibs-bin is not configured yet.
 kdelibs5-plugins depends on kdoctools (= 4:4.14.1-0ubuntu1); however:
  Package kdoctools is not configured yet.
 kdelibs5-plugins depends on libkde3support4 (= 4:4.14.1-0ubuntu1); however:
  Package libkde3support4 is not configured yet.
 kdelibs5-plugins depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 kdelibs5-plugins depends on libkdewebkit5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdewebkit5 is not configured yet.
 kdelibs5-plugins depends on libkemoticons4 (= 4:4.14.1-0ubuntu1); however:
  Package libkemoticons4 is not configured yet.
 kdelibs5-plugins depends on libkfile4 (= 4:4.14.1-0ubuntu1); 
dpkg: error processing package kdelibs5-plugins (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqapt2-runtime:
 libqapt2-runtime depends on libpolkit-qt-1-1 (>= 0.99.0); however:
  Package libpolkit-qt-1-1 is not configured yet.

dpkg: error processing package libqapt2-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-scriptengine-javascript:
No apport report written because MaxReports is reached already
                                                               plasma-scriptengine-javascript depends on libkdeui5 (>= 4:4.3.4); however:
  Package libkdeui5 is not configured yet.
 plasma-scriptengine-javascript depends on libkio5 (>= 4:4.3.4); however:
  Package libkio5 is not configured yet.
 plasma-scriptengine-javascript depends on libplasma3 (>= 4:4.7.0); however:
  Package libplasma3 is not configured yet.
 plasma-scriptengine-javascript depends on libqt4-declarative (>= 4:4.7.0~rc1); however:
  Package libqt4-declarative:amd64 is not configured yet.
 plasma-scriptengine-javascript depends on libqtgui4 (>= 4:4.6.2); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package plasma-scriptengine-javascript (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkmediaplayer4:
No apport report written because MaxReports is reached already
                                                               libkmediaplayer4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkmediaplayer4 depends on libkparts4 (= 4:4.14.1-0ubuntu1); however:
  Package libkparts4 is not configured yet.
 libkmediaplayer4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkmediaplayer4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknotifyconfig4:
 libknotifyconfig4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libknotifyconfig4 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:No apport report written because MaxReports is reached already

  Package libkio5 is not configured yet.
 libknotifyconfig4 depends on libphonon4 (>= 4:4.6.0really4.3.80); however:
  Package libphonon4:amd64 is not configured yet.
 libknotifyconfig4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libknotifyconfig4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkubuntu0:
 libkubuntu0 depends on libkio5 (>= 4:4.3.4); however:
  Package libkio5 is not configured yet.
 libkubuntu0 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkubuntu0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of libkxmlrpcclient4:
 libkxmlrpcclient4 depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.

dpkg: error processing package libkxmlrpcclient4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phonon:amd64:
 phonon:amd64 depends on libphonon4 (>= 4:4.7.80-0ubuntu2); however:
  Package libphonon4:amd64 is not configured yet.

dpkg: error processing package phonon:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on kdelibs5-plugins (>= 4:4.14.1); however:
  Package kdelibs5-plugins is not configured yet.
 kde-runtime depends on language-selector-common; however:
  Package language-selector-common is not configured yet.
 kde-runtime depends on libqapt2-runtime; however:
  Package libqapt2-runtime is not configured yet.
 kde-runtime depends on plasma-scriptengine-javascript (= 4:4.14.1-0ubuntu1); however:
  Package plasma-scriptengine-javascript is not configured yet.
 kde-runtime depends on libkcmutils4 (>= 4:4.4.95); however:
  Package libkcmutils4 is not configured yet.
 kde-runtime depends on libkdeclarative5 (>= 4:4.9.80); however:
  Package libkdeclarative5 is not configured yet.
 kde-runtime depends on libkdeui5 (>= 4:4.7.1); however:
  Package libkdeui5 is not configured yet.
 kde-runtime depends on libkdewebkit5 (>= 4:4.4.0); however:
  Package libkdewebkit5 is not configured yet.
 kde-runtime depends on libkdNo apport report written because MaxReports is reached already
           nssd4 (>= 4:4.3.4); ho
dpkg: error processing package kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-style-oxygen:
 kde-style-oxygen depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-style-oxygen depends on libkdeui5 (>= 4:4.11); however:
  Package libkdeui5 is not configured yet.
 kde-style-oxygen depends on libkio5 (>= 4:4.11); however:
  Package libkio5 is not configured yet.
 kde-style-oxygen depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package kde-style-oxygen (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime:
 kdebase-runtime depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing package kdebase-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency proNo apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              blems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on cups-daemon (>= 1.7.5-3ubuntu2); however:
  Package cups-daemon is not configured yet.

dpkg: error processing package cups-core-drivers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups:
 cups depends on cups-core-drivers (>= 1.7.5-3ubuntu2); however:
  Package cups-core-drivers is not configured yet.
 cups depends on cups-daemon (>= 1.7.5-3ubuntu2); however:
  Package cups-daemon is not configured yet.
 cups depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-hpcups:
 printer-driver-hpcups depends on cups (>= 1.4.0) | cupsddk; however:
  Package cups is not configured yet.
  Package cupsddk is not installed.
 printer-driver-hpcups depends on cups; however:
  Package cupNo apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         s is not configured yet.

dpkg: error processing package printer-driver-hpcups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on printer-driver-hpcups (= 3.14.6-1ubuntu1); however:
  Package printer-driver-hpcups is not configured yet.
 hplip depends on cups (>= 1.1.20); however:
  Package cups is not configured yet.

dpkg: error processing package hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip-gui:
 hplip-gui depends on hplip (>= 3.14.6-1ubuntu1); however:
  Package hplip is not configured yet.
 hplip-gui depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
 hplip-gui depends on python-qt4; however:
  Package python-qt4 is not configured yet.

dpkg: error processing package hplip-gui (--configure):
 dependency problems - leaving unconfiguredNo apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already

dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.14.6-1ubuntu1); however:
  Package hplip is not configured yet.

dpkg: error processing package printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-gutenprint:
 printer-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.

dpkg: error processing package printer-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-driver-gutenprint:
 cups-driver-gutenprint depends on printer-driver-gutenprint (= 5.2.10-3); however:
  Package printer-driver-gutenprint is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already

dpkg: error processing package cups-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing package evolution (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of gcr:
 gcr depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package gcr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-keyring:
 gnome-keyring depends on gcr (>= 3.4); however:
  Package gcr is not configured yet.
 gnome-keyring depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package gnome-keyring (--configure):No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnumeric:
 gnumeric depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package gnumeric (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package gconf2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.No apport report written because MaxReports is reached already


dpkg: error processing package libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:amd64:
 libgnomevfs2-0:amd64 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
 libgnomevfs2-0:amd64 depends on libgnomevfs2-common (= 1:2.24.4-6ubuntu1); however:
  Package libgnomevfs2-common is not configured yet.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing package libgnomevfs2-0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libvtk5.8:
 libvtk5.8 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libvtk5.8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libvtk5.8-qt4:
 libvtk5.8-qt4 depends on libqtgui4 (>= 4:4.8.0); however:No apport report written because MaxReports is reached already

  Package libqtgui4:amd64 is not configured yet.
 libvtk5.8-qt4 depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.

dpkg: error processing package libvtk5.8-qt4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgofigure0:
 libgofigure0 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.
 libgofigure0 depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.
 libgofigure0 depends on libvtk5.8-qt4; however:
  Package libvtk5.8-qt4 is not configured yet.

No apport report written because MaxReports is reached already
                                                              dpkg: error processing package libgofigure0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmotif-common:
 libmotif-common depends on x11-common (>= 1:7.0.0); however:
  Package x11-common is not configured yet.

dpkg: error processing package libmotif-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of libxm4:amd64:
 libxm4:amd64 depends on libmotif-common (= 2.3.4-6); however:
  Package libmotif-common is not configured yet.
 libxm4:amd64 depends on x11-common (>= 1:7.0.0); however:
  Package x11-common is not configured yet.

dpkg: error processing package libxm4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmrm4:amd64:
 libmrm4:amd64 depends on libxm4 (>= 2.3.4); however:
  Package libxm4:amd64 is not configured yet.
 libmrm4:amd64 depends on x11-common (>= 1:7.0.0); however:No apport report written because MaxReports is reached already

  Package x11-common is not configured yet.

dpkg: error processing package libmrm4:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libnjb5:amd64:
 libnjb5:amd64 depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package libnjb5:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of samba:
 samba depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba (= 2:4.1.11+dfsg-1ubuntu2); however:
  Package samba is not configured yet.

dpkg: error processing package winbind (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of libnss-winbind:amd64:
 libnss-winbind:amd64 depends on winbind (= 2:4.1.11+dfsg-1ubuntu2); however:
  Package winbind is not configured yet.

dpkg: error processing package libnss-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-winbind:amd64:
 libpam-winbind:amd64 depends on winbind (= 2:4.1.11+dfsg-1ubuntu2); however:
  Package winbind is not configured yet.

dpkg: error processing package libpam-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpoppler-qt4-4:amd64:
 libpoppler-qt4-4:amd64 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libpoppler-qt4-4:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg: dependency problems prevent configuration of libprison0:amd64:
 libprison0:amd64 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libprison0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5gui5:amd64:
 libqt5gui5:amd64 depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 libqt5gui5:amd64 depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package libqt5gui5:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of libqt5widgets5:amd64:
 libqt5widgets5:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.

dpkg: error processing package libqt5widgets5:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5opengl5:amd64:
No apport report written because MaxReports is reached already
                                                               libqt5opengl5:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 libqt5opengl5:amd64 depends on libqt5widgets5 (>= 5.3.0); however:
  Package libqt5widgets5:amd64 is not configured yet.

dpkg: error processing package libqt5opengl5:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt5quick5:amd64:
 libqt5quick5:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 libqt5quick5:amd64 depends on libqt5gui5 (>= 5.2.0); however:
  Package libqt5gui5:amd64 is not configured yet.

dpkg: error processing package libqt5quick5:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt53d5:amd64:
 libqt53d5:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 libqt53d5:amd64 depends on libqt5opengl5 (>= 5.0.2) | libqt5opengl5-gles (>= 5.0.2); however:
  Package libqt5opengl5:amd64 is not configured yet.
  Package libqt5opengl5-gles is not installed.
 libqt53d5:amd64 depends on libqt5quick5 (>= 5.2.0) | libqt5quick5-gles (>= 5.2.0); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.
 libqt53d5:amd64 depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:amd64 is not configured yet.

dpkg: error processing package libqt53d5:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5multimedia5:amd64:
 libqt5multimedia5:amd64 depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:amd64 is not configured yet.No apport report written because MaxReports is reached already

  Package libqt5gui5-gles is not installed.

dpkg: error processing package libqt5multimedia5:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5feedback5:amd64:
 libqt5feedback5:amd64 depends on libqt5multimedia5 (>= 5.0.2); however:
  Package libqt5multimedia5:amd64 is not configured yet.

dpkg: error processing package libqt5feedback5:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of libqt5location5:amd64:
 libqt5location5:amd64 depends on libqt53d5 (>= 5.0~git20130731) | libqt53d5-gles (>= 5.0~git20130731); however:
  Package libqt53d5:amd64 is not configured yet.
  Package libqt53d5-gles is not installed.
 libqt5location5:amd64 depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 libqt5location5:amd64 depends on libqt5opengl5 (>= 5.0.2) | libqt5opengl5-gles (>= 5.0.2); however:
  Package libqt5opengl5:amd64 is not configured yet.
  Package libqt5opengl5-gles is not installed.
 libqt5location5:amd64 depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:amd64 is not configured yet.

dpkg: error processing package libqt5location5:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5printsupport5:amd64:No apport report written because MaxReports is reached already

 libqt5printsupport5:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 libqt5printsupport5:amd64 depends on libqt5widgets5 (>= 5.3.0); however:
  Package libqt5widgets5:amd64 is not configured yet.

dpkg: error processing package libqt5printsupport5:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5svg5:amd64:
 libqt5svg5:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 libqt5svg5:amd64 depends on libqt5widgets5 (>= 5.3.0); however:
  Package libqt5widgets5:amd64 is not configured yet.
No apport report written because MaxReports is reached already

dpkg: error processing package libqt5svg5:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt5webkit5:amd64:
 libqt5webkit5:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 libqt5webkit5:amd64 depends on libqt5opengl5 (>= 5.0.2) | libqt5opengl5-gles (>= 5.0.2); however:
  Package libqt5opengl5:amd64 is not configured yet.
  Package libqt5opengl5-gles is not installed.
 libqt5webkit5:amd64 depends on libqt5printsupport5 (>= 5.0.2); however:
  Package libqt5printsupport5:amd64 is not configured yet.
 libqt5webkit5:amd64 depends on libqt5quick5 (>= 5.2.0) | libqt5quick5-gles (>= 5.2.0); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.
 libqt5webkit5:amd64 depends on libqt5widgets5 (>= 5.2.0); however:
  Package libqt5widgets5:amd64 is not configured yet.

dpkg: error processing package libqt5webkit5:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libuil4:amd64:
 libuil4:amd64 depends on libmrm4 (>= 2.3.4); however:
  Package libmrm4:amd64 is not configured yet.
 libuil4:amd64 depends on libxm4 (>= 2.3.4); however:
  Package libxm4:amd64 is not configured yet.
 libuil4:amd64 depends on x11-common (>= 1:7.0.0); however:
  Package x11-common is not configured yet.

dpkg: error processing package libuil4:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwxgtk2.8-0:amd64:
 libwxgtk2.8-0:amd64 depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package libwxgtk2.8-0:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwxgtk-media2.8-0:amd64:
 libwxgtk-media2.8-0:amd64 depends on libwxgtk2.8-0 (>= 2.8.12.1+dfsg2); however:
  Package libwxgtk2.8-0:amd64 is not configured yet.

dpkg: error processing package libwxgtk-media2.8-0:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwxgtk3.0-0:amd64:
 libwxgtk3.0-0:amd64 depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package libwxgtk3.0-0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxgtk-media3.0-0:amd64:
No apport report written because MaxReports is reached already
                                                               libwxgtk-media3.0-0:amd64 depends on libwxgtk3.0-0 (>= 3.0.1); however:
  Package libwxgtk3.0-0:amd64 is not configured yet.

dpkg: error processing package libwxgtk-media3.0-0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxsvg2:amd64:
 libwxsvg2:amd64 depends on libwxgtk3.0-0 (>= 3.0.1); however:
  Package libwxgtk3.0-0:amd64 is not configured yet.

dpkg: error processing package libwxsvg2:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxbae4m:amd64:
 libxbae4m:amd64 depends on libxm4 (>= 2.3.4); however:
  Package libxm4:amd64 is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already

dpkg: error processing package libxbae4m:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxmhtml1.1:amd64:
 libxmhtml1.1:amd64 depends on libxm4 (>= 2.3.4); however:
  Package libxm4:amd64 is not configured yet.

dpkg: error processing package libxmhtml1.1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxvmc1:amd64:
 libxvmc1:amd64 depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package libxvmc1:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.

dpkg: error processing package apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lightdm:
 lightdm depends on dbus; however:
  Package dbus is not configured yet.
 lightdm depends on plymouth (>= 0.8.8-0ubuntu18); however:
  Package plymouth is not configured yet.No apport report written because MaxReports is reached already


dpkg: error processing package lightdm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-3.16.0-24-generic:
 linux-image-3.16.0-24-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
 linux-image-3.16.0-24-generic depends on module-init-tools (>= 3.3-pre11-4ubuntu3); however:
  Package module-init-tools is not configured yet.

dpkg: error processing package linux-image-3.16.0-24-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on initscripts (>= 2.88dsf-13.3); however:
  Package initscripts is not configured yet.

dpkg: error processing package mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of wpasupplicant:
 wpasupplicant depends on initscripts (>= 2.88dsf-13.3); however:
  Package initscripts is not configured yet.

dpkg: error processing package wpasupplicant (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on wpasupplicant (>= 0.7.3-1); however:
  Package wpasupplicant is not configured yet.
 network-manager depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.
 network-manager depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package network-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ppp:
 ppp depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package ppp (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qml-module-qtquick2:amd64:
 qml-module-qtquick2:amd64 depends on libqt5quick5 (>= 5.0.2) | libqt5quick5-gles (>= 5.0.2); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.

dpkg: error processing package qml-module-qtquick2:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qml-module-qtgraphicaleffects:amd64:
 qml-module-qtgraphicaleffects:amd64 depends on qml-module-qtquick2; however:
  Package qml-module-qtquick2:amd64 is not configured yet.

dpkg: error processing package qml-module-qtgraphicaleffects:amd64 (--configure):
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                             dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qml-module-qtquick-privatewidgets:amd64:
 qml-module-qtquick-privatewidgets:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 qml-module-qtquick-privatewidgets:amd64 depends on libqt5quick5 (>= 5.2.0) | libqt5quick5-gles (>= 5.2.0); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.
 qml-module-qtquick-privatewidgets:amd64 depends on libqt5widgets5 (>= 5.2.0); however:
  Package libqt5widgets5:amd64 is not configured yet.

dpkg: error processing package qml-module-qtquick-privatewidgets:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qml-module-qtquick-dialogs:amd64:
 qml-module-qtquick-dialogs:amd64 depends on qml-module-qtquick-privatewidgets; however:
  Package qml-module-qtquick-privatewidgets:amd64 is not configured yet.
 qml-module-qtquick-dialogs:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 qml-module-qtquick-dialogs:amd64 depends on libqt5quick5 (>= 5.2.0) | libqt5quick5-gles (>= 5.2.0); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.

dpkg: error processing package qml-module-qtquick-dialogs:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qml-module-qtquick-window2:amd64:
 qml-module-qtquick-window2:amd64 depends on libqt5quick5 (>= 5.0.2) | libqt5quick5-gles (>= 5.0.2); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.

dpkg: error processing package qml-module-qtquick-window2:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qml-module-qtwebkit:amd64:
 qml-module-qtwebkit:amd64 depends on libqt5quick5 (>= 5.2.0) | libqt5quick5-gles (>= 5.2.0); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.
 qml-module-qtwebkit:amd64 depends on libqt5webkit5 (>= 5.0.2); however:
  Package libqt5webkit5:amd64 is not configured yet.

dpkg: error processing package qml-module-qtwebkit:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qtdeclarative5-qtfeedback-plugin:amd64:
 qtdeclarative5-qtfeedback-plugin:amd64 depends on libqt5feedback5; however:
  Package libqt5feedback5:amd64 is not configured yet.

dpkg: error processing package qtdeclarative5-qtfeedback-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of liboxideqtcore0:amd64:
 liboxideqtcore0:amd64 depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.

dpkg: error processing package liboxideqtcore0:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of liboxideqt-qmlplugin:amd64:
 liboxideqt-qmlplugin:amd64 depends on liboxideqtcore0 (= 1.2.5-0ubuntu1); however:
  Package liboxideqtcore0:amd64 is not configured yet.
 liboxideqt-qmlplugin:amd64 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 liboxideqt-qmlplugin:amd64 depends on libqt5quick5 (>= 5.2.0) | libqt5quick5-gles (>= 5.2.0); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.

dpkg: error processing package liboxideqt-qmlplugin:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-dialogs-plugin:amd64:
 qtdeclarative5-dialogs-plugin:amd64 depends on qml-module-qtquick-dialogs; however:No apport report written because MaxReports is reached already

  Package qml-module-qtquick-dialogs:amd64 is not configured yet.

dpkg: error processing package qtdeclarative5-dialogs-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-qtquick2-plugin:amd64:
 qtdeclarative5-qtquick2-plugin:amd64 depends on qml-module-qtquick2; however:
  Package qml-module-qtquick2:amd64 is not configured yet.

dpkg: error processing package qtdeclarative5-qtquick2-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt5qml-graphicaleffects:
 libqt5qml-graphicaleffects depends on qml-module-qtgraphicaleffects; however:
  Package qml-module-qtgraphicaleffects:amd64 is not configured yet.

dpkg: error processing package libqt5qml-graphicaleffects (--configure):No apport report written because MaxReports is reached already
                                                      No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qtdeclarative5-window-plugin:amd64:
 qtdeclarative5-window-plugin:amd64 depends on qml-module-qtquick-window2; however:
  Package qml-module-qtquick-window2:amd64 is not configured yet.

dpkg: error processing package qtdeclarative5-window-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64:
 qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 depends on qml-module-qtgraphicaleffects | libqt5qml-graphicaleffects; however:
  Package qml-module-qtgraphicaleffects:amd64 is not configured yet.
  Package libqt5qml-graphicaleffects is not configured yet.
 qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 depends on libqt5svg5 (>= 5.0.2); however:
  Package libqt5svg5:amd64 is not configured yet.
 qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 depends on qml-module-qtquick2 | qtdeclarative5-qtquick2-plugin; however:
  Package qml-module-qtquick2:amd64 is not configured yet.
  Package qtdeclarative5-qtquick2-plugin:amd64 is not configured yet.
 qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 depends on qml-module-qtquick-window2 | qtdeclarative5-window-plugin; however:
  Package qml-module-qtquick-window2:amd64 is not configured yet.
  Package qtdeclarative5-window-plugin:amd64 is not configured yet.
 qtdeclarative5-ubuntu-ui
dpkg: error processing package qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qtdeclarative5-ubuntu-web-plugin:amd64:
 qtdeclarative5-ubuntu-web-plugin:amd64 depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 qtdeclarative5-ubuntu-web-plugin:amd64 depends on libqt5quick5 (>= 5.0.2) | libqt5quick5-gles (>= 5.0.2); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.
 qtdeclarative5-ubuntu-web-plugin:amd64 depends on liboxideqt-qmlplugin (>= 1.0.2); however:
  Package liboxideqt-qmlplugin:amd64 is not configured yet.
 qtdeclarative5-ubuntu-web-plugin:amd64 depends on qtdeclarative5-qtquick2-plugin; however:
  Package qtdeclarative5-qtquick2-plugin:amd64 is not configured yet.
 qtdeclarative5-ubuntu-web-plugin:amd64 depends on qtdeclarative5-ubuntu-ui-toolkit-plugin; however:
  Package qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 is not configured yet.
 qtdeclarative5-ubuntu-
dpkg: error processing package qtdeclarative5-ubuntu-web-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64:
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64 depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64 depends on libqt5quick5 (>= 5.0.2) | libqt5quick5-gles (>= 5.0.2); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64 depends on qml-module-qtwebkit; however:
  Package qml-module-qtwebkit:amd64 is not configured yet.
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64 depends on qtdeclarative5-qtquick2-plugin; however:
  Package qtdeclarative5-qtquick2-plugin:amd64 is not configured yet.
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64 depends on qtdeclarative5-ubuntu-ui-toolkit-plugin; however:
  Package qtdeclarative5-ubuntu
dpkg: error processing package qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of webbrowser-app:
 webbrowser-app depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 webbrowser-app depends on libqt5quick5 (>= 5.0.2) | libqt5quick5-gles (>= 5.0.2); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.
 webbrowser-app depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:amd64 is not configured yet.
 webbrowser-app depends on liboxideqt-qmlplugin (>= 1.1); however:
  Package liboxideqt-qmlplugin:amd64 is not configured yet.
 webbrowser-app depends on qtdeclarative5-dialogs-plugin; however:
  Package qtdeclarative5-dialogs-plugin:amd64 is not configured yet.
 webbrowser-app depends on qtdeclarative5-qtquick2-plugin; however:
  Package qtdeclarative5-qtquick2-plugin:amd64 is not configured yet.
 webbrowser-app depends on qtdeclarative5-ubuntu-ui-toolkit-plugin; howe
dpkg: error processing package webbrowser-app (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qtgstreamer-plugins:amd64:
 qtgstreamer-plugins:amd64 depends on libqt4-opengl (>= 4:4.8.1); however:
  Package libqt4-opengl:amd64 is not configured yet.
 qtgstreamer-plugins:amd64 depends on libqtgui4 (>= 4:4.8.1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package qtgstreamer-plugins:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xfonts-encodings:
 xfonts-encodings depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package xfonts-encodings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xfonts-utils:
 xfonts-utils depends on x11-common; however:
  Package x11-common is not configured yet.No apport report written because MaxReports is reached already

 xfonts-utils depends on xfonts-encodings; however:
  Package xfonts-encodings is not configured yet.

dpkg: error processing package xfonts-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ttf-mscorefonts-installer:
 ttf-mscorefonts-installer depends on xfonts-utils; however:
  Package xfonts-utils is not configured yet.

No apport report written because MaxReports is reached already
                                                              dpkg: error processing package ttf-mscorefonts-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alsa-utils:
 alsa-utils depends on kmod (>= 17-1~); however:
  Package kmod is not configured yet.

dpkg: error processing package alsa-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on udev (>= 204-0ubuntu4~); however:
  Package udev is not configured yet.
 ubuntu-drivers-common depends on alsa-utils; however:
  Package alsa-utils is not configured yet.
 ubuntu-drivers-common depends on kmod | module-init-tools; however:
  Package kmod is not configured yet.
  Package module-init-tools is not configured yet.

dpkg: error processing package ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
Setting up gnustep-base-runtime (1.24.6-2ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package gnustep-base-runtime (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of unar:
 unar depends on gnustep-base-runtime (>= 1.24.0); however:
  Package gnustep-base-runtime is not configured yet.

dpkg: error processing package unar (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up binfmt-support (2.1.5-1) ...
update-binfmts: warning: current package is openjdk-7, but binary format already installed by openjdk-6
update-binfmts: warning: current package is mono-runtime, but binary format already installed by mono-common
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package binfmt-support (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on binfmt-support (>= 1.1.2); however:
  Package binfmt-support is not configured yet.No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already

 wine1.6 depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package wine1.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6-i386:
 wine1.6-i386 depends on wine1.6:any (= 1:1.6.2-0ubuntu6); however:
  Package wine1.6 is not configured yet.

dpkg: error processing package wine1.6-i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xfce4-session:
 xfce4-session depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 xfce4-session depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package xfce4-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-ubuntu-sso-client:
 python-ubuntu-sso-client depends on gnome-keyring; however:
  Package gnome-keyring is not configured yetNo apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         No apport report written because MaxReports is reached already
                                                                       .

dpkg: error processing package python-ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-sso-client:
 ubuntu-sso-client depends on python-ubuntu-sso-client (= 13.10-0ubuntu9); however:
  Package python-ubuntu-sso-client is not configured yet.

dpkg: error processing package ubuntu-sso-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-sso-client-qt:
 ubuntu-sso-client-qt depends on python-qt4; however:
  Package python-qt4 is not configured yet.
 ubuntu-sso-client-qt depends on python-ubuntu-sso-client (= 13.10-0ubuntu9); however:
  Package python-ubuntu-sso-client is not configured yet.
 ubuntu-sso-client-qt depends on ubuntu-sso-client (= 13.10-0ubuntu9); however:
  Package ubuntu-sso-client is not configured yet.

dpkg: error processing package ubuntu-sso-client-qt (--configure):
 dependency problems - leaving unconfigured
SettinNo apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  g up keyboard-configuration (1.70ubuntu9) ...
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.
 console-setup depends on initramfs-tools (>= 0.85eubuntu12); however:
  Package initramfs-tools is not configured yet.

dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of rsyslog:
 rsyslog depends on initscripts (>= 2.88dsf-13.3); however:
  Package initscripts is not configured yet.

dpkg: error processing package rsyslog (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
 ubuntu-minimal depends on ifupdown; however:
  Package ifupdown is not configured yet.
 ubuntu-minimal depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 ubuntu-minimal depends on kmod; however:
  Package kmod is not configured yet.
 ubuntu-minimal depends on procps; however:
  Package procps is not configured yet.
 ubuntu-minimal depends on resolvconf; however:
  Package resolvconf is not configured yet.
 ubuntu-minimal depends on rsyslog; however:
  Package rsyslog is not configured yet.
 ubuntu-minimal depends on udev; however:
  Package udev is not configured yet.
 ubuntu-minimal depends on upstart; however:
  Package upstart is not configured yet.

dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up irqbalance (1.0.6-2ubuntu1) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package irqbalance (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth; however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pppoeconf:
 pppoeconf depends on ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0); however:
  Package ppp is not configured yet.
  Package pppoe is not installed.
 pppoeconf depends on ppp (>= 2.4.1.uus2-4); however:
  Package ppp is not configured yet.
 pppoeconf depends on ifupdown (>= 0.7.44~); however:
  Package ifupdown is not configured yet.

dpkg: error processing package pppoeconf (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up rsync (3.1.1-2) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package rsync (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on cron; however:
  Package cron is not configured yet.
 ubuntu-standard depends on language-selector-common; however:
  Package language-selector-common is not configured yet.
 ubuntu-standard depends on rsync; however:
  Package rsync is not configured yet.

dpkg: error processing package ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up ufw (0.34~rc-0ubuntu4) ...
No apport report written because MaxReports is reached already
                                                              dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142986 package 'virtualbox-3.0':
 error in 'Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142987 package 'virtualbox-3.0':
 error in 'Config-Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142986 package 'virtualbox-3.0':
 error in 'Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142987 package 'virtualbox-3.0':
 error in 'Config-Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142986 package 'virtualbox-3.0':
 error in 'Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142987 package 'virtualbox-3.0':
 error in 'Config-Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142986 package 'virtualbox-3.0':
 error in 'Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142987 package 'virtualbox-3.0':
 error in 'Config-Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ufw (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of empathy:
 empathy depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package empathy (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mcp-account-manager-uoa:
 mcp-account-manager-uoa depends on empathy (= 3.8.6-0ubuntu13); however:
  Package empathy is not configured yet.

dpkg: error processing package mcp-account-manager-uoa (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-aim:
 account-plugin-aim depends on empathy (= 3.8.6-0ubuntu13); however:
  Package empathy is not configured yet.
 account-plugin-aim depends on mcp-account-manager-uoa; however:
  Package mcp-account-manager-uoa is not configured yet.

dpkg: error processing package account-plugin-aim (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of signon-ui-x11:
 signon-ui-x11 depends on libqt5gui5 (>= 5.2.0) | libqt5gui5-gles (>= 5.2.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 signon-ui-x11 depends on libqt5quick5 (>= 5.0.2) | libqt5quick5-gles (>= 5.0.2); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.
 signon-ui-x11 depends on libqt5webkit5 (>= 5.2.0); however:
  Package libqt5webkit5:amd64 is not configured yet.
 signon-ui-x11 depends on libqt5widgets5 (>= 5.2.0); however:
  Package libqt5widgets5:amd64 is not configured yet.

dpkg: error processing package signon-ui-x11 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of signon-ui:
 signon-ui depends on signon-ui-x11 | ubuntu-system-settings-online-accounts (>= 0.4); however:
  Package signon-ui-x11 is not configured yet.
  Package ubuntu-system-settings-online-accounts is not installed.

dpkg: error processing package signon-ui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of signon-plugin-oauth2:
 signon-plugin-oauth2 depends on signon-ui; however:No apport report written because MaxReports is reached already

  Package signon-ui is not configured yet.

dpkg: error processing package signon-plugin-oauth2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libaccount-plugin-generic-oauth:
 libaccount-plugin-generic-oauth depends on signon-plugin-oauth2; however:
  Package signon-plugin-oauth2 is not configured yet.

dpkg: error processing package libaccount-plugin-generic-oauth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-facebook:
 account-plugin-facebook depends on libaccount-plugin-generic-oauth | ubuntu-system-settings-online-accounts; however:
  Package libaccount-plugin-generic-oauth is not configured yet.
  Package ubuntu-system-settings-online-accounts is not installed.

dpkg: error processing package account-plugin-facebook (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-flickr:
 account-plugin-flickr depends on libaccount-plugin-generic-oauth | ubuntu-system-settings-online-accounts; however:
  Package libaccount-plugin-generic-oauth is not configured yet.
  Package ubuntu-system-settings-online-accounts is not installed.

dpkg: error processing package account-plugin-flickr (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libaccount-plugin-google:
 libaccount-plugin-google depends on signon-plugin-oauth2; however:
  Package signon-plugin-oauth2 is not configured yet.

dpkg: error processing package libaccount-plugin-google (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-google:
 account-plugin-google depends on libaccount-plugin-google | ubuntu-system-settings-online-accounts; however:
  Package libaccount-plugin-google is not configured yet.
  Package ubuntu-system-settings-online-accounts is not installed.

dpkg: error processing package account-plugin-google (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-identica:
 account-plugin-identica depends on libaccount-plugin-generic-oauth; however:
  Package libaccount-plugin-generic-oauth is not configured yet.

dpkg: error processing package account-plugin-identica (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-jabber:
 account-plugin-jabber depends on empathy (= 3.8.6-0ubuntu13); however:
  Package empathy is not configured yet.
 account-plugin-jabber depends on mcp-account-manager-uoa; however:
  Package mcp-account-manager-uoa is not configured yet.

dpkg: error processing package account-plugin-jabber (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of avahi-daemon:
 avahi-daemon depends on dbus (>= 1.2.16-0ubuntu3); however:
  Package dbus is not configured yet.

dpkg: error processing package avahi-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of telepathy-salut:
 telepathy-salut depends on avahi-daemon; however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package telepathy-salut (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-salut:
 account-plugin-salut depends on empathy (= 3.8.6-0ubuntu13); however:
  Package empathy is not configured yet.
 account-plugin-salut depends on telepathy-salut; however:
  Package telepathy-salut is not configured yet.
 account-plugin-salut depends on mcp-account-manager-uoa; however:
  Package mcp-account-manager-uoa is not configured yet.

dpkg: error processing package account-plugin-salut (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-twitter:
 account-plugin-twitter depends on libaccount-plugin-generic-oauth | ubuntu-system-settings-online-accounts; however:
  Package libaccount-plugin-generic-oauth is not configured yet.
  Package ubuntu-system-settings-online-accounts is not installed.

dpkg: error processing package account-plugin-twitter (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-windows-live:
 account-plugin-windows-live depends on libaccount-plugin-generic-oauth; however:
  Package libaccount-plugin-generic-oauth is not configured yet.

dpkg: error processing package account-plugin-windows-live (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-yahoo:
 account-plugin-yahoo depends on empathy (= 3.8.6-0ubuntu13); however:
  Package empathy is not configured yet.
 account-plugin-yahoo depends on mcp-account-manager-uoa; however:
  Package mcp-account-manager-uoa is not configured yet.

dpkg: error processing package account-plugin-yahoo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of acpid:
 acpid depends on kmod; however:
  Package kmod is not configured yet.

dpkg: error processing package acpid (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of aisleriot:
 aisleriot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package aisleriot (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of amide:
 amide depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0:amd64 is not configured yet.

dpkg: error processing package amide (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up anacron (2.3-21) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package anacron (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package apache2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2 (= 2.4.10-1ubuntu1); however:
  Package apache2 is not configured yet.

dpkg: error processing package apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apparmor-utils:
 apparmor-utils depends on apparmor (>= 2.6.1-4ubuntu1); however:
  Package apparmor is not configured yet.

dpkg: error processing package apparmor-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of appmenu-qt:amd64:
 appmenu-qt:amd64 depends on libdbusmenu-qt2; however:
  Package libdbusmenu-qt2:amd64 is not configured yet.
 appmenu-qt:amd64 depends on libqtgui4 (>= 4:4.8); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package appmenu-qt:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on sysv-rc (>= 2.86.ds1-14.1ubuntu2); however:
  Package sysv-rc is not configured yet.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing package apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xterm:
 xterm depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.

dpkg: error processing package xterm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
 apport-gtk depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up asterisk (1:11.11.0~dfsg-2ubuntu1) ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142986 package 'virtualbox-3.0':
 error in 'Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 142987 package 'virtualbox-3.0':
 error in 'Config-Version' field string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package asterisk (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of asterisk-voicemail:
 asterisk-voicemail depends on asterisk (= 1:11.11.0~dfsg-2ubuntu1); however:
  Package asterisk is not configured yet.

dpkg: error processing package asterisk-voicemail (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up at (3.1.14-1ubuntu2) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package at (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of audacity:
 audacity depends on libwxgtk2.8-0 (>= 2.8.12.1+dfsg2); however:
  Package libwxgtk2.8-0:amd64 is not configured yet.

dpkg: error processing package audacity (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up aumix-common (2.9.1-3) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package aumix-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of aumix-gtk:
 aumix-gtk depends on aumix-common; however:
  Package aumix-common is not configured yet.

dpkg: error processing package aumix-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avahi-utils:
 avahi-utils depends on avahi-daemon; however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package avahi-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluetooth:
 bluetooth depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-alsa:amd64:
 bluez-alsa:amd64 depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluez-alsa:amd64 (--configure):
 dependency problems - leavingNo apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                     unconfigured
dpkg: dependency problems prevent configuration of bluez-alsa:i386:
 bluez-alsa:i386 depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluez-alsa:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-cups:
 bluez-cups depends on cups; however:
  Package cups is not configured yet.

dpkg: error processing package bluez-cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-gstreamer:
 bluez-gstreamer depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluez-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-utils:
 bluez-utils depends on bluetooth; however:
  Package bluetooth is not configured yet.

dpkg: error processing package bluez-utils (--configure):
 dependency problemNo apport report written because MaxReports is reached already
 No apport report written because MaxReports is reached already
                                                               No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                           s - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-settings-daemon:
 unity-settings-daemon depends on accountsservice (>= 0.6.34); however:
  Package accountsservice is not configured yet.

dpkg: error processing package unity-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of media-player-info:
 media-player-info depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package media-player-info (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on dbus; however:
  Package dbus is not configured yet.
 rhythmbox depends on media-player-info; however:
  Package media-player-info is not configured yet.

dpkg: error processing package rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugins:No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already

 rhythmbox-plugins depends on rhythmbox (= 3.0.3-1ubuntu2); however:
  Package rhythmbox is not configured yet.

dpkg: error processing package rhythmbox-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-zeitgeist:
 rhythmbox-plugin-zeitgeist depends on rhythmbox (>= 3.0); however:
  Package rhythmbox is not configured yet.
 rhythmbox-plugin-zeitgeist depends on rhythmbox (<< 3.1); however:
  Package rhythmbox is not configured yet.

dpkg: error processing package rhythmbox-plugin-zeitgeist (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-cdrecorder:
 rhythmbox-plugin-cdrecorder depends on rhythmbox (= 3.0.3-1ubuntu2); however:
  Package rhythmbox is not configured yet.

dpkg: error processing package rhythmbox-plugin-cdrecorder (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configurNo apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
      ation of rhythmbox-mozilla:
 rhythmbox-mozilla depends on rhythmbox (= 3.0.3-1ubuntu2); however:
  Package rhythmbox is not configured yet.

dpkg: error processing package rhythmbox-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udisks2:
 udisks2 depends on udev; however:
  Package udev is not configured yet.
 udisks2 depends on dbus; however:
  Package dbus is not configured yet.
 udisks2 depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.

dpkg: error processing package udisks2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-daemons:
 gvfs-daemons depends on udisks2; however:
  Package udisks2 is not configured yet.

dpkg: error processing package gvfs-daemons (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs:amd64:
 gvfs:amd64 depends on gvfs-daemNo apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                          ons (>= 1.20.2-1ubuntu2); however:
  Package gvfs-daemons is not configured yet.
 gvfs:amd64 depends on gvfs-daemons (<< 1.20.2-1ubuntu2.1~); however:
  Package gvfs-daemons is not configured yet.

dpkg: error processing package gvfs:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gvfs (>= 1.3.2); however:
  Package gvfs:amd64 is not configured yet.

dpkg: error processing package nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs:i386:
 gvfs:i386 depends on gvfs-daemons (>= 1.20.2-1ubuntu2); however:
  Package gvfs-daemons is not configured yet.
 gvfs:i386 depends on gvfs-daemons (<< 1.20.2-1ubuntu2.1~); however:
  Package gvfs-daemons is not configured yet.

dpkg: error processing package gvfs:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of brasero:
 brasero depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 brasero depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.
 brasero depends on gvfs; however:
  Package gvfs:amd64 is not configured yet.

dpkg: error processing package brasero (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of camorama:
 camorama depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 camorama depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0:amd64 is not configured yet.

dpkg: error processing package camorama (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of udisks:
 udisks depends on udev; however:
  Package udev is not configured yet.
 udisks depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing package udisks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-checkbox:
 python3-checkbox depends on udev; however:
  Package udev is not configured yet.
 python3-checkbox depends on udisks2 | udisks; however:
No apport report written because MaxReports is reached already
                                                                Package udisks2 is not configured yet.
  Package udisks is not configured yet.

dpkg: error processing package python3-checkbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-checkbox-support:
 python3-checkbox-support depends on udev; however:
  Package udev is not configured yet.No apport report written because MaxReports is reached already

 python3-checkbox-support depends on udisks2; however:
  Package udisks2 is not configured yet.

dpkg: error processing package python3-checkbox-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-checkbox-ng:
No apport report written because MaxReports is reached already
                                                               python3-checkbox-ng depends on python3-checkbox-support; however:
  Package python3-checkbox-support is not configured yet.

dpkg: error processing package python3-checkbox-ng (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-ng:
 checkbox-ng depends on python3-checkbox-ng (= 0.3.1-1); however:
  Package python3-checkbox-ng is not configured yet.

No apport report written because MaxReports is reached already
                                                              dpkg: error processing package checkbox-ng (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox:
 checkbox depends on python3-checkbox; however:
  Package python3-checkbox is not configured yet.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing package checkbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of checkbox-ng-service:
 checkbox-ng-service depends on checkbox-ng (= 0.3.1-1); however:
  Package checkbox-ng is not configured yet.

dpkg: error processing package checkbox-ng-service (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of checkbox-gui:
 checkbox-gui depends on checkbox-ng-service; however:
  Package checkbox-ng-service is not configured yet.
 checkbox-gui depends on qtdeclarative5-qtquick2-plugin; however:
  Package qtdeclarative5-qtquick2-plugin:amd64 is not configured yet.
 checkbox-gui depends on qtdeclarative5-ubuntu-ui-toolkit-plugin | qt-components-ubuntu; however:
  Package qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 is not configured yet.
  Package qt-components-ubuntu is not installed.
  Package qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 which provides qt-components-ubuntu is not configured yet.

dpkg: error processing package checkbox-gui (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of checkbox-qt:
 checkbox-qt depends on checkbox-gui; however:
  Package checkbox-gui is not configured yet.

dpkg: error processing package checkbox-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of chkrootkit:
 chkrootkit depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package chkrootkit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on procps (>= 1:3.3.2); however:
  Package procps is not configured yet.

dpkg: error processing package clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.

dpkg: error processing package clamav (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
 clamav-daemon depends on procps (>= 1:3.3.2); however:
  Package procps is not configured yet.

dpkg: error processing package clamav-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of clamsmtp:
 clamsmtp depends on clamav-daemon (>= 0.75.1); however:
  Package clamav-daemon is not configured yet.

dpkg: error processing package clamsmtp (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of clamtk:
 clamtk depends on clamav (>= 0.95); however:
  Package clamav is not configured yet.
 clamtk depends on clamav-freshclam (>= 0.95) | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
 clamtk depends on cron; however:
  Package cron is not configured yet.

dpkg: error processing package clamtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cmake:
 cmake depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cmake (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of epiphany-browser:
 epiphany-browser depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package epiphany-browser (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on systemd; however:
  Package systemd is not configured yet.

dpkg: error processing package gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libmutter0d:
 libmutter0d depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 libmutter0d depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package libmutter0d (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-mutter-3.0:
 gir1.2-mutter-3.0 depends on libmutter0d; however:No apport report written because MaxReports is reached already

  Package libmutter0d is not configured yet.

dpkg: error processing package gir1.2-mutter-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upower:No apport report written because MaxReports is reached already

 upower depends on udev; however:
  Package udev is not configured yet.
 upower depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing package upower (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 gnome-session-bin depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.
 gnome-session-bin depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
 gnome-session-bin depends on upower (>= 0.9.0); however:
  Package upower is not configured yet.

dpkg: error processing package gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-settings-daemon (>= 3.0); however:
  Package gnome-settings-daemon is not configured yet.
 gnome-session depends on gnome-session-bin (>= 3.9.90-0ubuntu16); however:
  Package gnome-session-bin is not configured yet.
 gnome-session depends on gnome-session-bin (<< 3.10); however:
  Package gnome-session-bin is not configured yet.

dpkg: error processing package gnome-session (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gir1.2-mutter-3.0 (>= 3.12.0); however:
  Package gir1.2-mutter-3.0 is not configured yet.
 gnome-shell depends on libmutter0d; however:
  Package libmutter0d is not configured yet.
 gnome-shell depends on gnome-session; however:
  Package gnome-session is not configured yet.
 gnome-shell depends on gnome-settings-daemon (>= 3.4.0); however:
  Package gnome-settings-daemon is not configured yet.

dpkg: error processing package gnome-shell (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 gnome-panel depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package gnome-panel (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of metacity:
 metacity depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 metacity depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package metacity (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-session-flashback:
 gnome-session-flashback depends on gnome-panel (>= 3.0); however:
  Package gnome-panel is not configured yet.
 gnome-session-flashback depends on gnome-session-bin; however:
  Package gnome-session-bin is not configured yet.
 gnome-session-flashback depends on metacity (>= 2.30); however:
  Package metacity is not configured yet.
 gnome-session-flashback depends on nautilus (>= 3.8); however:
  Package nautilus is not configured yet.
 gnome-session-flashback depends on unity-settings-daemon; however:
  Package unity-settings-daemon is not configured yet.

dpkg: error processing package gnome-session-flashback (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-session:
 ubuntu-session depends on unity-settings-daemon; however:
  Package unity-settings-daemon is not configured yet.
 ubuntu-session depends on gnome-session-bin (>= 3.9.90-0ubuntu16); however:
  Package gnome-session-bin is not configured yet.
 ubuntu-session depends on gnome-session-bin (<< 3.10); however:
  Package gnome-session-bin is not configured yet.

dpkg: error processing package ubuntu-session (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mutter:
 mutter depends on libmutter0d; however:
  Package libmutter0d is not configured yet.

dpkg: error processing package mutter (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkdecorations4abi2:
 libkdecorations4abi2 depends on libkdeui5 (>= 4:4.11); however:
  Package libkdeui5 is not configured yet.
 libkdecorations4abi2 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkdecorations4abi2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkwineffects1abi5:
 libkwineffects1abi5 depends on libkdeui5 (>= 4:4.11); however:
  Package libkdeui5 is not configured yet.
 libkwineffects1abi5 depends on libqtgui4 (>= 4:4.7.0~beta1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkwineffects1abi5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkworkspace4abi2:
 libkworkspace4abi2 depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 libkworkspace4abi2 depends on libkdeui5 (>= 4:4.11); however:
  Package libkdeui5 is not configured yet.
 libkworkspace4abi2 depends on libplasma3 (>= 4:4.11); however:
  Package libplasma3 is not configured yet.
 libkworkspace4abi2 depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4:amd64 is not configured yet.
 libkworkspace4abi2 depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package libkworkspace4abi2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde-window-manager-common:
 kde-window-manager-common depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager-common depends on kde-style-oxygen (= 4:4.11.12-0ubuntu1); however:
  Package kde-style-oxygen is not configured yet.
 kde-window-manager-common depends on libkcmutils4 (>= 4:4.11); however:
  Package libkcmutils4 is not configured yet.
 kde-window-manager-common depends on libkdeclarative5 (>= 4:4.7.0); however:
  Package libkdeclarative5 is not configured yet.
 kde-window-manager-common depends on libkdecorations4abi2 (= 4:4.11.12-0ubuntu1); however:
  Package libkdecorations4abi2 is not configured yet.
 kde-window-manager-common depends on libkdeui5 (>= 4:4.11); however:
  Package libkdeui5 is not configured yet.
 kde-window-manager-common depends on libkio5 (>= 4:4.11); however:
  Package libkio5 is not configured yet.
 kde-window-manager-common depends on libknewstuff3-4 (>= 4:4.11); however:
  Package libknew
dpkg: error processing package kde-window-manager-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkwinglesutils1:
 libkwinglesutils1 depends on libqtgui4 (>= 4:4.6.2); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkwinglesutils1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkwinglutils1abi3:
No apport report written because MaxReports is reached already
                                                               libkwinglutils1abi3 depends on libqtgui4 (>= 4:4.6.2); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkwinglutils1abi3 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde-window-manager:
 kde-window-manager depends on kde-window-manager-common (= 4:4.11.12-0ubuntu1); however:
  Package kde-window-manager-common is not configured yet.
 kde-window-manager depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 kde-window-manager depends on libkdeclarative5 (>= 4:4.7.0); however:
  Package libkdeclarative5 is not configured yet.
 kde-window-manager depends on libkdecorations4abi2 (= 4:4.11.12-0ubuntu1); however:
  Package libkdecorations4abi2 is not configured yet.
 kde-window-manager depends on libkdeui5 (>= 4:4.11); however:
  Package libkdeui5 is not configured yet.
 kde-window-manager depends on libkwineffects1abi5 (= 4:4.11.12-0ubuntu1); however:
  Package libkwineffects1abi5 is not configured yet.
 kde-window-manager depends on libkwinglesutils1 (= 4:4.11.12-0ubuntu1); however:
  Package libkwin
dpkg: error processing package kde-window-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of compiz-core:
 compiz-core depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 compiz-core depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package compiz-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of compiz-plugins-default:
 compiz-plugins-default depends on compiz-core (= 1:0.9.12+14.10.20140918-0ubuntu1); however:
  Package compiz-core is not configured yet.

dpkg: error processing package compiz-plugins-default (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libcompizconfig0:
 libcompizconfig0 depends on compiz-core (= 1:0.9.12+14.10.20140918-0ubuntu1); however:
  Package compiz-core is not configured yet.

dpkg: error processing package libcompizconfig0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libcompizconfig0; however:
  Package libcompizconfig0 is not configured yet.
 compiz-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 compiz-gnome depends on compiz-plugins-default (= 1:0.9.12+14.10.20140918-0ubuntu1); however:
  Package compiz-plugins-default is not configured yet.

dpkg: error processing package compiz-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-core (>= 1:0.9.12+14.10.20140918-0ubuntu1); however:
  Package compiz-core is not configured yet.
 compiz depends on compiz-plugins-default (>= 1:0.9.12+14.10.20140918-0ubuntu1); however:
  Package compiz-plugins-default is not configured yet.
 compiz depends on compiz-gnome; however:
  Package compiz-gnome is not configured yet.

dpkg: error processing package compiz (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gdm:
 gdm depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.
 gdm depends on gnome-session-bin (>= 3.6); however:
  Package gnome-session-bin is not configured yet.
 gdm depends on gnome-settings-daemon (>= 3.2); however:
  Package gnome-settings-daemon is not configured yet.
 gdm depends on gnome-shell; however:
  Package gnome-shell is not configured yet.
 gdm depends on plymouth (>= 0.8.8-0ubuntu6.1); however:
  Package plymouth is not configured yet.
 gdm depends on accountsservice (>= 0.6.12); however:
  Package accountsservice is not configured yet.
 gdm depends on x11-common (>= 1:7.6+11); however:
  Package x11-common is not configured yet.

dpkg: error processing package gdm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of vino:
 vino depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 vino depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package vino (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package gnome-media (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on accountsservice; however:
  Package accountsservice is not configured yet.
 gnome-control-center depends on gnome-settings-daemon (>= 3.7.91); however:
  Package gnome-settings-daemon is not configured yet.

dpkg: error processing package gnome-control-center (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
 gnome-bluetooth depends on udev (>= 154); however:
  Package udev is not configured yet.

dpkg: error processing package gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of indicator-datetime:
 indicator-datetime depends on systemd-services; however:
  Package systemd-services is not installed.
  Package systemd which provides systemd-services is not configured yet.
 indicator-datetime depends on systemd-shim; however:
  Package systemd-shim is not configured yet.

dpkg: error processing package indicator-datetime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-power:
 indicator-power depends on upower; however:No apport report written because MaxReports is reached already

  Package upower is not configured yet.

dpkg: error processing package indicator-power (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.
No apport report written because MaxReports is reached already
                                                               pulseaudio depends on udev (>= 143); however:
  Package udev is not configured yet.

dpkg: error processing package pulseaudio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-sound:
 indicator-sound depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package indicator-sound (--configure):
 dependency problems - leaving unconfiguredNo apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already

dpkg: dependency problems prevent configuration of unity-control-center:
 unity-control-center depends on accountsservice; however:
  Package accountsservice is not configured yet.
 unity-control-center depends on unity-settings-daemon; however:
  Package unity-settings-daemon is not configured yet.
 unity-control-center depends on indicator-datetime; however:
  Package indicator-datetime is not configured yet.
 unity-control-center depends on indicator-power; however:
  Package indicator-power is not configured yet.
 unity-control-center depends on indicator-sound; however:
  Package indicator-sound is not configured yet.

dpkg: error processing package unity-control-center (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of indicator-bluetooth:
 indicator-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
 indicator-bluetooth depends on unity-control-center | gnome-control-center | ubuntu-system-settings; however:
  Package unity-control-center is not configured yet.
  Package gnome-control-center is not configured yet.
  Package ubuntu-system-settings is not installed.
 indicator-bluetooth depends on gnome-bluetooth | ubuntu-system-settings; however:
  Package gnome-bluetooth is not configured yet.
  Package ubuntu-system-settings is not installed.

dpkg: error processing package indicator-bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.9.8); however:
  Package network-manager is not configured yet.
 network-manager-gnome depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of compiz-plugins:
 compiz-plugins depends on compiz-core (= 1:0.9.12+14.10.20140918-0ubuntu1); however:
  Package compiz-core is not configured yet.
 compiz-plugins depends on compiz-plugins-default (= 1:0.9.12+14.10.20140918-0ubuntu1); however:
  Package compiz-plugins-default is not configured yet.

dpkg: error processing package compiz-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of erlang-base:
No apport report written because MaxReports is reached already
                                                               erlang-base depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package erlang-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of erlang-crypto:
 erlang-crypto depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.

dpkg: error processing package erlang-crypto (--configure):No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of erlang-eunit:
 erlang-eunit depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.

dpkg: error processing package erlang-eunit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of erlang-mnesia:
 erlang-mnesia depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.No apport report written because MaxReports is reached already


dpkg: error processing package erlang-mnesia (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of erlang-runtime-tools:
 erlang-runtime-tools depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.
 erlang-runtime-tools depends on erlang-mnesia (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-mnesia is not configured yet.

No apport report written because MaxReports is reached already
                                                              dpkg: error processing package erlang-runtime-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of erlang-asn1:
 erlang-asn1 depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.

dpkg: error processing package erlang-asn1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of erlang-public-key:
 erlang-public-key depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.
 erlang-public-key depends on erlang-asn1 (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-asn1 is not configured yet.
 erlang-public-key depends on erlang-crypto (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-crypto is not configured yet.

dpkg: error processing package erlang-public-key (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of erlang-ssl:
 erlang-ssl depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.
 erlang-ssl depends on erlang-crypto (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-crypto is not configured yet.
 erlang-ssl depends on erlang-public-key (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-public-key is not configured yet.

dpkg: error processing package erlang-ssl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of erlang-inets:
 erlang-inets depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.
 erlang-inets depends on erlang-mnesia (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-mnesia is not configured yet.
 erlang-inets depends on erlang-runtime-tools (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-runtime-tools is not configured yet.
 erlang-inets depends on erlang-ssl (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-ssl is not configured yet.

dpkg: error processing package erlang-inets (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of erlang-snmp:
 erlang-snmp depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.
 erlang-snmp depends on erlang-crypto (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-crypto is not configured yet.
 erlang-snmp depends on erlang-mnesia (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-mnesia is not configured yet.
 erlang-snmp depends on erlang-runtime-tools (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-runtime-tools is not configured yet.

dpkg: error processing package erlang-snmp (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of erlang-os-mon:
 erlang-os-mon depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.
 erlang-os-mon depends on erlang-mnesia (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-mnesia is not configured yet.
 erlang-os-mon depends on erlang-snmp (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-snmp is not configured yet.

dpkg: error processing package erlang-os-mon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of erlang-syntax-tools:
 erlang-syntax-tools depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.

dpkg: error processing package erlang-syntax-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of erlang-webtool:No apport report written because MaxReports is reached already

 erlang-webtool depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.
 erlang-webtool depends on erlang-inets (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-inets is not configured yet.

dpkg: error processing package erlang-webtool (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of erlang-tools:
 erlang-tools depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.
 erlang-tools depends on erlang-inets (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-inets is not configured yet.
 erlang-tools depends on erlang-runtime-tools (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-runtime-tools is not configured yet.
 erlang-tools depends on erlang-webtool (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-webtool is not configured yet.

dpkg: error processing package erlang-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of erlang-xmerl:
 erlang-xmerl depends on erlang-base (= 1:17.1-dfsg-4ubuntu2) | erlang-base-hipe (= 1:17.1-dfsg-4ubuntu2); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.

dpkg: error processing package erlang-xmerl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of couchdb-bin:
 couchdb-bin depends on erlang-abi-17.0; however:
  Package erlang-abi-17.0 is not installed.
  Package erlang-base which provides erlang-abi-17.0 is not configured yet.
 couchdb-bin depends on erlang-base (>= 1:17.1-dfsg) | erlang-base-hipe (>= 1:17.1-dfsg); however:
  Package erlang-base is not configured yet.
  Package erlang-base-hipe is not installed.
 couchdb-bin depends on erlang-crypto (>= 1:17.1-dfsg); however:
  Package erlang-crypto is not configured yet.
 couchdb-bin depends on erlang-eunit (>= 1:17.1-dfsg); however:
  Package erlang-eunit is not configured yet.
 couchdb-bin depends on erlang-inets (>= 1:17.1-dfsg); however:
  Package erlang-inets is not configured yet.
 couchdb-bin depends on erlang-os-mon (>= 1:17.1-dfsg); however:
  Package erlang-os-mon is not configured yet.
 couchdb-bin depends on erlang-public-key (>= 1:17.1-dfsg); however:
  Package erlang-public-key is not configured yet.
 couchdb-bin depends on erlang-ssl (>= 1:1
dpkg: error processing package couchdb-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cryptsetup:
 cryptsetup depends on initramfs-tools (>= 0.91) | linux-initramfs-tool; however:
  Package initramfs-tools is not configured yet.
  Package linux-initramfs-tool is not installed.
  Package initramfs-tools which provides linux-initramfs-tool is not configured yet.
 cryptsetup depends on plymouth; however:
  Package plymouth is not configured yet.

dpkg: error processing package cryptsetup (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on gvfs (= 1.20.2-1ubuntu2); however:
  Package gvfs:amd64 is not configured yet.
 gvfs-backends depends on gvfs-daemons (= 1.20.2-1ubuntu2); however:
  Package gvfs-daemons is not configured yet.

dpkg: error processing package gvfs-backends (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of deja-dup-backend-gvfs:
 deja-dup-backend-gvfs depends on gvfs-backends; however:
  Package gvfs-backends is not configured yet.

dpkg: error processing package deja-dup-backend-gvfs (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of dvdstyler:
 dvdstyler depends on libwxgtk-media3.0-0 (>= 3.0.1); however:
  Package libwxgtk-media3.0-0:amd64 is not configured yet.
 dvdstyler depends on libwxgtk3.0-0 (>= 3.0.1); however:
  Package libwxgtk3.0-0:amd64 is not configured yet.
 dvdstyler depends on libwxsvg2; however:
  Package libwxsvg2:amd64 is not configured yet.

dpkg: error processing package dvdstyler (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (= 3.12.7-0ubuntu1); however:
  Package evolution is not configured yet.

dpkg: error processing package evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on libice6; however:No apport report written because MaxReports is reached already

  Package libice6:amd64 is not configured yet.
 flashplugin-installer depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of foxtrotgps:
 foxtrotgps depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing package foxtrotgps (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fslview:
 fslview depends on libqt4-qt3support (>= 4:4.5.3); however:
  Package libqt4-qt3support:amd64 is not configured yet.
 fslview depends on libqtgui4 (>= 4:4.7.0~beta1); however:
  Package libqtgui4:amd64 is not configured yet.
 fslview depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.
 fslview depends on libvtk5.8-qt4; however:
  Package libvtk5.8-qt4 is not configured yet.

dpkg: error processing package fslview (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of fsl-5.0-core:
 fsl-5.0-core depends on fslview; however:
  Package fslview is not configured yet.

dpkg: error processing package fsl-5.0-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fsl-core:
No apport report written because MaxReports is reached already
                                                               fsl-core depends on fsl-5.0-core; however:
  Package fsl-5.0-core is not configured yet.

dpkg: error processing package fsl-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fsl:
 fsl depends on fsl-core; however:
  Package fsl-core is not configured yet.

dpkg: error processing package fsl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of gconf-defaults-service:
 gconf-defaults-service depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package gconf-defaults-service (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ginkgocadx:
 ginkgocadx depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.
 ginkgocadx depends on libwxgtk3.0-0 (>= 3.0.1); however:
No apport report written because MaxReports is reached already
                                                                Package libwxgtk3.0-0:amd64 is not configured yet.

dpkg: error processing package ginkgocadx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem0:
 libtotem0 depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 libtotem0 depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.
No apport report written because MaxReports is reached already

dpkg: error processing package libtotem0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-totem-1.0:
 gir1.2-totem-1.0 depends on libtotem0 (<< 3.11); however:
  Package libtotem0 is not configured yet.
 gir1.2-totem-1.0 depends on libtotem0 (>= 3.10.1-1ubuntu6); however:
  Package libtotem0 is not configured yet.

dpkg: error processing package gir1.2-totem-1.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gnome-applets depends on gnome-applets-data (>= 3.8); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 3.9); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.91.91); however:
  Package gnome-panel is not configured yet.
 gnome-applets depends on gvfs; however:
  Package gvfs:amd64 is not configured yet.
 gnome-applets depends on upower; however:
  Package upower is not configured yet.

dpkg: error processing package gnome-applets (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up speech-dispatcher (0.8-6ubuntu2) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (1) of script `speech-dispatcher' overrides LSB defaults (0 1 6).
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package speech-dispatcher (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-orca:
 gnome-orca depends on speech-dispatcher (>= 0.8); however:
  Package speech-dispatcher is not configured yet.

dpkg: error processing package gnome-orca (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-session-fallback:
 gnome-session-fallback depends on gnome-session-flashback; however:
  Package gnome-session-flashback is not configured yet.

dpkg: error processing package gnome-session-fallback (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-shell-extensions:
 gnome-shell-extensions depends on gnome-shell (>= 3.12); however:
  Package gnome-shell is not configured yet.
 gnome-shell-extensions depends on gnome-shell (<< 3.13); however:
  Package gnome-shell is not configured yet.
 gnome-shell-extensions depends on gvfs (>= 1.16.0); however:
  Package gvfs:amd64 is not configured yet.
 gnome-shell-extensions depends on gnome-session (>= 3.8); however:
  Package gnome-session is not configured yet.

dpkg: error processing package gnome-shell-extensions (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gofigure2:
 gofigure2 depends on libgofigure0; however:
  Package libgofigure0 is not configured yet.
 gofigure2 depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4:amd64 is not configured yet.
 gofigure2 depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.

dpkg: error processing package gofigure2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of googleearth-package:
 googleearth-package depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package googleearth-package (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grace:
 grace depends on libxbae4m (>= 4.60.2); however:
  Package libxbae4m:amd64 is not configured yet.
 grace depends on libxm4 (>= 2.3.4); however:
  Package libxm4:amd64 is not configured yet.
 grace depends on libxmhtml1.1 (>= 1.1.9); however:
  Package libxmhtml1.1:amd64 is not configured yet.
 grace depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 grace depends on xterm; however:
  Package xterm is not configured yet.

dpkg: error processing package grace (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-15); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.02~beta2-15); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.02~beta2-15); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub2-common (= 2.02~beta2-15); however:
  Package grub2-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.02~beta2-15); however:
  Package grub-pc-bin is not configured yet.

dpkg: error processing package grub-pc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up sane-utils (1.0.24-1.1ubuntu1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package sane-utils (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gscan2pdf:
 gscan2pdf depends on sane-utils (>= 1.0.17); however:
  Package sane-utils is not configured yet.

dpkg: error processing package gscan2pdf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-gnomevfs:amd64:No apport report written because MaxReports is reached already

 gstreamer0.10-gnomevfs:amd64 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0:amd64 is not configured yet.

dpkg: error processing package gstreamer0.10-gnomevfs:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gvfs-fuse:
 gvfs-fuse depends on gvfs (= 1.20.2-1ubuntu2); however:
  Package gvfs:amd64 is not configured yet.

dpkg: error processing package gvfs-fuse (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gwyddion-common:
 gwyddion-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package gwyddion-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgwyddion2-0:
 libgwyddion2-0 depends on gwyddion-common (= 2.36-1ubuntu1); however:
  Package gwyddion-common is not configured yet.

dpkg: error processing package libgwyddion2-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gwyddion:
 gwyddion depends on libgwyddion2-0 (>= 2.36-1ubuntu1); however:
  Package libgwyddion2-0 is not configured yet.
 gwyddion depends on gwyddion-common (= 2.36-1ubuntu1); however:
  Package gwyddion-common is not configured yet.

dpkg: error processing package gwyddion (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libxine2-x:
 libxine2-x depends on libxvmc1; however:
  Package libxvmc1:amd64 is not configured yet.

dpkg: error processing package libxine2-x (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libxine2-gnome:
 libxine2-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0:amd64 is not configured yet.

dpkg: error processing package libxine2-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gxine:
 gxine depends on libxine2-x; however:
  Package libxine2-x is not configured yet.
 gxine depends on libxine2-gnome; however:
  Package libxine2-gnome is not configured yet.

dpkg: error processing package gxine (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gxineplugin:
 gxineplugin depends on gxine (>= 0.5.0); however:
  Package gxine is not configured yet.

dpkg: error processing package gxineplugin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hud:
 hud depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 hud depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:amd64 is not configured yet.

dpkg: error processing package hud (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hugin-tools:
 hugin-tools depends on libwxgtk3.0-0 (>= 3.0.1); however:
  Package libwxgtk3.0-0:amd64 is not configured yet.

dpkg: error processing package hugin-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hugin:
 hugin depends on hugin-tools (= 2014.0.0~rc3+dfsg-2); however:
  Package hugin-tools is not configured yet.
 hugin depends on libwxgtk3.0-0 (>= 3.0.1); however:
  Package libwxgtk3.0-0:amd64 is not configured yet.

dpkg: error processing package hugin (--configure):
 dependency problems - leaving unconfigured
Setting up iaxmodem (1.2.0~dfsg-2ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package iaxmodem (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of imagevis3d:
 imagevis3d depends on libqt4-opengl (>= 4:4.5.3); however:
  Package libqt4-opengl:amd64 is not configured yet.
 imagevis3d depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package imagevis3d (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of indicator-session:
 indicator-session depends on systemd-services; however:
  Package systemd-services is not installed.
  Package systemd which provides systemd-services is not configured yet.

dpkg: error processing package indicator-session (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of inkscape:
 inkscape depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0:amd64 is not configured yet.

dpkg: error processing package inkscape (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of jarwrapper:
 jarwrapper depends on binfmt-support; however:
  Package binfmt-support is not configured yet.

dpkg: error processing package jarwrapper (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkcompactdisc4:
 libkcompactdisc4 depends on libphonon4 (>= 4:4.6.0really4.3.80); however:
  Package libphonon4:amd64 is not configured yet.
 libkcompactdisc4 depends on libsolid4 (>= 4:4.14.1); however:
  Package libsolid4 is not configured yet.
 libkcompactdisc4 depends on phonon; however:
  Package phonon:amd64 is not configured yet.

dpkg: error processing package libkcompactdisc4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkcddb4:
 libkcddb4 depends on libkcompactdisc4; however:
  Package libkcompactdisc4 is not configured yet.
 libkcddb4 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libkcddb4 depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 libkcddb4 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkcddb4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libk3b6:
 libk3b6 depends on libkcddb4 (>= 4:4.3.4); however:
  Package libkcddb4 is not configured yet.
 libk3b6 depends on libkcmutils4 (>= 4:4.4.95); however:
  Package libkcmutils4 is not configured yet.
 libk3b6 depends on libkde3support4 (>= 4:4.4.4); however:
  Package libkde3support4 is not configured yet.
 libk3b6 depends on libkdeui5 (>= 4:4.4.4); however:
  Package libkdeui5 is not configured yet.
 libk3b6 depends on libkio5 (>= 4:4.4.4); however:
  Package libkio5 is not configured yet.
 libk3b6 depends on libqt4-qt3support (>= 4:4.5.3); however:
  Package libqt4-qt3support:amd64 is not configured yet.
 libk3b6 depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4:amd64 is not configured yet.
 libk3b6 depends on libsolid4 (>= 4:4.4.4); however:
  Package libsolid4 is not configured yet.

dpkg: error processing package libk3b6 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 k3b depends on libk3b6 (= 2.0.2-7ubuntu2); however:
  Package libk3b6 is not configured yet.
 k3b depends on libkcddb4 (>= 4:4.3.4); however:
  Package libkcddb4 is not configured yet.
 k3b depends on libkcmutils4 (>= 4:4.4.95); however:
  Package libkcmutils4 is not configured yet.
 k3b depends on libkde3support4 (>= 4:4.4.4); however:
  Package libkde3support4 is not configured yet.
 k3b depends on libkdeui5 (>= 4:4.5.85); however:
  Package libkdeui5 is not configured yet.
 k3b depends on libkfile4 (>= 4:4.7.0); however:
  Package libkfile4 is not configured yet.
 k3b depends on libkio5 (>= 4:4.4.4); however:
  Package libkio5 is not configured yet.
 k3b depends on libknotifyconfig4 (>= 4:4.4.4); however:
  Package libknotifyconfig4 is not configured yet.
 k3b depends on libqt4-qt3support (>= 4:4.5.3); however:
  Package libqt4-qt3support:amd64 is not configured yet.
 k3b d
dpkg: error processing package k3b (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libknewstuff2-4:
 libknewstuff2-4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libknewstuff2-4 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libknewstuff2-4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libknewstuff2-4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkidletime4:
 libkidletime4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkidletime4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkidletime4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkprintutils4:
 libkprintutils4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkprintutils4 depends on libkparts4 (= 4:4.14.1-0ubuntu1); however:
  Package libkparts4 is not configured yet.
 libkprintutils4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkprintutils4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkutils4:
 libkutils4 depends on libkcmutils4 (= 4:4.14.1-0ubuntu1); however:
  Package libkcmutils4 is not configured yet.
 libkutils4 depends on libkemoticons4 (= 4:4.14.1-0ubuntu1); however:
  Package libkemoticons4 is not configured yet.
 libkutils4 depends on libkidletime4 (= 4:4.14.1-0ubuntu1); however:
  Package libkidletime4 is not configured yet.
 libkutils4 depends on libkprintutils4 (= 4:4.14.1-0ubuntu1); however:
  Package libkprintutils4 is not configured yet.

dpkg: error processing package libkutils4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkimproxy4:
 libkimproxy4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkimproxy4 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libkimproxy4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkimproxy4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkrossui4:
 libkrossui4 depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 libkrossui4 depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 libkrossui4 depends on libkparts4 (= 4:4.14.1-0ubuntu1); however:
  Package libkparts4 is not configured yet.
 libkrossui4 depends on libkrosscore4 (= 4:4.14.1-0ubuntu1); however:
  Package libkrosscore4 is not configured yet.
 libkrossui4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkrossui4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkunitconversion4:
 libkunitconversion4 depends on libsolid4 (= 4:4.14.1-0ubuntu1); however:
  Package libsolid4 is not configured yet.

dpkg: error processing package libkunitconversion4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt4-dev-bin:
 libqt4-dev-bin depends on libqt4-qt3support (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-qt3support:amd64 is not configured yet.
 libqt4-dev-bin depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqt4-dev-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt4-dev:
 libqt4-dev depends on libqt4-declarative (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-declarative:amd64 is not configured yet.
 libqt4-dev depends on libqt4-designer (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-designer:amd64 is not configured yet.
 libqt4-dev depends on libqt4-dev-bin (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-dev-bin is not configured yet.
 libqt4-dev depends on libqt4-help (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-help:amd64 is not configured yet.
 libqt4-dev depends on libqt4-qt3support (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-qt3support:amd64 is not configured yet.
 libqt4-dev depends on libqt4-scripttools (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-scripttools:amd64 is not configured yet.
 libqt4-dev depends on libqt4-svg (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package l
dpkg: error processing package libqt4-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libphonon-dev:
 libphonon-dev depends on libphonon4 (= 4:4.7.80-0ubuntu2); however:
  Package libphonon4:amd64 is not configured yet.
 libphonon-dev depends on phonon-backend-null | phonon; however:
  Package phonon-backend-null is not installed.
  Package phonon:amd64 is not configured yet.
 libphonon-dev depends on libqt4-dev (>= 4:4.8.1); however:
  Package libqt4-dev is not configured yet.
 libphonon-dev depends on libqt4-designer (>= 4:4.8.1); however:
  Package libqt4-designer:amd64 is not configured yet.
 libphonon-dev depends on libqtgui4 (>= 4:4.8.1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libphonon-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kdelibs5-dev:
 kdelibs5-dev depends on kdelibs-bin (= 4:4.14.1-0ubuntu1); however:
  Package kdelibs-bin is not configured yet.
 kdelibs5-dev depends on kdoctools (= 4:4.14.1-0ubuntu1); however:
  Package kdoctools is not configured yet.
 kdelibs5-dev depends on libkdeui5 (= 4:4.14.1-0ubuntu1); however:
  Package libkdeui5 is not configured yet.
 kdelibs5-dev depends on libkjsembed4 (= 4:4.14.1-0ubuntu1); however:
  Package libkjsembed4 is not configured yet.
 kdelibs5-dev depends on libkio5 (= 4:4.14.1-0ubuntu1); however:
  Package libkio5 is not configured yet.
 kdelibs5-dev depends on libsolid4 (= 4:4.14.1-0ubuntu1); however:
  Package libsolid4 is not configured yet.
 kdelibs5-dev depends on libkde3support4 (= 4:4.14.1-0ubuntu1); however:
  Package libkde3support4 is not configured yet.
 kdelibs5-dev depends on libkfile4 (= 4:4.14.1-0ubuntu1); however:
  Package libkfile4 is not configured yet.
 kdelibs5-dev depends on libknewstuff2-4 (= 4:4.14.1-0ubuntu1); ho
dpkg: error processing package kdelibs5-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kdenetwork-filesharing:
 kdenetwork-filesharing depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 kdenetwork-filesharing depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 kdenetwork-filesharing depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package kdenetwork-filesharing (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kernel-package:
 kernel-package depends on kmod; however:
  Package kmod is not configured yet.

No apport report written because MaxReports is reached already
                                                              dpkg: error processing package kernel-package (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kstars:
 kstars depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kstars depends on libkdeclarative5 (>= 4:4.7.0); however:
  Package libkdeclarative5 is not configured yet.
 kstars depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 kstars depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 kstars depends on libknewstuff3-4 (>= 4:4.14.1); however:
  Package libknewstuff3-4 is not configured yet.
 kstars depends on libqt4-declarative (>= 4:4.7.0~rc1); however:
  Package libqt4-declarative:amd64 is not configured yet.
 kstars depends on libqt4-opengl (>= 4:4.6.1); however:
  Package libqt4-opengl:amd64 is not configured yet.
 kstars depends on libqt4-svg (>= 4:4.5.3); however:
  Package libqt4-svg:amd64 is not configured yet.
 kstars depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package kstars (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kwin-style-qtcurve:
 kwin-style-qtcurve depends on libkdecorations4abi2 (>= 4:4.11.1); however:
  Package libkdecorations4abi2 is not configured yet.
 kwin-style-qtcurve depends on libkdeui5 (>= 4:4.3.4); however:
  Package libkdeui5 is not configured yet.
 kwin-style-qtcurve depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package kwin-style-qtcurve (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of language-selector-gnome:
 language-selector-gnome depends on language-selector-common (= 0.135); however:
  Package language-selector-common is not configured yet.

dpkg: error processing package language-selector-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libakonadi-kde4:
 libakonadi-kde4 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libakonadi-kde4 depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 libakonadi-kde4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.
 libakonadi-kde4 depends on libsolid4 (>= 4:4.14.1); however:
  Package libsolid4 is not configured yet.

dpkg: error processing package libakonadi-kde4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkldap4:
 libkldap4 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libkldap4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkldap4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkresources4:
 libkresources4 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libkresources4 depends on libqtgui4 (>= 4:4.8); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkresources4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkabc4:
 libkabc4 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libkabc4 depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 libkabc4 depends on libkldap4 (= 4:4.14.1-0ubuntu1); however:
  Package libkldap4 is not configured yet.
 libkabc4 depends on libkresources4 (= 4:4.14.1-0ubuntu1); however:
  Package libkresources4 is not configured yet.
 libkabc4 depends on libqtgui4 (>= 4:4.8); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkabc4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkcalcore4:
 libkcalcore4 depends on libqtgui4 (>= 4:4.8); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkcalcore4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkpimutils4:
 libkpimutils4 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libkpimutils4 depends on libkemoticons4 (>= 4:4.14.1); however:
  Package libkemoticons4 is not configured yet.
 libkpimutils4 depends on libqtgui4 (>= 4:4.8); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkpimutils4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libakonadi-contact4:
 libakonadi-contact4 depends on libakonadi-kde4 (= 4:4.14.1-0ubuntu1); however:
  Package libakonadi-kde4 is not configured yet.
 libakonadi-contact4 depends on libkabc4 (= 4:4.14.1-0ubuntu1); however:
  Package libkabc4 is not configured yet.
 libakonadi-contact4 depends on libkcalcore4 (= 4:4.14.1-0ubuntu1); however:
  Package libkcalcore4 is not configured yet.
 libakonadi-contact4 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libakonadi-contact4 depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 libakonadi-contact4 depends on libkpimutils4 (= 4:4.14.1-0ubuntu1); however:
  Package libkpimutils4 is not configured yet.
 libakonadi-contact4 depends on libphonon4 (>= 4:4.2.0); however:
  Package libphonon4:amd64 is not configured yet.
 libakonadi-contact4 depends on libprison0 (>= 1.0); however:
  Package libprison0:amd64 is not configured yet.
 libakonadi-contact4 de
dpkg: error processing package libakonadi-contact4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwxgtk3.0-dev:
 libwxgtk3.0-dev depends on libwxgtk3.0-0 (= 3.0.1-3); however:
  Package libwxgtk3.0-0:amd64 is not configured yet.

dpkg: error processing package libwxgtk3.0-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwxgtk-media3.0-dev:
 libwxgtk-media3.0-dev depends on libwxgtk-media3.0-0 (= 3.0.1-3); however:
  Package libwxgtk-media3.0-0:amd64 is not configured yet.
 libwxgtk-media3.0-dev depends on libwxgtk3.0-dev (= 3.0.1-3); however:
  Package libwxgtk3.0-dev is not configured yet.

dpkg: error processing package libwxgtk-media3.0-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libalien-wxwidgets-perl:
 libalien-wxwidgets-perl depends on libwxgtk3.0-dev (>= 3.0.1-3); however:
  Package libwxgtk3.0-dev is not configured yet.
 libalien-wxwidgets-perl depends on libwxgtk3.0-dev (<< 3.0.2~); however:
  Package libwxgtk3.0-dev is not configured yet.
 libalien-wxwidgets-perl depends on libwxgtk-media3.0-dev (>= 3.0.1-3); however:
  Package libwxgtk-media3.0-dev is not configured yet.
 libalien-wxwidgets-perl depends on libwxgtk-media3.0-dev (<< 3.0.2~); however:
  Package libwxgtk-media3.0-dev is not configured yet.

dpkg: error processing package libalien-wxwidgets-perl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2 (>= 2.4); however:
  Package apache2 is not configured yet.

dpkg: error processing package libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libatspi2.0-dev:
 libatspi2.0-dev depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing package libatspi2.0-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libatk-bridge2.0-dev:amd64:
 libatk-bridge2.0-dev:amd64 depends on libatspi2.0-dev; however:
  Package libatspi2.0-dev is not configured yet.

dpkg: error processing package libatk-bridge2.0-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libbaloofiles4:
 libbaloofiles4 depends on libsolid4 (>= 4:4.14.1); however:
  Package libsolid4 is not configured yet.

dpkg: error processing package libbaloofiles4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libcanberra-pulse:amd64:
 libcanberra-pulse:amd64 depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package libcanberra-pulse:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgconf2-dev:
 libgconf2-dev depends on gconf2 (= 3.2.6-2ubuntu1); however:
  Package gconf2 is not configured yet.

dpkg: error processing package libgconf2-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgtk-3-dev:
 libgtk-3-dev depends on libatk-bridge2.0-dev; however:
  Package libatk-bridge2.0-dev:amd64 is not configured yet.

dpkg: error processing package libgtk-3-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgcr-3-dev:
 libgcr-3-dev depends on libgtk-3-dev (>= 3.0.0); however:
  Package libgtk-3-dev is not configured yet.

dpkg: error processing package libgcr-3-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgoa-backend-1.0-dev:
 libgoa-backend-1.0-dev depends on libgtk-3-dev; however:
  Package libgtk-3-dev is not configured yet.

dpkg: error processing package libgoa-backend-1.0-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgoa-1.0-dev:
 libgoa-1.0-dev depends on libgoa-backend-1.0-dev; however:
  Package libgoa-backend-1.0-dev is not configured yet.
 libgoa-1.0-dev depends on libgtk-3-dev; however:
  Package libgtk-3-dev is not configured yet.

dpkg: error processing package libgoa-1.0-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgdata-dev:
 libgdata-dev depends on libgcr-3-dev; however:
  Package libgcr-3-dev is not configured yet.
 libgdata-dev depends on libgoa-1.0-dev (>= 3.8); however:
  Package libgoa-1.0-dev is not configured yet.

dpkg: error processing package libgdata-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of x11-apps:
 x11-apps depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package x11-apps (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xbase-clients:
 xbase-clients depends on x11-apps; however:
  Package x11-apps is not configured yet.
 xbase-clients depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package xbase-clients (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.No apport report written because MaxReports is reached already


dpkg: error processing package libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-vfs-perl:
 libgnome2-vfs-perl depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0:amd64 is not configured yet.

dpkg: error processing package libgnome2-vfs-perl (--configure):
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                             dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-perl:
 libgnome2-perl depends on libgnome2-vfs-perl; however:
  Package libgnome2-vfs-perl is not configured yet.

dpkg: error processing package libgnome2-perl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgnomevfs2-dev:amd64:
 libgnomevfs2-dev:amd64 depends on libgnomevfs2-0 (= 1:2.24.4-6ubuntu1); however:
  Package libgnomevfs2-0:amd64 is not configured yet.
 libgnomevfs2-dev:amd64 depends on libgconf2-dev (>= 2.8.0-1); however:
  Package libgconf2-dev is not configured yet.

dpkg: error processing package libgnomevfs2-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgnomevfs2-extra:amd64:
 libgnomevfs2-extra:amd64 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0:amd64 is not configured yet.
 libgnomevfs2-extra:amd64 depends on libgnomevfs2-common (= 1:2.24.4-6ubuntu1); however:
  Package libgnomevfs2-common is not configured yet.

dpkg: error processing package libgnomevfs2-extra:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libice-dev:amd64:
 libice-dev:amd64 depends on libice6 (= 2:1.0.9-1); however:
  Package libice6:amd64 is not configured yet.

dpkg: error processing package libice-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libsm-dev:amd64:
 libsm-dev:amd64 depends on libsm6 (= 2:1.2.2-1); however:
  Package libsm6:amd64 is not configured yet.
 libsm-dev:amd64 depends on libice-dev (>= 1:1.0.0-1); however:
  Package libice-dev:amd64 is not configured yet.

dpkg: error processing package libsm-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgtkglext1-dev:
 libgtkglext1-dev depends on libice-dev; however:
  Package libice-dev:amd64 is not configured yet.
 libgtkglext1-dev depends on libsm-dev; however:
  Package libsm-dev:amd64 is not configured yet.

dpkg: error processing package libgtkglext1-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkcompactdisc-dev:
 libkcompactdisc-dev depends on libkcompactdisc4 (= 4:4.14.1-0ubuntu1); however:
  Package libkcompactdisc4 is not configured yet.

dpkg: error processing package libkcompactdisc-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkcddb-dev:
 libkcddb-dev depends on libkcddb4 (= 4:4.14.1-0ubuntu1); however:
  Package libkcddb4 is not configured yet.
 libkcddb-dev depends on libkcompactdisc-dev; however:
  Package libkcompactdisc-dev is not configured yet.

dpkg: error processing package libkcddb-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkephal4abi1:
 libkephal4abi1 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkephal4abi1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkonq-common:
 libkonq-common depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 libkonq-common depends on libphonon4 (>= 4:4.3.0); however:
  Package libphonon4:amd64 is not configured yet.
 libkonq-common depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.
 libkonq-common depends on phonon; however:
  Package phonon:amd64 is not configured yet.

dpkg: error processing package libkonq-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkonq5abi1:
 libkonq5abi1 depends on libkonq-common (>= 4:4.14.1-0ubuntu1); however:
  Package libkonq-common is not configured yet.
 libkonq5abi1 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libkonq5abi1 depends on libkfile4 (>= 4:4.14.1); however:
  Package libkfile4 is not configured yet.
 libkonq5abi1 depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 libkonq5abi1 depends on libkparts4 (>= 4:4.14.1); however:
  Package libkparts4 is not configured yet.
 libkonq5abi1 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkonq5abi1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkontactinterface4:
 libkontactinterface4 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libkontactinterface4 depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 libkontactinterface4 depends on libkparts4 (>= 4:4.14.1); however:
  Package libkparts4 is not configured yet.
 libkontactinterface4 depends on libqtgui4 (>= 4:4.8); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkontactinterface4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libnjb-dev:amd64:
 libnjb-dev:amd64 depends on libnjb5 (= 2.2.7~dfsg0-4); however:
  Package libnjb5:amd64 is not configured yet.

dpkg: error processing package libnjb-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkscreen1:
 libkscreen1 depends on libkdeui5 (>= 4:4.5.85); however:
  Package libkdeui5 is not configured yet.
 libkscreen1 depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libkscreen1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libokularcore5:
 libokularcore5 depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 libokularcore5 depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 libokularcore5 depends on libkscreen1 (>= 1.0.2); however:
  Package libkscreen1 is not configured yet.
 libokularcore5 depends on libphonon4 (>= 4:4.2.0); however:
  Package libphonon4:amd64 is not configured yet.
 libokularcore5 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.
 libokularcore5 depends on phonon; however:
  Package phonon:amd64 is not configured yet.

dpkg: error processing package libokularcore5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libowncloudsync0:
 libowncloudsync0 depends on libqtgui4 (>= 4:4.6.1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libowncloudsync0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqca2-dev:
 libqca2-dev depends on libqt4-dev (>= 4.4.0~); however:
  Package libqt4-dev is not configured yet.

dpkg: error processing package libqca2-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqmobipocket1:
 libqmobipocket1 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqmobipocket1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqscintilla2-11:No apport report written because MaxReports is reached already

 libqscintilla2-11 depends on libqtgui4 (>= 4:4.8.0~); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqscintilla2-11 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt4-gui:
 libqt4-gui depends on libqt4-designer (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-designer:amd64 is not configured yet.
 libqt4-gui depends on libqt4-opengl (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-opengl:amd64 is not configured yet.
 libqt4-gui depends on libqt4-svg (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-svg:amd64 is not configured yet.
 libqt4-gui depends on libqtgui4 (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package libqt4-gui (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt4-opengl-dev:
 libqt4-opengl-dev depends on libqt4-dev (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-dev is not configured yet.
 libqt4-opengl-dev depends on libqt4-opengl (= 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1); however:
  Package libqt4-opengl:amd64 is not configured yet.

dpkg: error processing package libqt4-opengl-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt5webkit5-qmlwebkitplugin:
 libqt5webkit5-qmlwebkitplugin depends on qml-module-qtwebkit; however:
  Package qml-module-qtwebkit:amd64 is not configured yet.

dpkg: error processing package libqt5webkit5-qmlwebkitplugin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libsnmp-dev:
 libsnmp-dev depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package libsnmp-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libstrigiqtdbusclient-dev:
 libstrigiqtdbusclient-dev depends on libqt4-dev (>= 4.4.0~); however:
  Package libqt4-dev is not configured yet.

dpkg: error processing package libstrigiqtdbusclient-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of unity-services:
 unity-services depends on upstart-bin; however:
  Package upstart-bin is not configured yet.

dpkg: error processing package unity-services (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libunity-core-6.0-9:
 libunity-core-6.0-9 depends on unity-services (= 7.3.1+14.10.20141016-0ubuntu1); however:
  Package unity-services is not configured yet.

dpkg: error processing package libunity-core-6.0-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libvtk-java:
 libvtk-java depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.
No apport report written because MaxReports is reached already

dpkg: error processing package libvtk-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libvtkgdcm2.2:
 libvtkgdcm2.2 depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.

dpkg: error processing package libvtkgdcm2.2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of libvtkgdcm-java:
 libvtkgdcm-java depends on libvtk-java; however:
  Package libvtk-java is not configured yet.
 libvtkgdcm-java depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.
 libvtkgdcm-java depends on libvtkgdcm2.2; however:
  Package libvtkgdcm2.2 is not configured yet.

dpkg: error processing package libvtkgdcm-java (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libvtkgdcm-tools:
 libvtkgdcm-tools depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.
 libvtkgdcm-tools depends on libvtkgdcm2.2; however:
  Package libvtkgdcm2.2 is not configured yet.

dpkg: error processing package libvtkgdcm-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libvtkgdcm2-dev:
 libvtkgdcm2-dev depends on libvtkgdcm2.2 (= 2.2.4-1.1ubuntu7); however:
  Package libvtkgdcm2.2 is not configured yet.

dpkg: error processing package libvtkgdcm2-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwxgtk2.8-dev:
 libwxgtk2.8-dev depends on libwxgtk2.8-0 (= 2.8.12.1+dfsg2-2ubuntu1); however:
  Package libwxgtk2.8-0:amd64 is not configured yet.

dpkg: error processing package libwxgtk2.8-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwxgtk-media2.8-dev:
 libwxgtk-media2.8-dev depends on libwxgtk-media2.8-0 (= 2.8.12.1+dfsg2-2ubuntu1); however:
  Package libwxgtk-media2.8-0:amd64 is not configured yet.
 libwxgtk-media2.8-dev depends on libwxgtk2.8-dev (= 2.8.12.1+dfsg2-2ubuntu1); however:
  Package libwxgtk2.8-dev is not configured yet.

dpkg: error processing package libwxgtk-media2.8-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.16.0-24-generic:
 linux-image-extra-3.16.0-24-generic depends on linux-image-3.16.0-24-generic; however:
  Package linux-image-3.16.0-24-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.16.0-24-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up thermald (1.3-6) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package thermald (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.16.0-24-generic; however:
  Package linux-image-3.16.0-24-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.16.0-24-generic; however:
  Package linux-image-extra-3.16.0-24-generic is not configured yet.
 linux-image-generic depends on thermald; however:
  Package thermald is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.16.0.24.25); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of lives:
 lives depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package lives (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-wxgtk2.8:
 python-wxgtk2.8 depends on libwxgtk-media2.8-0 (>= 2.8.12.1+dfsg2); however:
  Package libwxgtk-media2.8-0:amd64 is not configured yet.
 python-wxgtk2.8 depends on libwxgtk2.8-0 (>= 2.8.12.1+dfsg2); however:
  Package libwxgtk2.8-0:amd64 is not configured yet.

dpkg: error processing package python-wxgtk2.8 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyface:
 python-pyface depends on python-wxgtk2.8; however:
  Package python-wxgtk2.8 is not configured yet.
 python-pyface depends on python-qt4; however:
  Package python-qt4 is not configured yet.

dpkg: error processing package python-pyface (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-traitsui:
 python-traitsui depends on python-pyface; however:
  Package python-pyface is not configured yet.
 python-traitsui depends on python-wxgtk2.8; however:
  Package python-wxgtk2.8 is not configured yet.

dpkg: error processing package python-traitsui (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-apptools:
 python-apptools depends on python-traitsui; however:
  Package python-traitsui is not configured yet.

dpkg: error processing package python-apptools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of tcl-vtk:
 tcl-vtk depends on libvtk5.8 (= 5.8.0-17.3ubuntu2); however:
  Package libvtk5.8 is not configured yet.

dpkg: error processing package tcl-vtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-vtk:
 python-vtk depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.
 python-vtk depends on tcl-vtk; however:
  Package tcl-vtk is not configured yet.

dpkg: error processing package python-vtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-envisage:
 python-envisage depends on python-apptools; however:
  Package python-apptools is not configured yet.

dpkg: error processing package python-envisage (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mayavi2:
 mayavi2 depends on python-apptools (>= 4.0.0-1); however:
  Package python-apptools is not configured yet.
 mayavi2 depends on python-traitsui; however:
  Package python-traitsui is not configured yet.
 mayavi2 depends on python-wxgtk2.8; however:
  Package python-wxgtk2.8 is not configured yet.
 mayavi2 depends on python-vtk (>= 5.4.2-5); however:
  Package python-vtk is not configured yet.
 mayavi2 depends on python-envisage; however:
  Package python-envisage is not configured yet.

dpkg: error processing package mayavi2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mriconvert:
 mriconvert depends on libwxgtk3.0-0 (>= 3.0.0); however:
  Package libwxgtk3.0-0:amd64 is not configured yet.

dpkg: error processing package mriconvert (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of nautilus-actions:
 nautilus-actions depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 nautilus-actions depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package nautilus-actions (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of nautilus-dropbox:
 nautilus-dropbox depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package nautilus-dropbox (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on nautilus (>= 1:2.91); however:
  Package nautilus is not configured yet.

dpkg: error processing package nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of nvidia-common:
 nvidia-common depends on ubuntu-drivers-common; however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing package nvidia-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package openssh-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of owncloud-client:
 owncloud-client depends on libowncloudsync0 (= 1.6.3+dfsg-0ubuntu1); however:
  Package libowncloudsync0 is not configured yet.
 owncloud-client depends on libqtgui4 (>= 4:4.7.0~beta1); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package owncloud-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pgadmin3:
 pgadmin3 depends on libwxgtk3.0-0 (>= 3.0.0); however:
  Package libwxgtk3.0-0:amd64 is not configured yet.

dpkg: error processing package pgadmin3 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 pidgin depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.
 pidgin depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package pidgin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pinentry-qt4:
 pinentry-qt4 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package pinentry-qt4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of planner:
 planner depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package planner (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.9.0-0ubuntu7); however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-label (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-kubuntu-logo:
 plymouth-theme-kubuntu-logo depends on plymouth; however:
  Package plymouth is not configured yet.
 plymouth-theme-kubuntu-logo depends on plymouth-label; however:
  Package plymouth-label is not configured yet.

dpkg: error processing package plymouth-theme-kubuntu-logo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-kubuntu-text:
 plymouth-theme-kubuntu-text depends on plymouth; however:
  Package plymouth is not configured yet.
 plymouth-theme-kubuntu-text depends on plymouth-theme-ubuntu-text; however:
  Package plymouth-theme-ubuntu-text is not configured yet.

dpkg: error processing package plymouth-theme-kubuntu-text (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-logo:
 plymouth-theme-ubuntu-logo depends on plymouth; however:
  Package plymouth is not configured yet.
 plymouth-theme-ubuntu-logo depends on plymouth-label; however:
  Package plymouth-label is not configured yet.

dpkg: error processing package plymouth-theme-ubuntu-logo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-theme-xubuntu-logo:No apport report written because MaxReports is reached already

 plymouth-theme-xubuntu-logo depends on plymouth; however:
  Package plymouth is not configured yet.
 plymouth-theme-xubuntu-logo depends on plymouth-label; however:
  Package plymouth-label is not configured yet.

dpkg: error processing package plymouth-theme-xubuntu-logo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-xubuntu-text:
 plymouth-theme-xubuntu-text depends on plymouth; however:
  Package plymouth is not configured yet.
 plymouth-theme-xubuntu-text depends on plymouth-theme-ubuntu-text; however:
  Package plymouth-theme-ubuntu-text is not configured yet.

dpkg: error processing package plymouth-theme-xubuntu-text (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-x11:
 plymouth-x11 depends on plymouth (= 0.9.0-0ubuntu7); however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-x11 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up postfix (2.11.1-1) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of postgresql-common:
 postgresql-common depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package postgresql-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-9.4:
 postgresql-9.4 depends on postgresql-common (>= 142~); however:
  Package postgresql-common is not configured yet.

No apport report written because MaxReports is reached already
                                                              dpkg: error processing package postgresql-9.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-9.4; however:
  Package postgresql-9.4 is not configured yet.

dpkg: error processing package postgresql (--configure):
 dependency problems - leaving unconfiguredNo apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already

dpkg: dependency problems prevent configuration of printer-driver-splix:
 printer-driver-splix depends on cups (>= 1.5.0-3~); however:
  Package cups is not configured yet.

dpkg: error processing package printer-driver-splix (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-esound-compat:
 pulseaudio-esound-compat depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-esound-compat (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-module-gconf:
 pulseaudio-module-gconf depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-module-gconf (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-utils:
 pulseaudio-utils depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 pulseaudio-utils depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.

dpkg: error processing package pulseaudio-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-module-x11:
 pulseaudio-module-x11 depends on libice6 (>= 1:1.0.0); however:
  Package libice6:amd64 is not configured yet.
 pulseaudio-module-x11 depends on libsm6; however:
  Package libsm6:amd64 is not configured yet.
 pulseaudio-module-x11 depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
 pulseaudio-module-x11 depends on pulseaudio-utils; however:
  Package pulseaudio-utils is not configured yet.

dpkg: error processing package pulseaudio-module-x11 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-chaco:
 python-chaco depends on python-traitsui; however:
  Package python-traitsui is not configured yet.
 python-chaco depends on python-wxgtk2.8; however:
  Package python-wxgtk2.8 is not configured yet.

dpkg: error processing package python-chaco (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qtgui:
 python-pyside.qtgui depends on libqtgui4 (>= 4:4.8.5); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-pyside.qtgui (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.phonon:
 python-pyside.phonon depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.phonon depends on libphonon4 (>= 4:4.7.0.0); however:
  Package libphonon4:amd64 is not configured yet.
 python-pyside.phonon depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4:amd64 is not configured yet.
 python-pyside.phonon depends on phonon; however:
  Package phonon:amd64 is not configured yet.

dpkg: error processing package python-pyside.phonon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qtdeclarative:
 python-pyside.qtdeclarative depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.qtdeclarative depends on libqt4-declarative (>= 4:4.7.0); however:
  Package libqt4-declarative:amd64 is not configured yet.
 python-pyside.qtdeclarative depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-pyside.qtdeclarative (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qthelp:
 python-pyside.qthelp depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.qthelp depends on libqt4-help (>= 4:4.8.0); however:
  Package libqt4-help:amd64 is not configured yet.
 python-pyside.qthelp depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-pyside.qthelp (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qtopengl:
 python-pyside.qtopengl depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.qtopengl depends on libqt4-opengl (>= 4:4.8.0); however:
  Package libqt4-opengl:amd64 is not configured yet.
 python-pyside.qtopengl depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-pyside.qtopengl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qtscript:
 python-pyside.qtscript depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.qtscript depends on libqt4-scripttools (>= 4:4.7.0); however:
  Package libqt4-scripttools:amd64 is not configured yet.

dpkg: error processing package python-pyside.qtscript (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qtsql:
 python-pyside.qtsql depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.qtsql depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-pyside.qtsql (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qtsvg:
 python-pyside.qtsvg depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.qtsvg depends on libqt4-svg (>= 4:4.7.0); however:
  Package libqt4-svg:amd64 is not configured yet.
 python-pyside.qtsvg depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-pyside.qtsvg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qttest:
 python-pyside.qttest depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.qttest depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-pyside.qttest (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qtuitools:
 python-pyside.qtuitools depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.qtuitools depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-pyside.qtuitools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside.qtwebkit:
 python-pyside.qtwebkit depends on python-pyside.qtgui (= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside.qtwebkit depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-pyside.qtwebkit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pyside:
 python-pyside depends on python-pyside.phonon (>= 1.2.2-1); however:
  Package python-pyside.phonon is not configured yet.
 python-pyside depends on python-pyside.qtdeclarative (>= 1.2.2-1); however:
  Package python-pyside.qtdeclarative is not configured yet.
 python-pyside depends on python-pyside.qtgui (>= 1.2.2-1); however:
  Package python-pyside.qtgui is not configured yet.
 python-pyside depends on python-pyside.qthelp (>= 1.2.2-1); however:
  Package python-pyside.qthelp is not configured yet.
 python-pyside depends on python-pyside.qtopengl (>= 1.2.2-1); however:
  Package python-pyside.qtopengl is not configured yet.
 python-pyside depends on python-pyside.qtscript (>= 1.2.2-1); however:
  Package python-pyside.qtscript is not configured yet.
 python-pyside depends on python-pyside.qtsql (>= 1.2.2-1); however:
  Package python-pyside.qtsql is not configured yet.
 python-pyside depends on python-pyside.qtsvg (>= 1.2.2-1); however:
  Packag
dpkg: error processing package python-pyside (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-qt4-gl:
 python-qt4-gl depends on python-qt4 (= 4.11.2+dfsg-1); however:
  Package python-qt4 is not configured yet.
 python-qt4-gl depends on libqt4-opengl (>= 4:4.8.0-1~); however:
  Package libqt4-opengl:amd64 is not configured yet.
 python-qt4-gl depends on libqtgui4 (>= 4:4.8.0-1~); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-qt4-gl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-secretstorage:
 python-secretstorage depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing package python-secretstorage (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up unattended-upgrades (0.82.8) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package unattended-upgrades (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.

dpkg: error processing package python3-software-properties (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3-software-properties (= 0.94); however:
  Package python3-software-properties is not configured yet.

dpkg: error processing package software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-software-properties:
 python-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.No apport report written because MaxReports is reached already


dpkg: error processing package python-software-properties (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-vtkgdcm:
 python-vtkgdcm depends on libvtk5.8; however:
  Package libvtk5.8 is not configured yet.
 python-vtkgdcm depends on libvtkgdcm2.2 (= 2.2.4-1.1ubuntu7); however:
  Package libvtkgdcm2.2 is not configured yet.
 python-vtkgdcm depends on python-vtk; however:
  Package python-vtk is not configured yet.

dpkg: error processing package python-vtkgdcm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-pyqt4:
 python3-pyqt4 depends on libqt4-declarative (>= 4:4.8.0-1~); however:
  Package libqt4-declarative:amd64 is not configured yet.
 python3-pyqt4 depends on libqt4-designer (>= 4:4.8.0-1~); however:
  Package libqt4-designer:amd64 is not configured yet.
 python3-pyqt4 depends on libqt4-help (>= 4:4.8.0-1~); however:
  Package libqt4-help:amd64 is not configured yet.
 python3-pyqt4 depends on libqt4-scripttools (>= 4:4.8.0-1~); however:
  Package libqt4-scripttools:amd64 is not configured yet.
 python3-pyqt4 depends on libqt4-svg (>= 4:4.8.0-1~); however:
  Package libqt4-svg:amd64 is not configured yet.
 python3-pyqt4 depends on libqtgui4 (>= 4:4.8.0-1~); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python3-pyqt4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qapt-batch:
 qapt-batch depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 qapt-batch depends on libkdeui5 (>= 4:4.3.4); however:
  Package libkdeui5 is not configured yet.
 qapt-batch depends on libkio5 (>= 4:4.3.4); however:
  Package libkio5 is not configured yet.
 qapt-batch depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.
 qapt-batch depends on libqapt2-runtime; however:
  Package libqapt2-runtime is not configured yet.

dpkg: error processing package qapt-batch (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up qemu-system-x86 (2.1+dfsg-4ubuntu6) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Service mountkernfs has to be enabled to start service qemu-system-x86
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package qemu-system-x86 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qemu-kvm:
 qemu-kvm depends on qemu-system-x86 (>= 1.7.0+dfsg-2~); however:
  Package qemu-system-x86 is not configured yet.

dpkg: error processing package qemu-kvm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qemu-system:
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                             qemu-system depends on qemu-system-x86; however:
  Package qemu-system-x86 is not configured yet.

dpkg: error processing package qemu-system (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qemu:
 qemu depends on qemu-system (>= 2.1+dfsg-4ubuntu6); however:
  Package qemu-system is not configured yet.

dpkg: error processing package qemu (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qemu-user-binfmt:
 qemu-user-binfmt depends on binfmt-support; however:
  Package binfmt-support is not configured yet.

dpkg: error processing package qemu-user-binfmt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qt4-default:
 qt4-default depends on libqt4-dev; however:
  Package libqt4-dev is not configured yet.

dpkg: error processing package qt4-default (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qtdeclarative5-accounts-plugin:amd64:
 qtdeclarative5-accounts-plugin:amd64 depends on qtdeclarative5-qtquick2-plugin; however:
  Package qtdeclarative5-qtquick2-plugin:amd64 is not configured yet.

dpkg: error processing package qtdeclarative5-accounts-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qtdeclarative5-privatewidgets-plugin:amd64:
 qtdeclarative5-privatewidgets-plugin:amd64 depends on qml-module-qtquick-privatewidgets; however:
  Package qml-module-qtquick-privatewidgets:amd64 is not configured yet.

dpkg: error processing package qtdeclarative5-privatewidgets-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of qutecom:
 qutecom depends on libqt4-svg (>= 4:4.5.3); however:
  Package libqt4-svg:amd64 is not configured yet.
 qutecom depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package qutecom (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of remmina:
 remmina depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package remmina (--configure):No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of remmina-plugin-rdp:
 remmina-plugin-rdp depends on remmina (= 1.0.0-6ubuntu1); however:
  Package remmina is not configured yet.

dpkg: error processing package remmina-plugin-rdp (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of remmina-plugin-vnc:
 remmina-plugin-vnc depends on remmina (= 1.0.0-6ubuntu1); however:
  Package remmina is not configured yet.

dpkg: error processing package remmina-plugin-vnc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of rhythmbox-plugin-magnatune:
 rhythmbox-plugin-magnatune depends on rhythmbox (= 3.0.3-1ubuntu2); however:
  Package rhythmbox is not configured yet.

dpkg: error processing package rhythmbox-plugin-magnatune (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up spamassassin (3.4.0-3) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package spamassassin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sa-compile:
 sa-compile depends on spamassassin (>= 3.3.2-8); however:
  Package spamassassin is not configured yet.

dpkg: error processing package sa-compile (--configure):
 dependency problems - leaving unconfiguredNo apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already

Setting up screen (4.2.1-2) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package screen (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of scribus:
 scribus depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package scribus (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of seahorse:
 seahorse depends on gcr (>= 3.4); however:
  Package gcr is not configured yet.
 seahorse depends on gnome-keyring (>= 3.4); however:
  Package gnome-keyring is not configured yet.

dpkg: error processing package seahorse (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3-software-properties (= 0.94); however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not configured yet.
 software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.75); however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing package software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of spacefm:
 spacefm depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing package spacefm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of splix:
 splix depends on printer-driver-splix; however:
  Package printer-driver-splix is not configured yet.

dpkg: error processing package splix (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up tor (0.2.4.23-1) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package tor (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of tor-geoipdb:
 tor-geoipdb depends on tor (>= 0.2.4.23-1); however:
  Package tor is not configured yet.

dpkg: error processing package tor-geoipdb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on libtotem0 (>= 3.10.1-1ubuntu6); however:
  Package libtotem0 is not configured yet.
 totem depends on libtotem0 (<< 3.11); however:
  Package libtotem0 is not configured yet.

dpkg: error processing package totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem (= 3.10.1-1ubuntu6); however:
  Package totem is not configured yet.
 totem-mozilla depends on dbus-x11 (>= 0.61); however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems pNo apport report written because MaxReports is reached already
         No apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                     revent configuration of totem-plugins:
 totem-plugins depends on libtotem0 (>= 3.10.1-1ubuntu6); however:
  Package libtotem0 is not configured yet.
 totem-plugins depends on libtotem0 (<< 3.11); however:
  Package libtotem0 is not configured yet.
 totem-plugins depends on totem (= 3.10.1-1ubuntu6); however:
  Package totem is not configured yet.
 totem-plugins depends on gir1.2-totem-1.0 (= 3.10.1-1ubuntu6); however:
  Package gir1.2-totem-1.0 is not configured yet.

dpkg: error processing package totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins-extra:
 totem-plugins-extra depends on totem (= 3.10.1-1ubuntu6); however:
  Package totem is not configured yet.
 totem-plugins-extra depends on libtotem0 (>= 3.10.1-1ubuntu6); however:
  Package libtotem0 is not configured yet.
 totem-plugins-extra depends on libtotem0 (<< 3.11); however:
  Package libtotem0 is not configured yet.

dpkg: error processing pacNo apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  kage totem-plugins-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of transfig:
 transfig depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package transfig (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of transmission-gtk:
 transmission-gtk depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package transmission-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubiquity-frontend-kde:
 ubiquity-frontend-kde depends on python3-pyqt4; however:
  Package python3-pyqt4 is not configured yet.
 ubiquity-frontend-kde depends on kde-window-manager | kwin; however:
  Package kde-window-manager is not configured yet.
  Package kwin is not installed.

dpkg: error processing package ubiquity-frontend-kde (--confNo apport report written because MaxReports is reached already
                                          igure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubiquity:
 ubiquity depends on console-setup (>= 1.70ubuntu9); however:
  Package console-setup is not configured yet.
 ubiquity depends on cryptsetup; however:
  Package cryptsetup is not configured yet.
 ubiquity depends on language-selector-common (>= 0.4.16); however:
  Package language-selector-common is not configured yet.
 ubiquity depends on grub-common; however:
  Package grub-common is not configured yet.
 ubiquity depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.

dpkg: error processing package ubiquity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubiquity-frontend-gtk:
 ubiquity-frontend-gtk depends on ubiquity (= 2.20.0); however:
  Package ubiquity is not configured yet.

dpkg: error processing package ubiquity-frontend-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg:No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                  dependency problems prevent configuration of xserver-common:
 xserver-common depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package xserver-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on xserver-common (>= 2:1.16.0-1ubuntu1); however:
  Package xserver-common is not configured yet.
 xserver-xorg-core depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of unity:
 unity depends on compiz-core; however:
  Package compiz-core is not configured yet.
 unity depends on libunity-core-6.0-9 (= 7.3.1+14.10.20141016-0ubuntu1); however:
  Package libunity-core-6.0-9 is not configured yet.
 unity depends on compiz; however:
  Package compiz is not configured yet.
 unity depends on compiz-core-abiversion-20140123; however:
  Package compiz-core-abiversion-20140123 is not installed.
  Package compiz-core which provides compiz-core-abiversion-20140123 is not configured yet.
 unity depends on compiz-plugins-default; however:
  Package compiz-plugins-default is not configured yet.

dpkg: error processing package unity (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-r128:
 xserver-xorg-video-r128 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-r128 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-r128 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-mach64:
 xserver-xorg-video-mach64 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-mach64 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-mach64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-radeon depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-radeon (--configure)No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  :
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-ati:
 xserver-xorg-video-ati depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-r128; however:
  Package xserver-xorg-video-r128 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-mach64; however:
  Package xserver-xorg-video-mach64 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-radeon; however:
  Package xserver-xorg-video-radeon is not configured yet.

dpkg: error processing package xserver-xorg-video-ati (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xNo apport report written because MaxReports is reached already
                                          org-video-cirrus:
 xserver-xorg-video-cirrus depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-cirrus depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-cirrus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-fbdev:
 xserver-xorg-video-fbdev depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
No apport report written because MaxReports is reached already
                                                                Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-fbdev depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-fbdev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on libxvmc1; however:
  Package libxvmc1:amd64 is not configured yet.
 xserver-xorg-video-intel depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-intel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mga:
No apport report written because MaxReports is reached already
                                                               xserver-xorg-video-mga depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-mga depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-mga (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-modesetting:
 xserver-xorg-video-modesetting depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-modesetting depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-modesetting (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-neomagic:
 xserver-xorg-video-neomagic depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-neomagic depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-neomagic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-nouveau:
 xserver-xorg-video-nouveau depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-nouveau depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-nouveau (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-openchrome:
 xserver-xorg-video-openchrome depends on libxvmc1; however:
  Package libxvmc1:amd64 is not configured yet.
 xserver-xorg-video-openchrome depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-openchrome depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-openchrome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-savage:
 xserver-xorg-video-savage depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.No apport report written because MaxReports is reached already

 xserver-xorg-video-savage depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-savage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-siliconmotion:
 xserver-xorg-video-siliconmotion depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-siliconmotion depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-siliconmotion (--configure):
 dependency problems - leaving unconfiguredNo apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already

dpkg: dependency problems prevent configuration of xserver-xorg-video-sisusb:
 xserver-xorg-video-sisusb depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-sisusb depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-sisusb (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-tdfx:
 xserver-xorg-video-tdfx depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-tdfx depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-tdfx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-trident:
 xserver-xorg-video-trident depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-trident depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-trident (--configure):
 No apport report written because MaxReports is reached already
                                                               No apport report written because MaxReports is reached already
                                             dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vesa:
 xserver-xorg-video-vesa depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-vesa depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-vesa (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-vmware:
 xserver-xorg-video-vmware depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-vmware depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-vmware (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-all:
 xserver-xorg-video-all depends on xserver-xorg-video-ati; however:
  Package xserver-xorg-video-ati is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-cirrus; however:
  Package xserver-xorg-video-cirrus is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-fbdev; however:
  Package xserver-xorg-video-fbdev is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-intel; however:
  Package xserver-xorg-video-intel is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-mga; however:
  Package xserver-xorg-video-mga is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-modesetting; however:
  Package xserver-xorg-video-modesetting is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-neomagic; however:
  Package xserver-xorg-video-neomagic is not configured yet.
 xserver-xorg-video-all depends on xserver-xor
dpkg: error processing package xserver-xorg-video-all (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-s3:
 xserver-xorg-video-s3 depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-s3 depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-s3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-qxl:No apport report written because MaxReports is reached already

 xserver-xorg-video-qxl depends on xorg-video-abi-18; however:
  Package xorg-video-abi-18 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-18 is not configured yet.
 xserver-xorg-video-qxl depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-video-qxl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-evdev:
 xserver-xorg-input-evdev depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.No apport report written because MaxReports is reached already

  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-evdev depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-evdev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-input-mouse:
 xserver-xorg-input-mouse depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-mouse depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-mouse (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-input-vmmouse:
 xserver-xorg-input-vmmouse depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg-input-vmmouse depends on xserver-xorg-input-mouse; however:
  Package xserver-xorg-input-mouse is not configured yet.
 xserver-xorg-input-vmmouse depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package xserver-xorg-input-vmmouse (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-input-synaptics:
 xserver-xorg-input-synaptics depends on udev; however:
  Package udev is not configured yet.
 xserver-xorg-input-synaptics depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-synaptics depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-synaptics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-wacom:No apport report written because MaxReports is reached already

 xserver-xorg-input-wacom depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-wacom depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-wacom (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-all:
 xserver-xorg-input-all depends on xserver-xorg-input-evdev; however:
  Package xserver-xorg-input-evdev is not configured yet.
No apport report written because MaxReports is reached already
                                                               xserver-xorg-input-all depends on xserver-xorg-input-vmmouse; however:
  Package xserver-xorg-input-vmmouse is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-synaptics; however:
  Package xserver-xorg-input-synaptics is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-wacom; however:
  Package xserver-xorg-input-wacom is not configured yet.

dpkg: error processing package xserver-xorg-input-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-mutouch:
 xserver-xorg-input-mutouch depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already

  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-mutouch depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-mutouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-multitouch:
 xserver-xorg-input-multitouch depends on xorg-input-abi-21; however:
  Package xorg-input-abi-21 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-21 is not configured yet.
 xserver-xorg-input-multitouch depends on xserver-xorg-core (>= 2:1.15.99.903); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing package xserver-xorg-input-multitouch (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg:
 xserver-xorg depends on xserver-xorg-core (>= 2:1.15.0.901); however:
  Package xserver-xorg-core is not configured yet.
 xserver-xorg depends on xserver-xorg-video-all | xorg-driver-video; however:
  Package xserver-xorg-video-all is not configured yet.
  Package xorg-driver-video is not installed.
  Package xserver-xorg-video-siliconmotion which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-ati which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-mach64 which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-intel which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-trident which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-s3 which provides xorg-driver-video is not configured yet.
  Package xserver-xorg-video-mga which provides xorg-driver-video is not configured yet.
  Package xserver-xor
dpkg: error processing package xserver-xorg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg (>= 1:7.7+7ubuntu2); however:
  Package xserver-xorg is not configured yet.
 xorg depends on x11-apps; however:
  Package x11-apps is not configured yet.
 xorg depends on xfonts-utils; however:
  Package xfonts-utils is not configured yet.
 xorg depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package xorg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on alsa-utils; however:
  Package alsa-utils is not configured yet.
 ubuntu-desktop depends on anacron; however:
  Package anacron is not configured yet.
 ubuntu-desktop depends on checkbox-gui; however:
  Package checkbox-gui is not configured yet.
 ubuntu-desktop depends on language-selector-gnome; however:
  Package language-selector-gnome is not configured yet.
 ubuntu-desktop depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.
 ubuntu-desktop depends on lightdm; however:
  Package lightdm is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on nautilus-sendto; however:
  Package nautilus-sendto is not configured yet.
 ubuntu-desktop depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
 ubuntu-desktop depends on seahorse; however:
  Package seahorse is not configured yet.
 ubuntu-
dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of unity-2d-common:
 unity-2d-common depends on unity; however:
  Package unity is not configured yet.

dpkg: error processing package unity-2d-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-2d-shell:
 unity-2d-shell depends on unity; however:
  Package unity is not configured yet.

dpkg: error processing package unity-2d-shell (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of unity-control-center-signon:
 unity-control-center-signon depends on unity-control-center; however:
  Package unity-control-center is not configured yet.
 unity-control-center-signon depends on libaccount-plugin-generic-oauth; however:
  Package libaccount-plugin-generic-oauth is not configured yet.
 unity-control-center-signon depends on libaccount-plugin-google; however:
  Package libaccount-plugin-google is not configured yet.
 unity-control-center-signon depends on signon-ui-x11; however:
  Package signon-ui-x11 is not configured yet.

dpkg: error processing package unity-control-center-signon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of unity-tweak-tool:
 unity-tweak-tool depends on unity (>= 6.8); however:
  Package unity is not configured yet.

dpkg: error processing package unity-tweak-tool (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of unity-webapps-qml:
 unity-webapps-qml depends on qml-module-qtwebkit; however:
  Package qml-module-qtwebkit:amd64 is not configured yet.
 unity-webapps-qml depends on liboxideqt-qmlplugin (>= 1.0); however:
  Package liboxideqt-qmlplugin:amd64 is not configured yet.
 unity-webapps-qml depends on qtdeclarative5-qtquick2-plugin; however:
  Package qtdeclarative5-qtquick2-plugin:amd64 is not configured yet.
 unity-webapps-qml depends on qtdeclarative5-ubuntu-ui-toolkit-plugin | qtdeclarative5-ubuntu-ui-toolkit-plugin-gles; however:
  Package qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 is not configured yet.
  Package qtdeclarative5-ubuntu-ui-toolkit-plugin-gles is not installed.
 unity-webapps-qml depends on qtdeclarative5-accounts-plugin; however:
  Package qtdeclarative5-accounts-plugin:amd64 is not configured yet.
 unity-webapps-qml depends on libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2); however:
  Package libqt5gui5:amd64 is not configured yet.
  Packag
dpkg: error processing package unity-webapps-qml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of usb-creator-common:
 usb-creator-common depends on udisks2; however:
  Package udisks2 is not configured yet.No apport report written because MaxReports is reached already


dpkg: error processing package usb-creator-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of usb-creator-gtk:
 usb-creator-gtk depends on usb-creator-common (= 0.2.62); however:
  Package usb-creator-common is not configured yet.

dpkg: error processing package usb-creator-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of vlc:
 vlc depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc (>= 2.2.0~pre2-4build1); however:
  Package vlc is not configured yet.

dpkg: error processing package vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of vym:
 vym depends on libqt4-svg (>= 4:4.5.3); however:
  Package libqt4-svg:amd64 is not configured yet.
 vym depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package vym (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of webapp-container:
 webapp-container depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 webapp-container depends on libqt5quick5 (>= 5.0.2) | libqt5quick5-gles (>= 5.0.2); however:
  Package libqt5quick5:amd64 is not configured yet.
  Package libqt5quick5-gles is not installed.
 webapp-container depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:amd64 is not configured yet.
 webapp-container depends on liboxideqt-qmlplugin (>= 1.2.0); however:
  Package liboxideqt-qmlplugin:amd64 is not configured yet.
 webapp-container depends on qml-module-qtwebkit; however:
  Package qml-module-qtwebkit:amd64 is not configured yet.
 webapp-container depends on qtdeclarative5-accounts-plugin; however:
  Package qtdeclarative5-accounts-plugin:amd64 is not configured yet.
 webapp-container depends on qtdeclarative5-qtquick2-plugin (>= 5.2); howeve
dpkg: error processing package webapp-container (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xaralx:
 xaralx depends on libwxgtk2.8-0 (>= 2.8.12.1+dfsg); however:
  Package libwxgtk2.8-0:amd64 is not configured yet.

dpkg: error processing package xaralx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xaralx-svg:
 xaralx-svg depends on xaralx; however:
  Package xaralx is not configured yet.
 xaralx-svg depends on libwxgtk2.8-0 (>= 2.8.12.1+dfsg); however:
  Package libwxgtk2.8-0:amd64 is not configured yet.

dpkg: error processing package xaralx-svg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of xchat-common:
 xchat-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.

dpkg: error processing package xchat-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.8-7.1ubuntu7); however:
  Package xchat-common is not configured yet.

dpkg: error processing package xchat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xfce4-power-manager:
 xfce4-power-manager depends on upower (<< 0.99); however:
  Package upower is not configured yet.
 xfce4-power-manager depends on systemd-services; however:
  Package systemd-services is not installed.
  Package systemd which provides systemd-services is not configured yet.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg: error processing package xfce4-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xfce4-power-manager-plugins:
 xfce4-power-manager-plugins depends on xfce4-power-manager (>= 0.8.0~); however:
  Package xfce4-power-manager is not configured yet.

dpkg: error processing package xfce4-power-manager-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xine-ui:
 xine-ui depends on libxine2-x; however:
  Package libxine2-x is not configured yet.

dpkg: error processing package xine-ui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xephyr:
 xserver-xephyr depends on xserver-common (>= 2:1.16.0-1ubuntu1); however:
  Package xserver-common is not configured yet.No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already


dpkg: error processing package xserver-xephyr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-default-settings:
 xubuntu-default-settings depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 xubuntu-default-settings depends on x11-common (>= 1:7.6+7ubuntu2); however:
  Package x11-common is not configured yet.

dpkg: error processing package xubuntu-default-settings (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of akonadi-server:
 akonadi-server depends on libqtgui4 (>= 4:4.6.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package akonadi-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of appmenu-qt5:
 appmenu-qt5 depends on libqt5gui5 (>= 5.3.0) | libqt5gui5-gles (>= 5.3.0); however:
  Package libqt5gui5:amd64 is not configured yet.
  Package libqt5gui5-gles is not installed.
 appmenu-qt5 depends on libqt5widgets5 (>= 5.0.2); however:
  Package libqt5widgets5:amd64 is not configured yet.

dpkg: error processing package appmenu-qt5 (--configure):
 dependency problems - leaving unconfiguredNo apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already

dpkg: dependency problems prevent configuration of brltty-x11:
 brltty-x11 depends on brltty (= 5.0-2ubuntu3); however:
  Package brltty is not configured yet.

dpkg: error processing package brltty-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-plugins-extra:
 compiz-plugins-extra depends on compiz-plugins; however:
  Package compiz-plugins is not configured yet.

dpkg: error processing package compiz-plugins-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-plugins-main:
 compiz-plugins-main depends on compiz-plugins; however:
  Package compiz-plugins is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already

dpkg: error processing package compiz-plugins-main (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compizconfig-backend-gconf:
 compizconfig-backend-gconf depends on compiz-gnome; however:
  Package compiz-gnome is not configured yet.
 compizconfig-backend-gconf depends on gconf2; however:
  Package gconf2 is not configured yet.

dpkg: error processing package compizconfig-backend-gconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-compizconfig:
 python-compizconfig depends on libcompizconfig0; however:
  Package libcompizconfig0 is not configured yet.

dpkg: error processing package python-compizconfig (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compizconfig-settings-manager:
 compizconfig-settings-manager depends on python-compizconfig (>= 1:0.9.12+14.10.20140918-0ubuntu1); however:
  PackageNo apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                    python-compizconfig is not configured yet.

dpkg: error processing package compizconfig-settings-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-indicator:
 evolution-indicator depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 evolution-indicator depends on evolution; however:
  Package evolution is not configured yet.

dpkg: error processing package evolution-indicator (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freecad:
 freecad depends on python-pyside; however:
  Package python-pyside is not configured yet.
 freecad depends on libqt4-opengl (>= 4:4.5.3); however:
  Package libqt4-opengl:amd64 is not configured yet.
 freecad depends on libqt4-svg (>= 4:4.5.3); however:
  Package libqt4-svg:amd64 is not configured yet.
No apport report written because MaxReports is reached already
                                                               freecad depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package freecad (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of friends-facebook:
 friends-facebook depends on account-plugin-facebook; however:
  Package account-plugin-facebook is not configured yet.

dpkg: error processing package friends-facebook (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of friends-identica:
 friends-identica depends on account-plugin-identica; however:
  Package account-plugin-identica is not configured yet.

dpkg: error processing package friends-identica (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of friends-twitter:
 friends-twitter depends on account-plugin-twitter; however:
  Package account-plugin-twitter is not configured yet.

dpkg: error processing package friends-twitter (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc (= 2.02~beta2-15); however:
  Package grub-pc is not configured yet.
 grub2 depends on grub-common (= 2.02~beta2-15); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of indicator-printers:
 indicator-printers depends on cups (>= 1.5); however:
  Package cups is not configured yet.

dpkg: error processing package indicator-printers (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde-style-qtcurve:
 kde-style-qtcurve depends on libkdeui5 (>= 4:4.3.4); however:
  Package libkdeui5 is not configured yet.
 kde-style-qtcurve depends on libkio5 (>= 4:4.3.4); however:
  Package libkio5 is not configured yet.
 kde-style-qtcurve depends on libqt4-svg (>= 4:4.5.3); however:
  Package libqt4-svg:amd64 is not configured yet.
 kde-style-qtcurve depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package kde-style-qtcurve (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kpartx:
 kpartx depends on udev (>> 136-1); however:
  Package udev is not configured yet.

dpkg: error processing package kpartx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpartx-boot:
 kpartx-boot depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 kpartx-boot depends on kpartx (>= 0.4.9-3ubuntu10); however:
  Package kpartx is not configured yet.
 kpartx-boot depends on kpartx (<< 0.4.9-3ubuntu10.1~); however:
  Package kpartx is not configured yet.

No apport report written because MaxReports is reached already
                                                              dpkg: error processing package kpartx-boot (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libwebkitgtk-3.0-dev:
 libwebkitgtk-3.0-dev depends on libgtk-3-dev; however:
  Package libgtk-3-dev is not configured yet.

dpkg: error processing package libwebkitgtk-3.0-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on lsb-invalid-mta (>= 4.1+Debian11ubuntu8) | mail-transport-agent; however:
  Package lsb-invalid-mta is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
 lsb-core depends on at; however:
  Package at is not configured yet.
 lsb-core depends on cron | cron-daemon; however:
  Package cron is not configured yet.
  Package cron-daemon is not installed.
  Package cron which provides cron-daemon is not configured yet.
 lsb-core depends on procps; however:
  Package procps is not configured yet.
 lsb-core depends on rsync; however:
  Package rsync is not configured yet.

dpkg: error processing package lsb-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of okular-extra-backends:
 okular-extra-backends depends on libkdeui5 (>= 4:4.14.1); however:
  Package libkdeui5 is not configured yet.
 okular-extra-backends depends on libkhtml5 (>= 4:4.14.1); however:
  Package libkhtml5 is not configured yet.
 okular-extra-backends depends on libkio5 (>= 4:4.14.1); however:
  Package libkio5 is not configured yet.
 okular-extra-backends depends on libokularcore5 (>= 1.7); however:
  Package libokularcore5 is not configured yet.
 okular-extra-backends depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package okular-extra-backends (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-qscintilla2:
 python-qscintilla2 depends on python-qt4 (>= 4.8.3-3~); however:
  Package python-qt4 is not configured yet.
 python-qscintilla2 depends on libqscintilla2-11; however:
  Package libqscintilla2-11 is not configured yet.
 python-qscintilla2 depends on libqtgui4 (>= 4:4.8.0~); however:
  Package libqtgui4:amd64 is not configured yet.

dpkg: error processing package python-qscintilla2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up vdr (2.0.3-2) ...
insserv: warning: script 'K01fnfxd' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package vdr (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of wine1.6-amd64:
 wine1.6-amd64 depends on wine1.6:any (= 1:1.6.2-0ubuntu6); however:
  Package wine1.6 is not configured yet.

dpkg: error processing package wine1.6-amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.19-10ubuntu2) ...
Errors were encountered while processing:
 sysv-rc
 initscripts
 util-linux
 e2fsprogs
 x11-common
 procps
 gpsd
 kmod
 module-init-tools
 upstart-bin
 ifupdown
 grub-common
 udev
 initramfs-tools
 mountall
 plymouth
 upstart
 friendly-recovery
 mdadm
 dbus
 consolekit
 brltty
 bluez
 cron
 resolvconf
 accountsservice
 language-selector-common
 cgmanager
 systemd-shim
 systemd
 libpam-systemd:amd64
 uuid-runtime
 cups-browsed
 cups-daemon
 dbus-x11
 libice6:amd64
 libice6:i386
 libsm6:amd64
 libsm6:i386
 libqtgui4:i386
 libqt4-declarative:i386
 libqtgui4:amd64
 libqt4-declarative:amd64
 libqt4-designer:amd64
 libqt4-designer:i386
 libqt4-help:amd64
 libqt4-scripttools:amd64
 libqt4-scripttools:i386
 libqt4-svg:amd64
 libqt4-svg:i386
 python-qt4
 libdbusmenu-qt2:amd64
 libdbusmenu-qt2:i386
 libkdeui5
 libkcmutils4
 libkdeclarative5
 libsolid4
 libkio5
 libkparts4
 libkdewebkit5
 libkdnssd4
 libknewstuff3-4
 libphonon4:amd64
 libqt4-opengl:amd64
 libqt4-opengl:i386
 libplasma3
 libkactivities-bin
 libktexteditor4
 libkatepartinterfaces4
 katepart
 libkjsembed4
 libkrosscore4
 kdelibs-bin
 kdoctools
 libqt4-qt3support:amd64
 libqt4-qt3support:i386
 libkde3support4
 libkemoticons4
 libkfile4
 libkhtml5
 libpolkit-qt-1-1
 kdelibs5-plugins
 libqapt2-runtime
 plasma-scriptengine-javascript
 libkmediaplayer4
 libknotifyconfig4
 libkubuntu0
 libkxmlrpcclient4
 phonon:amd64
 kde-runtime
 kde-style-oxygen
 kdebase-runtime
 cups-core-drivers
 cups
 printer-driver-hpcups
 hplip
 hplip-gui
 printer-driver-postscript-hp
 printer-driver-gutenprint
 cups-driver-gutenprint
 evolution
 gcr
 gnome-keyring
 gnumeric
 gconf2
 libgnomevfs2-common
 libgnomevfs2-0:amd64
 libvtk5.8
 libvtk5.8-qt4
 libgofigure0
 libmotif-common
 libxm4:amd64
 libmrm4:amd64
 libnjb5:amd64
 samba
 winbind
 libnss-winbind:amd64
 libpam-winbind:amd64
 libpoppler-qt4-4:amd64
 libprison0:amd64
 libqt5gui5:amd64
 libqt5widgets5:amd64
 libqt5opengl5:amd64
 libqt5quick5:amd64
 libqt53d5:amd64
 libqt5multimedia5:amd64
 libqt5feedback5:amd64
 libqt5location5:amd64
 libqt5printsupport5:amd64
 libqt5svg5:amd64
 libqt5webkit5:amd64
 libuil4:amd64
 libwxgtk2.8-0:amd64
 libwxgtk-media2.8-0:amd64
 libwxgtk3.0-0:amd64
 libwxgtk-media3.0-0:amd64
 libwxsvg2:amd64
 libxbae4m:amd64
 libxmhtml1.1:amd64
 libxvmc1:amd64
 apparmor
 lightdm
 linux-image-3.16.0-24-generic
 mysql-server-5.5
 wpasupplicant
 network-manager
 ppp
 qml-module-qtquick2:amd64
 qml-module-qtgraphicaleffects:amd64
 qml-module-qtquick-privatewidgets:amd64
 qml-module-qtquick-dialogs:amd64
 qml-module-qtquick-window2:amd64
 qml-module-qtwebkit:amd64
 qtdeclarative5-qtfeedback-plugin:amd64
 liboxideqtcore0:amd64
 liboxideqt-qmlplugin:amd64
 qtdeclarative5-dialogs-plugin:amd64
 qtdeclarative5-qtquick2-plugin:amd64
 libqt5qml-graphicaleffects
 qtdeclarative5-window-plugin:amd64
 qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64
 qtdeclarative5-ubuntu-web-plugin:amd64
 qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64
 webbrowser-app
 qtgstreamer-plugins:amd64
 xfonts-encodings
 xfonts-utils
 ttf-mscorefonts-installer
 alsa-utils
 ubuntu-drivers-common
 gnustep-base-runtime
 unar
 binfmt-support
 wine1.6
 wine1.6-i386
 xfce4-session
 python-ubuntu-sso-client
 ubuntu-sso-client
 ubuntu-sso-client-qt
 keyboard-configuration
 console-setup
 rsyslog
 ubuntu-minimal
 irqbalance
 plymouth-theme-ubuntu-text
 pppoeconf
 rsync
 ubuntu-standard
 ufw
 empathy
 mcp-account-manager-uoa
 account-plugin-aim
 signon-ui-x11
 signon-ui
 signon-plugin-oauth2
 libaccount-plugin-generic-oauth
 account-plugin-facebook
 account-plugin-flickr
 libaccount-plugin-google
 account-plugin-google
 account-plugin-identica
 account-plugin-jabber
 avahi-daemon
 telepathy-salut
 account-plugin-salut
 account-plugin-twitter
 account-plugin-windows-live
 account-plugin-yahoo
 acpid
 aisleriot
 amide
 anacron
 apache2
 apache2-mpm-prefork
 apparmor-utils
 appmenu-qt:amd64
 apport
 xterm
 apport-gtk
 asterisk
 asterisk-voicemail
 at
 audacity
 aumix-common
 aumix-gtk
 avahi-utils
 bluetooth
 bluez-alsa:amd64
 bluez-alsa:i386
 bluez-cups
 bluez-gstreamer
 bluez-utils
 unity-settings-daemon
 media-player-info
 rhythmbox
 rhythmbox-plugins
 rhythmbox-plugin-zeitgeist
 rhythmbox-plugin-cdrecorder
 rhythmbox-mozilla
 udisks2
 gvfs-daemons
 gvfs:amd64
 nautilus
 gvfs:i386
 brasero
 camorama
 udisks
 python3-checkbox
 python3-checkbox-support
 python3-checkbox-ng
 checkbox-ng
 checkbox
 checkbox-ng-service
 checkbox-gui
 checkbox-qt
 chkrootkit
 clamav-freshclam
 clamav
 clamav-daemon
 clamsmtp
 clamtk
 cmake
 epiphany-browser
 gnome-settings-daemon
 libmutter0d
 gir1.2-mutter-3.0
 upower
 gnome-session-bin
 gnome-session
 gnome-shell
 gnome-panel
 metacity
 gnome-session-flashback
 ubuntu-session
 mutter
 libkdecorations4abi2
 libkwineffects1abi5
 libkworkspace4abi2
 kde-window-manager-common
 libkwinglesutils1
 libkwinglutils1abi3
 kde-window-manager
 compiz-core
 compiz-plugins-default
 libcompizconfig0
 compiz-gnome
 compiz
 gdm
 vino
 gnome-media
 gnome-control-center
 gnome-bluetooth
 indicator-datetime
 indicator-power
 pulseaudio
 indicator-sound
 unity-control-center
 indicator-bluetooth
 network-manager-gnome
 compiz-plugins
 erlang-base
 erlang-crypto
 erlang-eunit
 erlang-mnesia
 erlang-runtime-tools
 erlang-asn1
 erlang-public-key
 erlang-ssl
 erlang-inets
 erlang-snmp
 erlang-os-mon
 erlang-syntax-tools
 erlang-webtool
 erlang-tools
 erlang-xmerl
 couchdb-bin
 cryptsetup
 gvfs-backends
 deja-dup-backend-gvfs
 dvdstyler
 evolution-plugins
 flashplugin-installer
 foxtrotgps
 fslview
 fsl-5.0-core
 fsl-core
 fsl
 gconf-defaults-service
 ginkgocadx
 libtotem0
 gir1.2-totem-1.0
 gnome-applets-data
 gnome-applets
 speech-dispatcher
 gnome-orca
 gnome-screensaver
 gnome-session-fallback
 gnome-shell-extensions
 gofigure2
 googleearth-package
 grace
 grub2-common
 grub-pc-bin
 grub-pc
 sane-utils
 gscan2pdf
 gstreamer0.10-gnomevfs:amd64
 gvfs-fuse
 gwyddion-common
 libgwyddion2-0
 gwyddion
 libxine2-x
 libxine2-gnome
 gxine
 gxineplugin
 hud
 hugin-tools
 hugin
 iaxmodem
 imagevis3d
 indicator-session
 inkscape
 jarwrapper
 libkcompactdisc4
 libkcddb4
 libk3b6
 k3b
 libknewstuff2-4
 libkidletime4
 libkprintutils4
 libkutils4
 libkimproxy4
 libkrossui4
 libkunitconversion4
 libqt4-dev-bin
 libqt4-dev
 libphonon-dev
 kdelibs5-dev
 kdenetwork-filesharing
 kernel-package
 kstars
 kwin-style-qtcurve
 language-selector-gnome
 libakonadi-kde4
 libkldap4
 libkresources4
 libkabc4
 libkcalcore4
 libkpimutils4
 libakonadi-contact4
 libwxgtk3.0-dev
 libwxgtk-media3.0-dev
 libalien-wxwidgets-perl
 libapache2-mod-php5
 libatspi2.0-dev
 libatk-bridge2.0-dev:amd64
 libbaloofiles4
 libcanberra-pulse:amd64
 libgconf2-dev
 libgtk-3-dev
 libgcr-3-dev
 libgoa-backend-1.0-dev
 libgoa-1.0-dev
 libgdata-dev
 x11-apps
 xbase-clients
 libgksu2-0
 libgnome2-vfs-perl
 libgnome2-perl
 libgnomevfs2-dev:amd64
 libgnomevfs2-extra:amd64
 libice-dev:amd64
 libsm-dev:amd64
 libgtkglext1-dev
 libkcompactdisc-dev
 libkcddb-dev
 libkephal4abi1
 libkonq-common
 libkonq5abi1
 libkontactinterface4
 libnjb-dev:amd64
 libkscreen1
 libokularcore5
 libowncloudsync0
 libqca2-dev
 libqmobipocket1
 libqscintilla2-11
 libqt4-gui
 libqt4-opengl-dev
 libqt5webkit5-qmlwebkitplugin
 libsnmp-dev
 libstrigiqtdbusclient-dev
 unity-services
 libunity-core-6.0-9
 libvtk-java
 libvtkgdcm2.2
 libvtkgdcm-java
 libvtkgdcm-tools
 libvtkgdcm2-dev
 libwxgtk2.8-dev
 libwxgtk-media2.8-dev
 linux-image-extra-3.16.0-24-generic
 thermald
 linux-image-generic
 linux-generic
 lives
 python-wxgtk2.8
 python-pyface
 python-traitsui
 python-apptools
 tcl-vtk
 python-vtk
 python-envisage
 mayavi2
 mriconvert
 mysql-server
 nautilus-actions
 nautilus-dropbox
 nautilus-sendto
 nvidia-common
 openssh-server
 owncloud-client
 pgadmin3
 pidgin
 pinentry-qt4
 planner
 plymouth-label
 plymouth-theme-kubuntu-logo
 plymouth-theme-kubuntu-text
 plymouth-theme-ubuntu-logo
 plymouth-theme-xubuntu-logo
 plymouth-theme-xubuntu-text
 plymouth-x11
 postfix
 postgresql-common
 postgresql-9.4
 postgresql
 printer-driver-splix
 pulseaudio-esound-compat
 pulseaudio-module-gconf
 pulseaudio-utils
 pulseaudio-module-x11
 python-chaco
 python-pyside.qtgui
 python-pyside.phonon
 python-pyside.qtdeclarative
 python-pyside.qthelp
 python-pyside.qtopengl
 python-pyside.qtscript
 python-pyside.qtsql
 python-pyside.qtsvg
 python-pyside.qttest
 python-pyside.qtuitools
 python-pyside.qtwebkit
 python-pyside
 python-qt4-gl
 python-secretstorage
 unattended-upgrades
 python3-software-properties
 software-properties-common
 python-software-properties
 python-vtkgdcm
 python3-pyqt4
 qapt-batch
 qemu-system-x86
 qemu-kvm
 qemu-system
 qemu
 qemu-user-binfmt
 qt4-default
 qtdeclarative5-accounts-plugin:amd64
 qtdeclarative5-privatewidgets-plugin:amd64
 qutecom
 remmina
 remmina-plugin-rdp
 remmina-plugin-vnc
 rhythmbox-plugin-magnatune
 spamassassin
 sa-compile
 screen
 scribus
 seahorse
 software-properties-gtk
 spacefm
 splix
 tor
 tor-geoipdb
 totem
 totem-mozilla
 totem-plugins
 totem-plugins-extra
 transfig
 transmission-gtk
 ubiquity-frontend-kde
 ubiquity
 ubiquity-frontend-gtk
 xserver-common
 xserver-xorg-core
 unity
 xserver-xorg-video-r128
 xserver-xorg-video-mach64
 xserver-xorg-video-radeon
 xserver-xorg-video-ati
 xserver-xorg-video-cirrus
 xserver-xorg-video-fbdev
 xserver-xorg-video-intel
 xserver-xorg-video-mga
 xserver-xorg-video-modesetting
 xserver-xorg-video-neomagic
 xserver-xorg-video-nouveau
 xserver-xorg-video-openchrome
 xserver-xorg-video-savage
 xserver-xorg-video-siliconmotion
 xserver-xorg-video-sisusb
 xserver-xorg-video-tdfx
 xserver-xorg-video-trident
 xserver-xorg-video-vesa
 xserver-xorg-video-vmware
 xserver-xorg-video-all
 xserver-xorg-video-s3
 xserver-xorg-video-qxl
 xserver-xorg-input-evdev
 xserver-xorg-input-mouse
 xserver-xorg-input-vmmouse
 xserver-xorg-input-synaptics
 xserver-xorg-input-wacom
 xserver-xorg-input-all
 xserver-xorg-input-mutouch
 xserver-xorg-input-multitouch
 xserver-xorg
 xorg
 ubuntu-desktop
 unity-2d-common
 unity-2d-shell
 unity-control-center-signon
 unity-tweak-tool
 unity-webapps-qml
 usb-creator-common
 usb-creator-gtk
 vlc
 vlc-plugin-pulse
 vym
 webapp-container
 xaralx
 xaralx-svg
 xchat-common
 xchat
 xfce4-power-manager
 xfce4-power-manager-plugins
 xine-ui
 xserver-xephyr
 xubuntu-default-settings
 akonadi-server
 appmenu-qt5
 brltty-x11
 compiz-plugins-extra
 compiz-plugins-main
 compizconfig-backend-gconf
 python-compizconfig
 compizconfig-settings-manager
 evolution-indicator
 freecad
 friends-facebook
 friends-identica
 friends-twitter
 grub2
 indicator-printers
 kde-style-qtcurve
 kpartx
 kpartx-boot
 libwebkitgtk-3.0-dev
 lsb-core
 okular-extra-backends
 pulseaudio-module-bluetooth
 python-qscintilla2
 vdr
 wine1.6-amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have disabled all 3rd party repositories and PPAs and re-run the commands. I have tried 
```
apt-get install -f
```
and
```
dpkg --configure -a
```
all with the same results. 

The SoftwareUpdater gives the same results. I have 617 incompletely installed or removed packages it seems. I've tried installing/configuring a few one at a time to no avail. 
Any ideas? I've googled my fingers raw! Luckily my system seems to work fine and is running 14.10 but there will come a time that I need to upgrade and that concerns me.
Thanks every/anyone!

---

### Post by ubuntubrian on 2014-11-04
I finally solved this. I tried using dpkg to configure any of the packages that were a problem and ultimately, after only 3 tries, found that the issue was package sysv-rc. I found that it is the "unable to migrate to dependency based boot sequencing" error that is thrown when trying to configure sysv-rc. I followed the suggestions here[HTML]http://askubuntu.com/questions/543857/getting-error-with-dpkg[/HTML]. I also had the virtuoso-nepomuk script problem when I checked the log file so I deleted it and the upgrade completed without errors!
Marked Solved.

---

### Post by herdwick on 2015-02-22
+1 for moving the virtuoso-nepomuk script out of  /etc/init.d  and the borked upgrade fixed itself.

---

