---
title: "Problem installing Virtual Box in Gutsy"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by subpreza on 2008-02-28
Hello


    I tried to install Virtual Box in my laptop. Everything was fine. I specified the RAM, the hard disk space evrything. When i tried to open it a message is coming up. 


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 I had a look in many forums about this problem. Actually it says that i'm missing the /lib/modules/2.6.22-14-generic/misc/vboxdrv.ko.  I also used the command sudo /etc/init.d/vboxdrv start and the output was::::   * Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko): Invalid argument

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

The thing is that i have to work some windows programs that's why i need this .Does anyone has any ideas about it???

Thank you

---

### Post by pytheas22 on 2008-02-28
To run Virtual Box you need to added to the vboxusers group.  You can do this using the Users and Groups utility.  Or for a less sound solution, try running the program as root (open a terminal and type "sudo VirtualBox").  I'm not sure if this is your problem but it's worth checking.

---

