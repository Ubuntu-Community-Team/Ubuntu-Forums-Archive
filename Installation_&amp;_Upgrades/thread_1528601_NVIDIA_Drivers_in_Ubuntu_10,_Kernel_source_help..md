---
title: "NVIDIA Drivers in Ubuntu 10, Kernel source help."
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by omnisource on 2010-07-11
Ok I am trying to install the latest nVidia Drivers to my system. It is a NVIDIA 9600gt, I am using drivers from here for Ubuntu x64 [[http://www.nvnews.net/vbulletin/showthread.php?t=109422](http://www.nvnews.net/vbulletin/showthread.php?t=109422)]

I get this error message:
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.

**How Do I do this?** I am still new to unix and do not know what that means. I think this is that last part of the installation process I need to actually install the drivers (took me long enough to figure out how to turn the X server off lol)

I have been reading the nVidia forums and even the noobs there know more than I do lol. Here is a copy of the entire installer log file:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Jul 10 22:53:47 2010

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
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-23-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-23-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
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
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by omnisource on 2010-07-11
anyone? I navigated to lib/modules/2.6.32-23 directory and the source is there but all the folders have the shortcut icon over them

---

### Post by alterpinguin on 2010-07-11
why did You not use the entry in the menu:
System -> Hardware Driver
and installed the nvidia-propietary driver with this menu-point?
-
The only use for doing a built of the nvidia-drivers local
is if you did install the kernel-sources and you did built
a special kernel on your own.
But then, the kernel-sources are on your machine and
the nvidia-install should find those parts from the source (header-files) and from the built.

---

### Post by Shazaam on 2010-07-11
Try this...
```
sudo apt-get install linux-headers-$(uname -r)
```
This code will install the kernel-headers for your current kernel version (uname -r) if they are not currently installed.

---

### Post by omnisource on 2010-07-11
Alterpinguin. I did use that method until I was told the graphics would still be software rendered and that I had to install it this way to have it hardware rendered. Was I told incorrect information?


Shazam. Yep tried that

---

### Post by cascade9 on 2010-07-11
> **omnisource said:**
> Alterpinguin. I did use that method until I was told the graphics would still be software rendered and that I had to install it this way to have it hardware rendered. Was I told incorrect information?

Yes, that info was wrong. 

BTW, those are very old drivers in that link 171.xx, and over 2 years old now. The current nvidia drivers for that card in the ubuntu repositories are 195.xx

---

### Post by tommcd on 2010-07-11
> **omnisource said:**
> Ok I am trying to install the latest nVidia Drivers to my system. It is a NVIDIA 9600gt
Have you tried the nvidia driver from the Ubuntu repos???? ... as **alterpinguin** suggested with using: system > administration > hardware_driver ???
This should *always* be your first choice, unless the latest driver in the Ubuntu repos will not work for you for some reason.
To install the driver from the Ubuntu repos ... I prefer using the terminal to install the specific driver that I want rather than using the hardware_drivers helper to decide for me. For your late model nvidia card (and my card also) it is:
```

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

```
After you reboot, run:
```
glxinfo | grep -i render
```
It should answer with something like:
```

bash-4.1$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2/3DNOW!
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
bash-4.1$ 

```

---

### Post by omnisource on 2010-07-11
Thanks all of you. Now that I know I was using incorrect information I can just try it with the hardware wizard. Or with that command you just.  Posted.

I appreciate it

---

### Post by ex_isp on 2010-07-11
Tommcd,

I don't understand why 3dnow is showing up in your output if you have an Nvidia card...

Please explain.

Ex

---

### Post by tommcd on 2010-07-12
> **ex_isp said:**
> Tommcd,
I don't understand why 3dnow is showing up in your output if you have an Nvidia card...
Please explain.

Well, to be perfectly honest ... I did not even know what 3Dnow was!
You see, I had always been in the habit of running:
```
glxinfo | grep -i direct
```
to check for the **direct rendering: Yes** output. In a thread on the LQ forums it was suggested that it is better to run:
 *glxinfo | grep -i render*:
[http://www.linuxquestions.org/questions/slackware-14/games-are-slow-818411/](http://www.linuxquestions.org/questions/slackware-14/games-are-slow-818411/)
The 3Dnow stuff does not show up when you *grep direct*. It only shows up when you *grep render*.

A quick google search has found that 3Dnow is something that is integral to AMD CPUs:
[http://en.wikipedia.org/wiki/3DNow](http://en.wikipedia.org/wiki/3DNow)!
[http://www.tomshardware.com/reviews/3dnow,109.html](http://www.tomshardware.com/reviews/3dnow,109.html)
It seems that the nvidia drivers get along ok with 3Dnow:
[http://www.nvidia.com/object/IO_20020109_5677.html](http://www.nvidia.com/object/IO_20020109_5677.html)
So ... perhaps you could explain this to me! Is there a problem with 3Dnow and the nvidia driver output I posted?
I have never actually heard of this 3Dnow thing before.
Gee whiz, you learn something new every day around here!

---

