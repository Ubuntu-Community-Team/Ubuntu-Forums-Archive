---
title: "can not start oracle vm virtual box after upgrading"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by techbrainless on 2012-04-16
Hi All,

I have upgraded from ubuntu 10.04 to ubuntu 11.04 successfully 

I was running oracle vm virtual box  on 10.04 , but after upgrading to 11.04 I am unable to start it , 



```
$ sudo virtualbox 
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.38-02063801-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.



```

```
$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                                                                                                                                                      [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                                                                                                                                                         [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                                                                                                                                                    
Error! Your kernel headers for kernel 2.6.38-02063801-generic cannot be found at
/lib/modules/2.6.38-02063801-generic/build or /lib/modules/2.6.38-02063801-generic/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                                                                                                                                                          
 * Look at /var/log/vbox-install.log to find out what went wrong

```

```
$ cat  /var/log/vbox-install.log
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  4.0.14

------------------------------
Deleting module version: 4.0.14
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.0.14/source ->
                 /usr/src/vboxhost-4.0.14

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.38-02063801-generic package.
Failed to install using DKMS, attempting to install without
Makefile:169: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

---

### Post by gordintoronto on 2012-04-16
How did you install Virtualbox?

Did you actually *upgrade* from 10.04 to 10.10, then to 11.04?

In theory, you should be able to uninstall Virtualbox, then install it from the repositories without losing any of your virtual machines, but I would want to have extremely good backup before attempting this.

---

### Post by techbrainless on 2012-04-17
Thanks for your reply , 


> How did you install Virtualbox?
using apt-get

>  Did you actually *upgrade* from 10.04 to 10.10, then to 11.04?
10.04 directly to 11.04

> In theory, you should be able to uninstall Virtualbox, then install it  from the repositories without losing any of your virtual machines, but I  would want to have extremely good backup before attempting this. 	
I will test that and reply you back

---

### Post by techbrainless on 2012-04-17
I am still getting the same error 

I have removed the virtualbox

install it again 

```
$ sudo apt-get install virtualbox-4.0 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-4.0
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 61.8 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Get:1 http://download.virtualbox.org/virtualbox/debian/ natty/contrib virtualbox-4.0 i386 4.0.16-75491~Ubuntu~natty [61.8 MB]
Fetched 29.5 MB in 16min 41s (29.5 kB/s)                                                                                                                                                                         
Preconfiguring packages ...
Selecting previously deselected package virtualbox-4.0.
(Reading database ... 163313 files and directories currently installed.)
Unpacking virtualbox-4.0 (from .../virtualbox-4.0_4.0.16-75491~Ubuntu~natty_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up virtualbox-4.0 (4.0.16-75491~Ubuntu~natty) ...
Installing new version of config file /etc/init.d/vboxdrv ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Stopping VirtualBox kernel modules                                                                                                                                                                      [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                                                                                                                                                         [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                                                                                                                                                    
Error! Your kernel headers for kernel 2.6.38-02063801-generic cannot be found at
/lib/modules/2.6.38-02063801-generic/build or /lib/modules/2.6.38-02063801-generic/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                                                                                                                                                          
 * Look at /var/log/vbox-install.log to find out what went wrong
Processing triggers for python-central ...

```


```
 $ cat /var/log/vbox-install.log 
Uninstalling modules from DKMS
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.0.16/source ->
                 /usr/src/vboxhost-4.0.16

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.38-02063801-generic package.
Failed to install using DKMS, attempting to install without
Makefile:169: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

---

### Post by MonkeyPaw on 2012-04-18
Virtualbox is up to version 4.1.12 on my machine, so it looks like you are pulling down an old version. Perhaps you are having some compatibility issues with 4.0.x and the updated kernel? Not really sure, but that's all that stands out to me.

I just installed through Software Center.

---

### Post by tmaranets on 2012-04-18
You might be using an older version of VirtualBox that is not compatible with 11.04. Try installing the 4.1.12 version.

---

### Post by lisanels47 on 2012-04-18
You are missing the headers for re-building the virtualbox drivers.  use "dpkg -l | grep linux" and see if you have the headers to go with the kernel you are running.  See my list from my machine below.

Use "uname -a" to see what kernel you are really running.



ii  linux-headers-3.2.0-20                 3.2.0-20.33                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-20-generic         3.2.0-20.33                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-21                 3.2.0-21.34                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-21-generic         3.2.0-21.34                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-22                 3.2.0-22.35                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-22-generic         3.2.0-22.35                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-23                 3.2.0-23.36                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-23-generic         3.2.0-23.36                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.23.25                             Generic Linux kernel headers
ii  linux-image-3.2.0-20-generic           3.2.0-20.33                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-21-generic           3.2.0-21.34                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-22-generic           3.2.0-22.35                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-23-generic           3.2.0-23.36                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP

---

### Post by Shazaam on 2012-04-19
Give this a try...
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by SeijiSensei on 2012-04-19
You'll also need to install the gcc compiler and tools. I'd also reboot before you begin in case your current kernel version and the one grub boots aren't the same.  After rebooting run:

```

sudo apt-get update
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo apt-get remove virtualbox-4.0

```

Now visit [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) and follow the instructions for "Debian-based distributions."  Edit /etc/apt/sources.list as directed adding the line that matches your version's name, "natty" if you're running 11.04. Follow the remaining instructions.  

Once you have build-essential and the matching kernel headers installed, VirtualBox will be able to compile a compatible kernel driver if a new kernel is distributed.

---

