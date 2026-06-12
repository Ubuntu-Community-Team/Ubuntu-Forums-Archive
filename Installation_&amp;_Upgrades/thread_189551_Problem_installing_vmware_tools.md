---
title: "Problem installing vmware tools"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by eoinlane on 2006-06-05
FIrst let me say congats on a polished looking distro I am v impressed.

To try it out I have created a vm image using vmmare.

However installing the vmware tools has given me some problems.

First is was looking for make, which I installed,

Second it was looking for gcc, which I installed.

But now it is looking for location of the C header files file that match my kernel.

Here I am at a bit of a loss. Maybe there is a howto that you point me to make this process a bit less painful.

Best wishes,

Eoin

---

### Post by bswilson on 2006-06-05
The same thing happened to me.  I finally figured it out, so I hope you can learn from my experience.  The challenge is that your linux kernel headers and compiler are in places that VMware doesn't expect, thus the problem.  You also may need a few additional packages.  Here's what you do:

**1. Prepare your system with the latest packages**
First, let's update your machine and ensure you have a few needed packages.  Note that for that last command, ensure you put in the numbers that match your running kernel.  Run **uname -a** to get that information.
```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install gcc-3.4
sudo apt-get install linux-headers-2.6.15-23-386
```

**2. Create links so your system can find your compiler.**
```
CC=gcc-3.4
export CC
```
	
That should be it!  Now when you run **vmware-install.pl**, you should have all the answers you need.  During the installation, you'll be promted to point the installer to the linux headers of your running kernel.  Instead of the default value of **/usr/src/linux/include**, you'll enter **/usr/src/linux-headers-2.6.15-23-386/include** (or whatever your kernel is).  OK?

---

### Post by bigken on 2006-06-05
the guest OS must be running 1st to install the tools :wink:

Take a look here [http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware")

---

### Post by mannheim on 2006-06-05
Do you need the tools? Once you have got the guest OS running, installing the tools in the guest OS is supposed to give you drivers which deliver better performance. But my experience is that the dapper installation in the gues OS already includes the vmware driver for xorg (check out /etc/X11/xorg.conf in the guest); and I've never felt I needed the faster network drivers, because networking already seemed pretty quick in the guest. 

If you are sharing files between the guest and the host, then faster networking would make a difference. But if you are just checking out dapper and browsing around, I don't see that the tools are useful.

---

### Post by bigken on 2006-06-05
[quote=mannheim]Do you need the tools? Once you have got the guest OS running, installing the tools in the guest OS is supposed to give you drivers which deliver better performance. But my experience is that the dapper installation in the gues OS already includes the vmware driver for xorg (check out /etc/X11/xorg.conf in the guest); and I've never felt I needed the faster network drivers, because networking already seemed pretty quick in the guest. 

If you are sharing files between the guest and the host, then faster networking would make a difference. But if you are just checking out dapper and browsing around, I don't see that the tools are useful.[/quote]

sorry but I disagree it also make things look and run much smoother

---

### Post by mannheim on 2006-06-06
[QUOTE=bigken]sorry but I disagree it also make things look and run much smoother[/QUOTE]

Well, I may be wrong. I know the tools make a **big** difference in a Windows guest OS. But running the vmware tools installer in the **dapper** guest (running under VMWare Workstation) seems to do only this:
[LIST=3]
[*]Installs a kernel module, vmhgfs, for file sharing between host and guest.
[*]Installs a kernel module, vmxnet, which is a faster network driver.
[*] Installs a startup script.
[/LIST]
The startup script does stuff like:
[LIST=1]
[*]Loads the above kernel modules.
[*]Starts a daemon vmware-guestd, which allows you to sync time between host and guest.
[*]Enables DMA on all drives, by running hdparm.
[/LIST]

Item (3) you can do yourself with hdparm; but this will not improve virtual hard disk performance, because the dapper installer enables DMA on the guest's virtual hard disk anyway. It may speed up the cdrom. The vmware tools installer also tries to set up an xorg driver, and fails (perhaps because this is xorg 7.0). However, the vmware xorg driver is already installed in dapper.

There is also a kernel module called vmmemctl, which is **not** installed in the guest by the tools installer. I think this module is only used with the non-free VMware "ESX Server", for dynamically rallocating memory between virtual machines. Maybe it is used in the (free) "Server" version also?

---

### Post by bbruecker on 2006-06-07
Im new to linux and I also try to install Ubuntu 6.06 at vmware. 

> ...What is the directory that contains the init scripts?
[/etc/init.d]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware-tools.

Execution aborted. 
What's wrong?

Regard's Benjamin

---

### Post by jon_gunnar on 2006-06-07
[QUOTE=bbruecker]Im new to linux and I also try to install Ubuntu 6.06 at vmware. 

 
What's wrong?

Regard's Benjamin[/QUOTE]

You must run as sudo

---

### Post by bbruecker on 2006-06-07
[quote=jon_gunnar]You must run as sudo[/quote]

Hi Jon, I run the script with sudo. (It is impossible to start the script without sudo.) Regard's, Benjamin

---

### Post by rcarring on 2006-06-07
If you install the linux-headers for both the main group of headers and i386 (not i686) then vmware-tools will find the files.

What I did was install:

gcc
make
linux-headers

And that was enought for vmware to find everything. I did not need to tell it where to find the compiler either. Maybe I am just lucky =D

---

### Post by Tom Fury on 2006-06-07
Thanks rcarring.  Installed those and the vmware tools installed fine.

---

### Post by bbruecker on 2006-06-08
It's me again. I'm sorry but there must be another hint installing the vmware tools.
 
'uname -a' shows this: > Linux vw6 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux  
So I tried this on my freshly installed Ubuntu:
 ```
sudo apt-get update
 sudo apt-get install build-essential
 sudo apt-get install gcc-3.4
 sudo apt-get install linux-headers-2.6.15-23-386
 CC=gcc-3.4
 export CC
 Linux vw6 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
```  
This yields to the same error:> Creating a new installer database using the tar3 format.
 Installing the content of the package.
 In which directory do you want to install the binary files?
 [/usr/bin]
 What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
 [/etc]
 What is the directory that contains the init scripts?
 [/etc/init.d]
 Unable to copy the source file ./installer/services.sh to the destination file
 /etc/init.d/vmware-tools.
 Execution aborted.  

 I'm new to linux, but I only know two possible reasons for a copy command to fail: 1) insufficient rights -- can't be, I run the installer with sudo, and sudo gives root privileges to the command (right?) or 2) a process or a service looks data.
 
 Can somebody help me again please!
 Regards Benjamin

---

