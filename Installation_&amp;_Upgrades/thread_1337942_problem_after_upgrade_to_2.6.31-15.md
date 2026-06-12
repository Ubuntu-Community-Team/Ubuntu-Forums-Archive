---
title: "problem after upgrade to 2.6.31-15"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by samair on 2009-11-25
hi
i upgrade kernel in ubuntu 9.10 and then reset my system
now  in kernel 2.6.31-15 when press enter go to terminal and i cant see graphic mode
and
 i can not install nvidia driver
i run
sudo sh NVIDIA-Linux-x86-190.42-pkg1.run


[B][quote]unable to find the kernel source tree for currenty running kernel
please make sure you have installed the kernel source file for our
kernel and that they are property configured on red hat linux systems
for example , be make sure you have the kernel-source or kernal -devel rpm installed



       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com/").[/B]


but
 kernel 2.6.31.14 is fine

please help me

---

### Post by alexmaco on 2009-11-26
I had this problem too, but I have an ati card and for me it worked after i generated and installed new packages for the 31-15.

Based on your error, I would suggest installing the kernel source and headers (packages are : linux-source, linux-headers-generic, linux-headers-2.6.31-15 ) and trying again afterwards.

---

### Post by samair on 2009-11-26
> **alexmaco said:**
> I had this problem too, but I have an ati card and for me it worked after i generated and installed new packages for the 31-15.

Based on your error, I would suggest installing the kernel source and headers (packages are : linux-source, linux-headers-generic, linux-headers-2.6.31-15 ) and trying again afterwards.


i do this
but not work

---

### Post by dhavalbbhatt on 2009-11-26
Can you revert back to using 2.6.31-14 kernal? I know there are some issues with the newer kernal. There is a bug report on launchpad here -

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/487355](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/487355)

See if you can use any information from there, although that is more related to GRUB 2.0

---

