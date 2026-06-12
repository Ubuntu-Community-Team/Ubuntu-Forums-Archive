---
title: "What Does This Error Message Mean?"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by Tim_Olaguna on 2010-03-22
I'm running under Ubuntu 9.10.  I received the following error message while trying to update my system via the Update Manager:

E: /var/cache/apt/archives/xserver-xorg-core_2%3a1.6.4-2ubuntu4.2_i386.deb: unable to create `/usr/lib/nvidia/libglx.so.xserver-xorg-core.dpkg-new' (while processing `./usr/lib/xorg/modules/extensions/libglx.so')

What does the message mean?  What steps should I take from here in order to correct or resolve the situation which causes the error?

---

### Post by lemming465 on 2010-03-24
There are a zillion possiblities for what could be going wrong, and we don't have enough information to distinguish them all yet.  I'll assume you have one big root partition.  The ".deb" file is the actual package it's trying to install or update.  "unable to create" means trying to write a file failed for some as yet unknown reason.  One possibility is failure to use sudo, e.g. if you ran "update-manager" at a terminal prompt rather than "sudo update-manager".

1. Check that you are mounted read-write still.  *mount | grep ' / '* should produce something like:> /dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)where the key thing is that the options in parenthesis start of "rw" meaning read-write, not "ro" meaning read-only.  It's OK if the device partition is different, e.g. /dev/sda1, or the file system type is different, e.g. ext3.

2. Check that you aren't out of disk space.  *df -m /* should show a use percentage below 90% and an available space of at least 30 MB, ideally more than 2000 MB.

3. Check that you aren't out of inodes.   *df -i /* should show a use percentage much lower than 90% and a free inode count much greater than 100,000.

Assuming, as is likely, that those are all OK, it's time to try some package cache maintenance:```
sudo -i
aptitude clean
aptitude update
aptitude full-upgrade
```

Sometimes there are download issues related to corrupted mirror sites or bugs in packages; often waiting a day and trying again will correct these.

---

### Post by Tim_Olaguna on 2010-03-25
I’ve decided this is no longer a problem I need to worry about and probably one I created for myself.  Here’s the background:
 
I use my PC mainly as a Windows machine.  I can dual boot into either Windows or Ubuntu but keep all of my serious or important documents on partitions which are equally accessible to either operating system.  I boot into the Ubuntu side when I want to experiment with Linux and learn new things.
 
My PC came with an nVidia GeForce 7350 graphics card.  I never could get my graphics card to work automatically, easily, or well under Ubuntu 8.04 or 8.10.  I just put up with the rather blah vesa generic output.  
 
When Ubuntu 9.04 came along I redoubled my efforts to get my nVidia card to work with it.  I still could not get the card to be recognized using Envy or any of the other tools that were supposed to work easy with nVidia.  But I was finally able to manually install and implement the nVidia drivers using directions I found in a Ubuntu Forums Tutorial (which I have since lost, naturally).  My monitor now produced excellent output.  I backed up that installation setting on a partition set aside for that purpose.
 
When 9.10 came along I wiped out my Ubuntu partition and performed a clean installation.  It was my understanding that 9.10 would provide “better” support for nVidia drivers.  Well, it did not for me.  I still could only get the rather blah vesa generic output.  Until I restored my previous settings from my 9.04 backup.  Then all was well and beautiful again.
 
Now I think it’s my backed up settings which are causing problems with the 9.10 Update Manager.  The latter must be expecting key files to be in places where my prior manual installation has not put them.  But since my backed up settings work I’m keeping them as they are.  At least until a non-beta production-ready version of Ubuntu 10.04 comes out.  
 
From my understanding 10.04 is supposed to include nVidia drivers which work automatically upon installation of Ubuntu.  So I’ll be doing another clean install of Ubuntu at that time.  In the meantime I’ll just ignore any more Update Manager update errors I receive which seem to be related to nVidia or xorg issues.  While continuing to maintain a backed up copy of the manually installed settings which do work.

---

### Post by Tim_Olaguna on 2010-03-25
Thanks so much for trying to help me, lemming465.  I really appreciate your time and knowledgeable suggestions.

> **lemming465 said:**
> ```
sudo -i
aptitude clean
aptitude update
aptitude full-upgrade
```


I did try your last four code suggestions in a terminal.  The first 3 ran fine as expected.  But the last one produced:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  xulrunner-1.9.1 
The following partially installed packages will be configured:
  metacity packagekit-backend-apt 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,273kB of archives. After unpacking 2,802kB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main xulrunner-1.9.1 1.9.1.10~hg20100324r26859+nobinonly-0ubuntu1~umd1~karmic [9,273kB]
Fetched 9,273kB in 42s (220kB/s)                                                                                                                  
(Reading database ... 304484 files and directories currently installed.)
Preparing to replace xulrunner-1.9.1 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1 (using .../xulrunner-1.9.1_1.9.1.10~hg20100324r26859+nobinonly-0ubuntu1~umd1~karmic_i386.deb) ...
Removing obsolete conffile /etc/gre.d/1.9.1.8.system.conf ...
Unpacking replacement xulrunner-1.9.1 ...
Setting up metacity (1:2.28.0-0ubuntu2) ...
update-alternatives: error: alternative link /usr/bin/x-window-manager is already managed by x-window-manager.before_restore_2010-02-24_13.01.07.511503.
dpkg: error processing metacity (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up packagekit-backend-apt (0.4.9+20090825-0ubuntu6) ...
/var/lib/dpkg/info/packagekit-backend-apt.postinst: 6: update-packagekit-app-data: not found
file does not exist: /usr/share/PackageKit/helpers/apt/aptBackend.py
file does not exist: /usr/lib/packagekit-backend/libpk_backend_apt.so
pycentral: pycentral pkginstall: error byte-compiling files (2)
pycentral pkginstall: error byte-compiling files (2)
dpkg: error processing packagekit-backend-apt (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up xulrunner-1.9.1 (1.9.1.10~hg20100324r26859+nobinonly-0ubuntu1~umd1~karmic) ...
update-alternatives: using /usr/bin/xulrunner-1.9.1 to provide /usr/bin/xulrunner (xulrunner) in auto mode.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 metacity
 packagekit-backend-apt
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up metacity (1:2.28.0-0ubuntu2) ...
update-alternatives: error: alternative link /usr/bin/x-window-manager is already managed by x-window-manager.before_restore_2010-02-24_13.01.07.511503.
dpkg: error processing metacity (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up packagekit-backend-apt (0.4.9+20090825-0ubuntu6) ...
/var/lib/dpkg/info/packagekit-backend-apt.postinst: 6: update-packagekit-app-data: not found
file does not exist: /usr/share/PackageKit/helpers/apt/aptBackend.py
file does not exist: /usr/lib/packagekit-backend/libpk_backend_apt.so
pycentral: pycentral pkginstall: error byte-compiling files (2)
pycentral pkginstall: error byte-compiling files (2)
dpkg: error processing packagekit-backend-apt (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 metacity
 packagekit-backend-apt
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

Current status: 0 updates [-1].


It's pretty clear I have a seriously damaged install.  Time to wipe and do something else.

---

