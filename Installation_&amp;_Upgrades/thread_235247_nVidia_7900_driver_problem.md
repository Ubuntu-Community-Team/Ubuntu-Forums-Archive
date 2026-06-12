---
title: "nVidia 7900 driver problem"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by AsRock on 2006-08-12
While in root and not in GUI i run ./file name from nVidia site and get this error in a log it makes.

I do have another problem and thats getting DOOM 3 installed \ setup on this system too.

Any help would be Great!

Thank You

> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC test with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' RPM installed.  If you
       know the correct kernel source files are installed, you may specify the
       kernel source path with the '--kernel-source-path' command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by bmorency on 2006-08-14
"No precompiled kernel interface was found to match your kernel; would you li
ke the installer to attempt to download a kernel interface for your kernel f
rom the NVIDIA ftp site"

What I think you will need the kernel header files.

To install them open up the console and type: sudo aptitude install linux-headers-`uname -r`

that should install the header files needed for the driver. I'm not sure if it will ask you where they are located but they will be under /usr/src/linux-headers-*  

Hopefully that will help.

---

