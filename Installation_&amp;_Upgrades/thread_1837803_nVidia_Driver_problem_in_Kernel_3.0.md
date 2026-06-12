---
title: "nVidia Driver problem in Kernel 3.0"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by Randize on 2011-09-02
Here's my release and kernel version.
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Linux randize-EX58-UD3R 3.0.0-0300-generic #201107220917 SMP Fri Jul 22 09:20:45 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```I'm having problem with my nvidia driver. I removed and install nvidia-current, and here's the result:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-settings
The following NEW packages will be installed:
  nvidia-current nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 929 kB/50.7 MB of archives.
After this operation, 154 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://my.archive.ubuntu.com/ubuntu/ natty/main nvidia-settings amd64 270.29-0ubuntu1 [929 kB]
Fetched 929 kB in 4s (188 kB/s)          
Selecting previously deselected package nvidia-current.
(Reading database ... 170944 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_270.41.06-0ubuntu1_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_270.29-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (270.41.06-0ubuntu1) ...
Loading new nvidia-current-270.41.06 DKMS files...
Building only for 3.0.0-0300-generic
Building for architecture x86_64
Building initial module for 3.0.0-0300-generic

Error! Bad return status for module build on kernel: 3.0.0-0300-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/270.41.06/build/ for more information.
Setting up nvidia-settings (270.29-0ubuntu1) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-support ...

```Here's the log:
```
DKMS make.log for nvidia-current-270.41.06 for kernel 3.0.0-0300-generic (x86_64)
Fri Sep  2 21:22:01 MYT 2011
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1
```Any solution to this problem? I downloaded the latest driver from nVidia but doesn't let me install. The problem stated in the log:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Sep  2 20:52:10 2011
installer version: 280.13

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  force compat32 tls                 : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  compat32 install chroot            : (not specified)
  compat32 install prefix            : (not specified)
  compat32 install libdir            : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : ftp://download.nvidia.com
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1009'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       www.nvidia.com.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```Followed a few guide I found on the net to exit X. So I tried gdm stop outside GUI mode (CTRL + ALT + F1) but doesn't work. Here's the error.
```
** (gdm-binary:14287): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.55" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:14287): WARNING **: Could not acquire name; bailing out

```I found a patch from the net too but I'm quite a novice Linux user, have no idea how to patch it. Here's the link I was referring to [http://www.nvnews.net/vbulletin/showthread.php?t=165000](http://www.nvnews.net/vbulletin/showthread.php?t=165000)

---

### Post by Hizoomi on 2011-10-27
I just ran into this "Unable to determine the target kernel version" problem in Gentoo with nvidia-drivers-96.43.19 (I have a "legacy" board) after upgrading from kernel 2.6.39 to 3.0.6.  Perhaps the installation script can only handle pre-3.0 kernels, based on the printed comments about 2.4 and 2.6?

-Charles

---

