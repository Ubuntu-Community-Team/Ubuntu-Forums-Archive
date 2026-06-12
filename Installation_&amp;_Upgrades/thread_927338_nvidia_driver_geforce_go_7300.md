---
title: "nvidia driver geforce go 7300"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by mavuashire on 2008-09-22
After intalling to Ubuntu 8.04 the graphics were poor as usual. What I'd normally do is download the drivers from the nvidia website and install them. It was always a tricky exercise for me. But this time nothing seems to work. 

If I go to the black screen and run the scrip "sh NVIDIA-...", I get a message about not having the kernel and it directs me to a log file that makes no sense to me. Of late, that is after installing and unstalling several nvidia packages, when i try the script it just returns an error message and aborts.

I am trying to install this on a toshiba satellite laptop
graphics card: nvidia geforce go 7300
screen 1200 x 800

---

### Post by Pumalite on 2008-09-22
Try:
sudo apt-get install build-essential

---

### Post by mavuashire on 2008-09-22
sudo apt-get install build-essential results

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---------------------X--------------------------X-------------------
Just now when I tried to install the driver, it is now saying 

"The kernel you are installing is a Xen kernel!

The NVIDIA driver does not currently work on the Xen kernels. If you are using a stock distribution kernel, please install a variant of this kernel without Xen support; If this is a custom kernel, please install a standard linux kernel. Then try installing the NVIDIA kernel module again."

I am not using custom built kernel. However, I have updated the kernel using the system updater (I guess the linux headers are the kernel we are talking about)

---

### Post by Pumalite on 2008-09-22
Try:
sudo apt-get install linux-headers-`uname -r`

---

### Post by mavuashire on 2008-09-22
sudo apt-get install linux-headers-`uname -r` results

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-19-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Pumalite on 2008-09-22
Tell me how are you installing your driver?

---

### Post by mavuashire on 2008-09-22
I don't really understand the question but if you want the steps i take to install the driver

Ctrl + alt + f1
$ /etc/init.d/gdm stop
$ sh Desktop/NVIDIA-Linux-x86-173.14.12-pkg1.run 

After a few quesions (EULA & warning)

the message it gives message about Xen then the following message

 ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).


Here are the contents of the log file:



nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Sep 23 12:55:36 2008
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-19-server/build'
-> Kernel output path: '/lib/modules/2.6.24-19-server/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
ERROR: The kernel you are installing for is a Xen kernel!
       
       The NVIDIA driver does not currently work on Xen kernels. If 
       you are using a stock distribution kernel, please install 
       a variant of this kernel without Xen support; if this is a 
       custom kernel, please install a standard Linux kernel.  Then 
       try installing the NVIDIA kernel module again.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by emshains on 2008-11-03
Use envy!

---

