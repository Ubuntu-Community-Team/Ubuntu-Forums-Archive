---
title: "nvidia drivers or repositories problem"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by Mis_Uszatek on 2006-11-04
Hello everyone

I have a problem with nvidia-glx updates.
I was notified that there are some software updates for dapper.
Ok, I installed them. Reboot. X-Org doesn't work anymore.
Black screen and info :
> X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux bobex 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  4 12:31:46 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) NVIDIA(0): Version mismatch detected between the NVIDIA X driver and the
(EE) NVIDIA(0):     NVIDIA GLX module.  X driver version: 1.0-8762; GLX module
(EE) NVIDIA(0):     version: 1.0-8776.  Please try reinstalling the NVIDIA
(EE) NVIDIA(0):     driver.
Error: API mismatch: the NVIDIA kernel module has the version 1.0-8776, but
this X module has the version 1.0-8762.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.


Most interesting is :
(EE) NVIDIA(0): Version mismatch detected between the NVIDIA X driver and the
(EE) NVIDIA(0): NVIDIA GLX module. X driver version: 1.0-8762; GLX module
(EE) NVIDIA(0): version: 1.0-8776. Please try reinstalling the NVIDIA
(EE) NVIDIA(0): driver.

After some time, I was able to bring back previous version of nvidia-xgl(downgrade it).
But I had also to downgrade my kernel-version.

So: when I choose and install version :1.0.8776+2.6.15.12-1(dapper-security) I have got a problem
But in case of : 1.0.8762+2.6.15.11-1(dapper) problem doesn't exist.

My /etc/apt/sources.list is:
> # 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060504)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060504)]/ dapper main restricted

deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

#dodawane dla mplayer
deb [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) dapper main universe multiverse restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) dapper main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://www.kadu.net/download/binary/ubuntu/repo](http://www.kadu.net/download/binary/ubuntu/repo) dapper main

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

#for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


Could anybody explain me where is the problem.
As far as I understand, newer version of nvidia-glx requires never version of driver/module. Is the problem in repositories somewhere? Or in my sources-list?

And why the hell I have to use kernel 2.6.15-23-k7 instead of kernel 2.6.15-27-k7??

I install my nvidia driver by method 1 from this article :

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Thx for help.

---

### Post by rws on 2006-11-04
I got the same issue one hour ago.

---

### Post by beemer on 2006-11-04
Same issue here as well - I've had to revert to the "nv" drivers to get my desktop back.

Beemer

---

### Post by theplatypus on 2006-11-04
I had the same problem. Using Synaptic go to the package tab then force version and downgrade to the old Nvida-GLX to fix the problem.

---

### Post by Mis_Uszatek on 2007-07-02
Does anyone know how to solve this?

---

### Post by rws on 2007-07-02
Installed a proprietary drivers from nvidia.com

---

### Post by Mis_Uszatek on 2007-07-03
Do I have to really install a driver from nvidia.com? Are you sure?
I have tried that but it is not working. Result is the same.

And as far as I know installing a driver from nvidia com and from repositories is the same. Am I right?

But I am not right:
What for are repositories? I always thought that I am able to install proper driver through apt-get.
I have done that(install nvidia drivers) before (in case of 8762) and everything works.

So I have to update nvidia glx driver through apt-get, and install a proper driver from nvidia?

---

