---
title: "Please help! Can't install Invidia graphics driver!"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by MgNate on 2007-02-21
I've been trying to install the drivers for my Invidia Geforce 6150 LE. I've been trying to installl the drivers for the past two days and i havent had any luck. 
I've tried a bunch of different ways but I've mostly used envy.

Please help me.


> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Feb 21 20:10:30 2007

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : false
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
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
  X install prefix        : /usr/lib64/xorg/modules
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
  kernel source path      : /usr/src/linux-headers-2.6.15-26-amd64-generic
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:
   
   The compiler used to compile the kernel (gcc 4.0) does not exactly match the
   current compiler (gcc 4.1).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


---

### Post by tsav87 on 2007-02-21
I used Automatix to install my Nvidia 7900GS Go Driver, worked well.  Just restart your system and the changes should take affect.

---

### Post by teaker1s on 2007-02-21
basically all it's saying is it doesn't like the newer compiler used on kernel. have you tried asking on nvidia forum -if it will cause problems compiling with newer compiler. I guess it wont but I'd check first.

---

### Post by MgNate on 2007-02-21
I'd rather not post on another forum it's bad enough surfing this one cause firefox is messed up because my graphics card is messed up. and i tried downloading Automatix but the site wasn't working, is it free?

---

### Post by MgNate on 2007-02-21
I downloaded automatix2 and it's installing right now, it's hanging on the nvidia driver, i hope it keeps going,,,:confused:


Yeah, it said an apt based error occured...

---

### Post by radj2 on 2007-02-21
I used easy ubuntu instead of automatix It caused my desktop to disappear


This may help

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by MgNate on 2007-02-21
> **radj2 said:**
> I used easy ubuntu instead of automatix It caused my desktop to disappear


This may help

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I have edgy i should of mentioned that...

---

### Post by MgNate on 2007-02-22
I tried automatix again and still no luck. I'm completely stuck at the moment because i can't do much more without installing these driver, it's driving me crazy. Automatix did sucessfully install some other things by the way. It just wouldn't install the Nvidia(64bit) drivers or the debian menu.

I don't care what i use i just want to get these drivers installed...

---

### Post by mezhaka on 2007-02-26
got the same problem -- still didn't solve it...
here's what the guy behind the envy script [replied ]("http://www.ubuntuforums.org/showpost.php?p=2011068&postcount=1423"), but i guess he's forgotten. maybe if you post the same problem to [this]("http://www.ubuntuforums.org/showthread.php?t=139264") thread he'll take this issue into consideration?

---

