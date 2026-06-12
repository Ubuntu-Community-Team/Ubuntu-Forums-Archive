---
title: "dpkg catch22 cannot install/remove anything"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by steve.horsley on 2007-01-17
I seem to have  a dependency catch22. Installing VirtualBox failed while trying to install it by clicking a downloaded .deb.file. Now I cannot install or remove any packages at all.

This is the state of the package:
> root@JamesPC:/home/james# dpkg -l virtualbox
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rFR virtualbox     1.3.2-20070114 InnoTek VirtualBox



I cannot install the package because it won't compile:
> root@JamesPC:/home/james/Desktop# dpkg -i VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb
Selecting previously deselected package virtualbox.
(Reading database ... 94611 files and directories currently installed.)
Preparing to replace virtualbox 1.3.2-20070114_Ubuntu_edgy (using VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb) ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb (--install):
 subprocess new pre-removal script returned error exit status 1
-e 
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb


I cannot remove virtualbox because it needs reinstalling:
> james@JamesPC:~$ sudo dpkg -r --force-remove-reinstreq virtualbox
Password:
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 94610 files and directories currently installed.)
Removing virtualbox ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing virtualbox (--remove):
 subprocess pre-removal script returned error exit status 1
-e 
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox


I guess maybe it won't compile because it needs the kernel headers and build-essential packeges, but I can't install them because I must install virtualbox first:
> root@JamesPC:/home/james/Desktop# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.


The problem here seems to be that removing the damn package involved finishing the install. How can I break this circle? The obvious way is to just forget that I ever tried to install it, but I can't figure out how.

---

### Post by ipguru99 on 2007-01-17
Same spot.  I have run into this in  a couple of situations, but this is crazy!  Everything I can normally do isn't working to get rid of it.

When I was trying it on a Dapper box, I was able to use APT to remove it ( I thought it was funny that dpkg wouldn't do it).. but I can't get anywhere.

In the log, I realized that just the headers are not enough.. I also need gcc.. and all of those dependencies... so I am stuck as well.

Hopefully someone knows the trick!

---

### Post by ipguru99 on 2007-01-17
how to remove it

I got this from:
[http://virtualbox.org/wiki/User_FAQ](http://virtualbox.org/wiki/User_FAQ)

They go into the problems people are having with 

Error inserting vboxdrv

Kernel module not found

VirtualBox kernel driver not accessible, permission problem

I had all three.  Should be mentioned here that build-essential,linux-header-2.17.10-386 (or whatever) gcc and the like need to be installed before you try to install... or you will end up like me :)

---

### Post by steve.horsley on 2007-01-18
> I got this from:
[http://virtualbox.org/wiki/User_FAQ](http://virtualbox.org/wiki/User_FAQ)
Excellent link, thanks. I will try it tonight. I think that having uninstalled the package, I should be able to install build-essential and then just reinstall the VirtualBox .deb without problems. I know it can be that easy - the first box I put it on happened to have the compiler etc. on it already so installing the VirtualBox .deb was just a case of double-clicking the file.

---

### Post by steve.horsley on 2007-01-22
Took longer than I thought, but I finally got round to it. The link worked thanks, and I managed to remove the package finally.

It still won't install, and it turns out that the compilation error is that uname -r returns the string 2.6.17-10-386 so this is where the install script looks for the sources, whereas the sources are actually under 2.6.17-10-generic. I think this is because the box has been upgraded from one of the "flight" CDs rather than installed fresh from the Edgy release CD. I'll look at doing a fresh install to clear out this and any other "funnies".

---

