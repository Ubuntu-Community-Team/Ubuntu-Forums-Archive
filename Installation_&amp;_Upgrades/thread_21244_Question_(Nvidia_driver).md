---
title: "Question (Nvidia driver)"
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by granite230 on 2005-03-21
I'm trying to install the latest Nvidia driver. The readme says:

KERNEL INTERFACES

The NVIDIA kernel module has a kernel interface layer which must be
compiled specifically for the configuration and version of the kernel
you are running.  NVIDIA distributes the source code to this kernel
interface layer, as well as a precompiled version for many of the kernels
distributed by some popular distributions.
  
When the installer is run, it will determine if it has a precompiled
kernel interface for the kernel you are running.  If it does not have
one, it will check if there is one on the NVIDIA ftp site (assuming you
have an internet connection), and download it.

If a precompiled kernel interface is found that matches your kernel,
then that will be linked[1] against the binary portion of the NVIDIA
kernel module.  The result of this operation will be a kernel module
appropriate for your kernel.

If no matching precompiled kernel interface is found, then the installer
will compile the kernel interface for you.  However, first it will
check that you have the correct kernel headers intalled on your system.
If the installer must compile the kernel interface, then you must install
the kernel-sources package for your kernel.

**Question: how do I install the kernel-sources package for my kernel? and where?**

[1] NOTE: installation requires that you have a linker installed.
The linker, usually '/usr/bin/ld', is part of the binutils package;
please be sure you have this package installed prior to installing the
NVIDIA driver.

**Question: what are they talking about here? Where can I find this 'binutils' package?**

I'm just a n00b so please be specific, thanks!

---

### Post by granite230 on 2005-04-26
What I did:
- disable X
- login as root
- type: sh NVIDIA-Linux-x86-1.0-7174-pkg1.run

This is what the log file says (ERRORS at the bottom):

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Apr 26 14:46:30 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : false
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
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
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

I also tried this:

granite@granite:~ $ uname -r
2.6.8.1-5-686

is that kernel version 2.6.8?

if I try:
granite@granite:~ $ sudo apt-get install kernel-source-2.6.*

I get this:

Reading Package Lists... Done
Building Dependency Tree... Done
Note, selecting kernel-source-2.6.1 for regex 'kernel-source-2.6.*'
Note, selecting kernel-source-2.6.4 for regex 'kernel-source-2.6.*'
Note, selecting kernel-source-2.6.5 for regex 'kernel-source-2.6.*'
Note, selecting kernel-source-2.6.6 for regex 'kernel-source-2.6.*'
Note, selecting kernel-source-2.6.7 for regex 'kernel-source-2.6.*'
Note, selecting kernel-source-2.6 for regex 'kernel-source-2.6.*'
The following extra packages will be installed:
  kernel-source-2.6.5 kernel-source-2.6.6
Suggested packages:
  kernel-package
The following NEW packages will be installed:
  kernel-source-2.6.5 kernel-source-2.6.6
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 68.8MB of archives.
After unpacking 69.1MB of additional disk space will be used.

since 2.7 is the closest to 2.8 I tried that... same error pops up when I try to install that NVIDIA driver...

Is there anybody who knows what to try next?

---

### Post by granite230 on 2005-04-26
it has been fixed!! 

I'm not sure what changes were made on my system because a friend did most of the work :P

it was something like this:

I've installed the kernel headers with



apt-get install linux-headers-2.6.8.1-5-686



then tried installing the driver again... that seems to work!

---

