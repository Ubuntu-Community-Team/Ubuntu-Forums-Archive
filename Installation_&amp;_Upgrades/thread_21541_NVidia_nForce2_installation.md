---
title: "NVidia nForce2 installation"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by Dracontopes on 2005-03-22
Trying Ubuntu again.

Installed 4.10 and upgraded to Hoary. 
Now I'm trying to install de nvidia nforce2 platform drivers, but they are giving me headache...

I downloaded the install script from nvida.com and followed instructions. In the installation, after the step that says the installer cannot find pre-installed blablabla, is says:

> 
ERROR:
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
         the appropriate nvidia-installer command line option.


In the error log:

> 
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Tue Mar 22 23:37:05 2005

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA network driver for Linux-x86 (1.0-11)
   NVIDIA audio driver for Linux-x86 (1.0-2)
-> Starting install of NVIDIA network driver for Linux-x86
-> Checking for loaded module nvnet
-> Checking for loaded module forcedeth
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.10-5-386 (buildd@rothera) (gcc version
   3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Mar 15 14:43:37 UTC 2005
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/usr/src/linux'
-> Kernel output path: '/usr/src/linux'
-> Performing cc_version_check with CC="cc".
ERROR: 
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
       the appropriate nvidia-installer command line option.
ERROR: Installation of the network driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com]("http://www.nvidia.com").


Something with version check is not going well here...

uname -r gives: 2.6.10-5-386

Contents of /usr/src : 
linux                   
linux-source-2.6.10          
rpm
linux-headers-2.6.10-5  
linux-source-2.6.10.tar.bz2

What am I doing wrong? :P

---

### Post by MicroChris on 2005-03-22
What do you need them for? nForce 2 drivers come with ubuntu.... Really no need for them..

Sound and NIC work fine for me on my a7n8x

---

### Post by Dracontopes on 2005-03-22
[QUOTE=MicroChris]What do you need them for? nForce 2 drivers come with ubuntu.... Really no need for them..

Sound and NIC work fine for me on my a7n8x[/QUOTE]
 Hmm idd, I do have sounds and networking. But I want my 4.1 analog speakers to work, now I only have the 2 front speakers working...

---

### Post by Dracontopes on 2005-03-24
[QUOTE=Dracontopes]Hmm idd, I do have sounds and networking. But I want my 4.1 analog speakers to work, now I only have the 2 front speakers working...[/QUOTE]
 Hehe, I just plugged my rear speakers, together with my front speakers, into the lineout :) Now the sounds is pretty much OKAY...

---

### Post by MicroChris on 2005-03-24
Hehe,

Awesome man. Does alsamixer have any kind of surround sound control?

Glad everything works  :) 

-Chris

---

### Post by Dracontopes on 2005-03-24
[QUOTE=MicroChris]Hehe,

Awesome man. Does alsamixer have any kind of surround sound control?

Glad everything works  :) 

-Chris[/QUOTE]
 It has an option called duplicate front. It does work, but the sound is horrible... No bass etc, so don't use it :P (unless you have proper speakers that support it correctly)

---

### Post by c_dog on 2005-03-24
[QUOTE=MicroChris]Hehe,

Awesome man. Does alsamixer have any kind of surround sound control?

Glad everything works  :) 

-Chris[/QUOTE]

Yep, (on Audigy 2 at least AFAIK) there's Front, Rear, Center, & LFE in both PCM and regular mixers in alsamixer. xine, vlc, mplayer work pretty good with and even let throw in some effects.

---

### Post by Dracontopes on 2005-03-25
LOL, I got it working... Kernelmodule compiled okay after kernel-header upgrade :) I let update-modules put some lines in modules.conf and now nvsound is associated with snd-card-0. NVmixer is worky also and the sound is BETTER now, full bass etc. :) :)

A few questions:

Everytime Ubuntu loads, the system beeps a couple of times, I think saying it can't find a soundcard... How can I fix this?

Is it safe to disable ALSA from loading?

**Update:**

I disbabled ALSA with rcconf. No problem during boot. But now, during shutdown, I'm getting like 5 beeps, problems with soundcard... WTF?

**Update2:**

I renamed snd-intel9x0.ko to snd-intel.ko_backup so it is not loaded during startup. And the beeping stopped! :o [i][b]

Of course this is not a very nice sollution... Is there another way to stop snd-intel8x0 from loading?[/b][/i]

---

