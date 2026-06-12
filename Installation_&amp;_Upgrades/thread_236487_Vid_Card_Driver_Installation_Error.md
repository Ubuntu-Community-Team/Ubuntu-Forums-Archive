---
title: "Vid Card Driver Installation Error"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by linuxnoobie on 2006-08-14
OK,

I downloaded the newest driver via nvidia.com.  Went to install it and got an error.  Checked the nvidia-installer.log and found the following.  Does any of this mean anything to any of you?

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Aug 14 20:09:11 2006

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
  OpenGL header files     : true
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
ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
       kernel.  This may be because it is in use (for example, by the X
       server), but may also happen if your kernel was configured without
       support for module unloading.  Please be sure you have exited X before
       attempting to upgrade your driver.  If you have exited X, know that your
       kernel supports module unloading, and still receive this message, then
       an error may have occured that has corrupted the NVIDIA kernel module's
       usage count; the simplest remedy is to reboot your computer.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by meng on 2006-08-14
The way to install nvidia drivers is:
sudo aptitude nvidia-glx

or else use Synaptic to do the same

---

### Post by pdub on 2006-08-14
Why are you installing the driver from the Nvidia site?

You probably want to install the latest one from a repository instead.

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

---

### Post by linuxnoobie on 2006-08-14
Because I unfortunately don't know any better.  I'll try that and see what happens.

---

### Post by linuxnoobie on 2006-08-14
This is what I get:

scott@gateway:~$ sudo apt-get install nvidia-glx nvidia-kernel-common
Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
nvidia-kernel-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott@gateway:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
scott@gateway:~$

I did alter the xorg.conf but I had to in order to lower my resolution.  Just going to system>preferences>screen resolution didnt work.

---

### Post by meng on 2006-08-14
> otherwise edit manually /etc/X11/xorg.conf to change the Driver section from nv to nvidia. This should fix it.

---

### Post by pdub on 2006-08-14
If you are still having problems then post your xorg.conf file here.

Also post resolution that you wish to run.

---

### Post by Beastmouth on 2006-08-15
I'm trying this, too.  I changed the xorg.conf "nv" to "nvidia", as the error message suggested, then I entered ```
md5sum /etc/X11/xorg.conf | sudo tee var/lib/x11/xorg.conf
``` (also suggested by the error message) and all that showed up on my terminal was ```
7a1ffcc62246dfcbc0e6b55fd1d406dc  /etc/X11/xorg.conf

```. 

I entered again sudo nvidia-glx-config enable but am still getting error message:

```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```

I haven't altered the xorg.conf file in any other way than changing the driver line on the video card from nv to nvidia, and my screen resolution's fine.

---

### Post by pdub on 2006-08-15
Beastmouth,

Does X load and work OK for you with "nvidia" instead of "nv"?

If so, you are done.

---

