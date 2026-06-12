---
title: "64bit VirtualBox XP not starting."
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by nitric on 2010-10-22
Ok guys, I've been on here before and gotten some great help, I need that once again!

First off I'm running Ubuntu 10.10 64bit, if you would like a complete discription of my hardware you can find my lshw > [http://dl.dropbox.com/u/6920165/lshw%28vaio%29.html](http://dl.dropbox.com/u/6920165/lshw%28vaio%29.html)

I seem to have broken my VirtualBox installation, I went from VirtualBox OSE to VirtualBox 3.2 (again 64bit version downloaded from virtualbox.org the about says version 3.2.10 r66523) I tried apt-get purging 3.2 and going back to OSE but it gives me the same error I started getting when I tried installing 3.2 so I have decided to install that again and try and trouble shoot the problem.

I get two error windows that pop up when I try and start my windows xp virtualbox, the first says:

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
And the second says:

Failed to open a session for the virtual machine Sierra Designs - XP.
The virtual machine 'Sierra*Designs*-*XP' has terminated unexpectedly during startup with exit code 1.
Details:


Result*Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}

So I open up a terminal and run 

$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                            *  done.

 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.

 * Trying to register the VirtualBox kernel modules using DKMS                  

Error! Your kernel headers for kernel 2.6.32-24-generic cannot be found at

/lib/modules/2.6.32-24-generic/build or /lib/modules/2.6.32-24-generic/source.



 * Failed, trying without DKMS

 * Recompiling VirtualBox kernel modules                                        

 * Look at /var/log/vbox-install.log to find out what went wrong


So I look at vbox-install.log and it says,
Uninstalling modules from DKMS

Attempting to install using DKMS



Creating symlink /var/lib/dkms/vboxhost/3.2.10/source ->

                 /usr/src/vboxhost-3.2.10



DKMS: add Completed.

You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.32-24-generic package.

Failed to install using DKMS, attempting to install without

Makefile:159: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

I also tried running:

$ sudo modprobe vboxdrv

and received the error:

FATAL: Module vboxdrv not found.


Any suggestions?

---

### Post by mikewhatever on 2010-10-23
```
Error! Your kernel headers for kernel 2.6.32-24-generic cannot be found at
```

So, what's the output of **dpkg -l | grep headers**  ?

---

### Post by nitric on 2010-10-23
$ dpkg -l | grep headers
ii  linux-headers-2.6.35-22                     2.6.35-22.35                                      Header files related to Linux kernel version 2.6.35
ii  linux-headers-2.6.35-22-generic             2.6.35-22.35                                      Linux kernel headers for version 2.6.35 on x86/x86_64
ii  linux-headers-2.6.35-22-virtual             2.6.35-22.35                                      Linux kernel headers for version 2.6.35 on x86/x86_64
ii  linux-headers-generic                       2.6.35.22.23                                      Generic Linux kernel headers

---

### Post by siliconmeadow on 2010-10-23
This error message:
> **nitric said:**
> Error! Your kernel headers for kernel 2.6.32-24-generic cannot be found at

/lib/modules/2.6.32-24-generic/build or /lib/modules/2.6.32-24-generic/source.
and this report:
> **nitric said:**
> $ dpkg -l | grep headers
ii  linux-headers-2.6.35-22                     2.6.35-22.35                                      Header files related to Linux kernel version 2.6.35
ii  linux-headers-2.6.35-22-generic             2.6.35-22.35                                      Linux kernel headers for version 2.6.35 on x86/x86_64
ii  linux-headers-2.6.35-22-virtual             2.6.35-22.35                                      Linux kernel headers for version 2.6.35 on x86/x86_64
ii  linux-headers-generic                       2.6.35.22.23                                      Generic Linux kernel headers

Show that the header files don't match the currently running kernel, as far as I can tell. I don't know the finer points of kernel development, but it looks as if the header files are for a newer kernel than the one you're running. If you can get the kernel and its header files in sync, ```
sudo /etc/init.d/vboxdrv setup
``` will probably sort things out for you.

HTH

---

### Post by nitric on 2010-10-25
So I gave up and just re-installed :P make sure your /home is mounted on a separate partition people! I love being able to reinstall without having to back up! :P so now it's working I just didn't install the OSE and went straight to 3.2 and it's wonderful! I figure it was a problem with the kernel installation and I didn't really want to try and mess with that :P

I need to build a system just to learn how to fix broken systems.

Again, Thanks for the help forums!

---

