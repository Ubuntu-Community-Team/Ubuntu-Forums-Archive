---
title: "Compile RAID Driver - 3Ware 9750"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by jtwood on 2011-07-28
I have several servers running 3ware 9750 raid controller cards.  The 9750 does not have a driver built into the linux kernel and must be manually added during installation.  This hasn't been a problem as I had a driver compiled for the kernel versions I was using.

There isn't a driver available precompiled for 10.04.3.  I would like to compile one from the source code I downloaded from the manufacturer, but I am not sure where to start.   I've looked for some sort of walkthrough or directions, but I haven't had any luck.  I've compiled and installed software from source, but I have a feeling that drivers are probably a bit more complicated, especially since I will need to compile the driver on a system that does not have the same kernel version.

Any help is much appreciated.

Thanks in advance!

---

### Post by steve11911 on 2011-07-29
In the second panel of the page linked below...

[http://communities.vmware.com/message/1728593](http://communities.vmware.com/message/1728593)

---

### Post by jtwood on 2011-08-01
I guess I wasn't completely clear:

I have a 9750 installed in my server-

It is the controller card for the OS drives.

I would like to compile the driver for kernel versions that the driver has not already been compiled for, such as the kernel for 10.04.3 server.

The problem isn't getting the machine to boot say on 10.04.1 as I can download the driver, precompiled for that kernel.  I would like to be able to update my server to 10.04.3.

If I do that now, without applying a driver compiled for that kernel, I'll end up with a cute little case of kernel panic during boot, as the harddrive for the os will not be found because the 9750 driver won't be loaded.

Besides, I can't imagine its the worst thing in the world to know how to compile a driver module for a specific kernel at any time. :P

---

### Post by jtwood on 2011-08-02
Bump

Just looking for a place to start.  I haven't found anything in Google or the forums

Thanks in advance

---

### Post by dino99 on 2011-08-02
[http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html)

[http://www.google.fr/url?sa=t&source=web&cd=3&sqi=2&ved=0CDAQFjAC&url=http%3A%2F%2Fwww.3ware.com%2Fdownload%2FEscalade9550SX-Series%2F9.3.0.1%2F9.3.0.1_Release_Notes_Linux_FreeBSD_install_Web.pdf&rct=j&q=linux%20raid%203ware%20compilation%20driver&ei=eRE4TrUnhfOyBqeYzQc&usg=AFQjCNHTDcCV0wcPUQqS-UgR2hFCPwKn4Q&cad=rja](http://www.google.fr/url?sa=t&source=web&cd=3&sqi=2&ved=0CDAQFjAC&url=http%3A%2F%2Fwww.3ware.com%2Fdownload%2FEscalade9550SX-Series%2F9.3.0.1%2F9.3.0.1_Release_Notes_Linux_FreeBSD_install_Web.pdf&rct=j&q=linux%20raid%203ware%20compilation%20driver&ei=eRE4TrUnhfOyBqeYzQc&usg=AFQjCNHTDcCV0wcPUQqS-UgR2hFCPwKn4Q&cad=rja)

[http://www.phwinfo.com/forum/linux-debian-user/235160-3ware-9650-se-etch-how-prevent-driver-being-upgraded.html](http://www.phwinfo.com/forum/linux-debian-user/235160-3ware-9650-se-etch-how-prevent-driver-being-upgraded.html)

---

### Post by jtwood on 2011-08-04
Ok, I stumbled into this page:

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

The first question addressed my issue and worked to build the driver I needed:

Thanks.

---

