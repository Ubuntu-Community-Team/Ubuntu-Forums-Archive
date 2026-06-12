---
title: "Ibex Alpha 5 installation of nvidia-glx-177 fails"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by jakobbg on 2008-09-07
Basically I want nvidia-driver installed on Alpha 5. Have tried hardware-manager, but the only thing that tool managed was to tear my newly installed D820 from 1400x1050 to 800x600.

$ lspci|grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

$ uname -a
Linux deathstar 2.6.27-2-generic #1 SMP Thu Aug 28 17:20:02 UTC 2008 i686 GNU/Linux

$ dpkg -l | grep -i kernel|cut -f 3 -d ' '
dkms
klogd
libdevmapper1.02.1
libdrm2
linux-generic
linux-headers-2.6.25-1-386
linux-image-2.6.27-2-generic
linux-image-generic
linux-libc-dev
linux-ports-headers-2.6.25-1
linux-restricted-modules-2.6.27-2-generic
linux-restricted-modules-generic
linux-source-2.6.27
module-init-tools
nvidia-177-kernel-source
udev

Then tried to install the thingy manually, but it does not work still.

jakobbg@deathstar:~$ sudo apt-get install nvidia-glx-177
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-177-kernel-source nvidia-settings
The following NEW packages will be installed:
  nvidia-177-kernel-source nvidia-glx-177 nvidia-settings
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.0MB of archives.
After this operation, 35.1MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously deselected package nvidia-177-kernel-source.
(Reading database ... 91943 files and directories currently installed.)
Unpacking nvidia-177-kernel-source (from .../nvidia-177-kernel-source_177.70-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-glx-177.
Unpacking nvidia-glx-177 (from .../nvidia-glx-177_177.70-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_173.14.09-1ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-177-kernel-source (177.70-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 177.70
Doing initial module build

Error! Your kernel source for kernel 2.6.27-2-generic cannot be found at
/lib/modules/2.6.27-2-generic/build or /lib/modules/2.6.27-2-generic/source.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.27-2-generic (i686) first.
Done.

Setting up nvidia-glx-177 (177.70-0ubuntu1) ...
Setting up nvidia-settings (173.14.09-1ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by Pumalite on 2008-09-07
Intrepid Ibex is in development. Maybe you should post your problem in the sub-forum

---

### Post by Pumalite on 2008-09-07
OTOH; I can show you this:
 sudo apt-get install nvidia-glx-177
[sudo] password for pumalite: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libamrnb3 glide2-bin libamrwb3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dkms nvidia-177-kernel-source nvidia-settings
The following NEW packages will be installed:
  dkms nvidia-177-kernel-source nvidia-glx-177 nvidia-settings
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.1MB of archives.
After this operation, 35.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main dkms 2.0.20.4-0ubuntu1 [55.2kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted nvidia-177-kernel-source 177.70-0ubuntu1 [2693kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted nvidia-glx-177 177.70-0ubuntu1 [8575kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe nvidia-settings 173.14.09-1ubuntu3 [768kB]
Fetched 12.1MB in 18s (644kB/s)                                                
Selecting previously deselected package dkms.
(Reading database ... 239370 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.0.20.4-0ubuntu1_all.deb) ...
Selecting previously deselected package nvidia-177-kernel-source.
Unpacking nvidia-177-kernel-source (from .../nvidia-177-kernel-source_177.70-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-glx-177.
Unpacking nvidia-glx-177 (from .../nvidia-glx-177_177.70-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_173.14.09-1ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up dkms (2.0.20.4-0ubuntu1) ...
Setting up nvidia-177-kernel-source (177.70-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 177.70
Doing initial module build
Installing initial module
Done.

Setting up nvidia-glx-177 (177.70-0ubuntu1) ...

Setting up nvidia-settings (173.14.09-1ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
pumalite@pumalite-desktop:~$

---

### Post by dn* on 2008-09-11
Have you tried using Envy? It's in Ubuntu 'universe' repository. I myself am having issues with the new kernel, my X Server isn't recognizing a proper resolution or loading the driver properly.

If you install the nvidia drivers, see if it does the same thing?

---

### Post by redlegion on 2008-09-12
Well, I'm running it also. I've noticed that for some reason nvidia.ko exists in /var/lib/dkms/nvidia/177.70/build/. No idea why. In any case, you can usually use "insmod" to pop that sucker into the kernel and use "Ctrl + Alt + Backspace" and an xorg.conf that includes the driver and glx module, and you're good to go. The only problem is, I don't know how to make such an alias automatic so that /etc/modules would call it's insertion and make all this unnecessary, or why 177.70 is installed to that directory in the first place. No clue. It works fine, though. Works fine indeed.

---

