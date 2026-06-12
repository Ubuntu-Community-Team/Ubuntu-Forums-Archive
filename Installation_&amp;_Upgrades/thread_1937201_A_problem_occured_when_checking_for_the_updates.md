---
title: "A problem occured when checking for the updates"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by Kkatt on 2012-03-07
Hi,

I am using Ubuntu 10.04. I can not install or update anything. On my task bar there is an arrow with orange background saying "A problem occured when checking for the updates". Everything, except for updating and installing, seams to work normally.

The problem appeared when I was changing my default version of Python, by installing from source and changing symbolic link, from 2.6 which is default for Ubuntu 10.4 to 3.1, and then to 2.7.

I have read several  similar threads on the forums but none of the advice there seams to resolve my problem.

sudo apt-get -f install 

returns 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  checkbox
The following packages will be upgraded:
  checkbox
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
27 not fully installed or removed.
Need to get 0B/242kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 342983 files and directories currently installed.)
Preparing to replace python-problem-report 1.13.3-0ubuntu2 (using .../python-problem-report_1.13.3-0ubuntu2_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error processing /var/cache/apt/archives/python-problem-report_1.13.3-0ubuntu2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace checkbox 0.9.1 (using .../checkbox_0.9.2_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error processing /var/cache/apt/archives/checkbox_0.9.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-problem-report_1.13.3-0ubuntu2_all.deb
 /var/cache/apt/archives/checkbox_0.9.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I have tried removing the offending file

python-problem-report_1.13.3-0ubuntu2_all.deb

but it reappeared.

sudo aptitude update && sudo aptitude safe-upgrade 

returned 

```

Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                              
Hit http://ppa.launchpad.net lucid Release.gpg                                                        
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US          
Hit http://archive.ubuntu.com lucid Release.gpg                                  
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release                                                         
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US         
Hit http://archive.ubuntu.com lucid-updates Release.gpg                          
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US       
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US   
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US 
Hit http://archive.ubuntu.com lucid-security Release.gpg                         
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US      
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US               
Hit http://archive.ubuntu.com lucid-backports Release.gpg                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US              
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US                    
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US                       
Hit http://archive.canonical.com lucid/partner Packages                                                  
Hit http://ppa.launchpad.net lucid/main Packages                                                         
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US                
Hit http://archive.ubuntu.com lucid Release                               
Hit http://archive.ubuntu.com lucid-updates Release                       
Hit http://archive.ubuntu.com lucid-security Release                      
Hit http://archive.ubuntu.com lucid-backports Release                                          
Hit http://archive.ubuntu.com lucid/main Packages                                              
Hit http://archive.ubuntu.com lucid/restricted Packages                   
Hit http://archive.ubuntu.com lucid/main Sources                          
Hit http://archive.ubuntu.com lucid/restricted Sources                    
Hit http://archive.ubuntu.com lucid/universe Packages                     
Hit http://archive.ubuntu.com lucid/universe Sources                      
Hit http://archive.ubuntu.com lucid/multiverse Packages                   
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages           
Hit http://archive.ubuntu.com lucid-updates/main Sources                  
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/universe Sources              
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages           
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources            
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/restricted Sources           
Hit http://archive.ubuntu.com lucid-security/universe Packages            
Hit http://archive.ubuntu.com lucid-security/universe Sources             
Hit http://archive.ubuntu.com lucid-security/multiverse Packages          
Hit http://archive.ubuntu.com lucid-security/multiverse Sources           
Hit http://archive.ubuntu.com lucid-backports/restricted Packages         
Hit http://archive.ubuntu.com lucid-backports/main Packages               
Hit http://archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://archive.ubuntu.com lucid-backports/universe Packages
Hit http://linux.dropbox.com lucid Release.gpg
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US
Hit http://linux.dropbox.com lucid Release
Hit http://linux.dropbox.com lucid/main Packages
Reading package lists... Done

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
Resolving dependencies...
The following NEW packages will be installed:
  linux-headers-2.6.32-39{a} linux-headers-2.6.32-39-generic{a} linux-image-2.6.32-39-generic{a} 
The following packages will be REMOVED:
  linux-headers-2.6.32-38{u} linux-headers-2.6.32-38-generic{u} 
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin checkbox chromium-browser chromium-browser-l10n 
  chromium-codecs-ffmpeg consolekit libck-connector0 libpam-ck-connector linux-generic 
  linux-headers-generic linux-image-generic linux-libc-dev python-problem-report 
The following partially installed packages will be configured:
  apport apport-gtk checkbox-gtk linux-image-2.6.32-38-generic packagekit-backend-apt python-apport 
  python-apt python-desktopcouch python-desktopcouch-records python-gmenu python-pysqlite2 
  python-software-properties software-center software-properties-gtk software-properties-kde 
  unattended-upgrades update-manager update-manager-core update-manager-kde update-notifier 
  update-notifier-common 
14 packages upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
Need to get 70.8MB/71.0MB of archives. After unpacking 99.4MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.canonical.com/ubuntu/ lucid/partner adobe-flash-properties-gtk 11.1.102.63-0lucid1 [130kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-39 2.6.32-39.86 [9,940kB]
Get:3 http://archive.canonical.com/ubuntu/ lucid/partner adobe-flashplugin 11.1.102.63-0lucid1 [6,432kB]
Get:4 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-39-generic 2.6.32-39.86 [795kB]   
Get:5 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-generic 2.6.32.39.46 [4,804B]            
Get:6 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-39-generic 2.6.32-39.86 [31.6MB]    
Get:7 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-generic 2.6.32.39.46 [4,804B]                    
Get:8 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-generic 2.6.32.39.46 [4,814B]              
Get:9 http://archive.ubuntu.com/ubuntu/ lucid-updates/universe chromium-browser-l10n 17.0.963.65~r124586-0ubuntu0.10.04.1 [2,026kB]
Get:10 http://archive.ubuntu.com/ubuntu/ lucid-updates/universe chromium-codecs-ffmpeg 17.0.963.65~r124586-0ubuntu0.10.04.1 [386kB]
Get:11 http://archive.ubuntu.com/ubuntu/ lucid-updates/universe chromium-browser 17.0.963.65~r124586-0ubuntu0.10.04.1 [18.5MB]
Get:12 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libck-connector0 0.4.1-3ubuntu3 [57.1kB]              
Get:13 http://archive.ubuntu.com/ubuntu/ lucid-updates/main consolekit 0.4.1-3ubuntu3 [97.6kB]                    
Get:14 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libpam-ck-connector 0.4.1-3ubuntu3 [8,042B]           
Get:15 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-libc-dev 2.6.32-39.86 [836kB]                   
Fetched 70.8MB in 48s (1,465kB/s)                                                                                 
Preconfiguring packages ...
Selecting previously deselected package linux-headers-2.6.32-39.
(Reading database ... 342983 files and directories currently installed.)
Unpacking linux-headers-2.6.32-39 (from .../linux-headers-2.6.32-39_2.6.32-39.86_all.deb) ...
Selecting previously deselected package linux-headers-2.6.32-39-generic.
Unpacking linux-headers-2.6.32-39-generic (from .../linux-headers-2.6.32-39-generic_2.6.32-39.86_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.32.38.44 (using .../linux-headers-generic_2.6.32.39.46_i386.deb) ...
Unpacking replacement linux-headers-generic ...
(Reading database ... 361410 files and directories currently installed.)
Removing linux-headers-2.6.32-38-generic ...
(Reading database ... 354682 files and directories currently installed.)
Preparing to replace python-problem-report 1.13.3-0ubuntu2 (using .../python-problem-report_1.13.3-0ubuntu2.1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error processing /var/cache/apt/archives/python-problem-report_1.13.3-0ubuntu2.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace checkbox 0.9.1 (using .../checkbox_0.9.2_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error processing /var/cache/apt/archives/checkbox_0.9.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Selecting previously deselected package linux-image-2.6.32-39-generic.
Unpacking linux-image-2.6.32-39-generic (from .../linux-image-2.6.32-39-generic_2.6.32-39.86_i386.deb) ...
Done.
Preparing to replace linux-generic 2.6.32.38.44 (using .../linux-generic_2.6.32.39.46_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.32.38.44 (using .../linux-image-generic_2.6.32.39.46_i386.deb) ...
Unpacking replacement linux-image-generic ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-problem-report_1.13.3-0ubuntu2.1_all.deb
 /var/cache/apt/archives/checkbox_0.9.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.32-38-generic (2.6.32-38.83) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-38-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-39-generic
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda3
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-38-generic /boot/vmlinuz-2.6.32-38-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 3, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection, NoDatadirError
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 23, in <module>
    import subprocess
  File "/usr/lib/python2.6/subprocess.py", line 427, in <module>
    import select
ImportError: No module named select
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-38-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-gmenu (2.30.0-0ubuntu4) ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Traceback (most recent call last):
  File "/usr/share/gnome-menus/update-gnome-menus-cache", line 23, in <module>
    import locale
  File "/usr/lib/python2.6/locale.py", line 15, in <module>
    import functools
  File "/usr/lib/python2.6/functools.py", line 10, in <module>
    from _functools import partial, reduce
ImportError: No module named _functools
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 13, in <module>
    from subprocess import call
  File "/usr/lib/python2.6/subprocess.py", line 427, in <module>
    import select
ImportError: No module named select
dpkg: error processing python-gmenu (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: error processing checkbox (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up linux-image-2.6.32-39-generic (2.6.32-39.86) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-39-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-39-generic
Found initrd image: /boot/initrd.img-2.6.32-39-generic
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda3
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-39-generic /boot/vmlinuz-2.6.32-39-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 3, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection, NoDatadirError
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 23, in <module>
    import subprocess
  File "/usr/lib/python2.6/subprocess.py", line 427, in <module>
    import select
ImportError: No module named select
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-39-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of checkbox-gtk:
 checkbox-gtk depends on checkbox (= 0.9.2); however:
  Version of checkbox on system is 0.9.1.
dpkg: error processing checkbox-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing python-problem-report (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-39-generic; however:
  Package linux-image-2.6.32-39-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-39 (2.6.32-39.86) ...
Setting up linux-headers-2.6.32-39-generic (2.6.32-39.86) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-39-generic /boot/vmlinuz-2.6.32-39-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 3, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection, NoDatadirError
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 23, in <module>
    import subprocess
  File "/usr/lib/python2.6/subprocess.py", line 427, in <module>
    import select
ImportError: No module named select
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-39-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.39.46); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up python-apt (0.7.94.2ubuntu6.4) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error processing python-apt (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-39-generic; however:
  Package linux-headers-2.6.32-39-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up python-desktopcouch (0.6.4-0ubuntu3.3) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error processing python-desktopcouch (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-desktopcouch-records:
 python-desktopcouch-records depends on python-desktopcouch; however:
  Package python-desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch-records (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python-apt (>= 0.6.12); however:
  Package python-apt is not configured yet.
dpkg: error processing update-notifier-common (--configure):
 dependency problems - leaving unconfigured
Setting up python-pysqlite2 (2.5.5-3) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import glob, logging, os, re, string, sys, time, cStringIO
  File "/usr/lib/python2.6/logging/__init__.py", line 34, in <module>
    import sys, os, types, time, string, cStringIO, traceback
ImportError: No module named time
dpkg: error processing python-pysqlite2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-software-properties:
 python-software-properties depends on python-apt (>= 0.6.20ubuntu16); however:
  Package python-apt is not configured yet.
dpkg: error processing python-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-apt; however:
  Package python-apt is not configured yet.
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on python-apt (>= 0.7.13.4ubuntu3); however:
  Package python-apt is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python-apt (>= 0.7.13.4ubuntu3); however:
  Package python-apt is not configured yet.
dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of packagekit-backend-apt:
 packagekit-backend-apt depends on python-apt (>= 0.7.13.2); however:
  Package python-apt is not configured yet.
 packagekit-backend-apt depends on update-manager-core; however:
  Package update-manager-core is not configured yet.
 packagekit-backend-apt depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
dpkg: error processing packagekit-backend-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-kde:
 software-properties-kde depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
dpkg: error processing software-properties-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 0.99.3ubuntu0.1); however:
  Package update-notifier-common is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on python-apt (>= 0.7.9); however:
  Package python-apt is not configured yet.
dpkg: error processing unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-kde:
 update-manager-kde depends on update-manager-core; however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.134.12.1); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-38-generic
 python-gmenu
 checkbox
 linux-image-2.6.32-39-generic
 checkbox-gtk
 python-problem-report
 linux-image-generic
 linux-headers-2.6.32-39-generic
 linux-generic
 python-apt
 linux-headers-generic
 python-desktopcouch
 python-desktopcouch-records
 update-notifier-common
 python-pysqlite2
 python-software-properties
 python-apport
 software-center
 update-manager-core
 packagekit-backend-apt
 software-properties-kde
 update-notifier
 unattended-upgrades
 update-manager-kde
 update-manager
 apport
 software-properties-gtk
 apport-gtk
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Current status: 11 updates [-3].

```Thanks for any suggestions on this.

---

