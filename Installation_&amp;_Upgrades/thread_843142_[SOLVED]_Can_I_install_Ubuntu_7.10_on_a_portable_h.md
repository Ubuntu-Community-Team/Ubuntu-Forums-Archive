---
title: "[SOLVED] Can I install Ubuntu 7.10 on a portable hard drive?"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Newuser1111 on 2008-06-28
Can I install Ubuntu 7.10 on a portable hard drive(USB)?

The portable hard drive contains 2 partitions right now,
1. 288GB NTFS which has a lot of my files that I do not want to lose.
2. 10GB HFS+ which has a broken and unused OS X.(Is bootable.)
Here's a picture to show it, [A link to the Image]("http://playstationportablestuff.googlepages.com/PARTITONS_124812481248124813248134.jpg")


And should I get a newer version than 7.10 if there is one?

---

### Post by Partyboi2 on 2008-06-28
Yes you can install to portable hard drive
[http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/)
[http://ubuntukids.org/blog/?p=69](http://ubuntukids.org/blog/?p=69)
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by Newuser1111 on 2008-06-28
Thanks but,
There might be a problem with the disk I'm using. Such as LiveCD crashes, doesn't install correctly, etc.
The disk does look dirty and has a few scratches.
I'll try burning the ISO to another CD-R then installing again.

---

### Post by Grizzlitiger on 2008-06-28
Hi,

yes you can install it on a portable usb hard drive but I would recommend not to, because booting from a usb drive is very prone to errors - I tried that out already but there are too many problems with it so I'd definitely recommend you not to as Ubuntu is quite small anyway, so you only need another small partition on your main drive anyway.

I'd also always recommend to get a long time support version as those are more stable. The latest one is 8.04.

---

### Post by Pumalite on 2008-06-28
You can install 8.04 to a 4 or 8 GB Pen Drive as if it were a hard drive.
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman+USB](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman+USB)
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[http://ubuntulinuxtipstricks.blogspot.com/2008/04/faq-hardy-upgrade.html](http://ubuntulinuxtipstricks.blogspot.com/2008/04/faq-hardy-upgrade.html)
[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

---

### Post by Newuser1111 on 2008-06-28
> **Grizzlitiger said:**
> I'd definitely recommend you not to as Ubuntu is quite small anyway, so you only need another small partition on your main drive anyway.
Vista won't let me make the Vista partition any smaller.

If it does have too many problems then I can take off XP.

---

### Post by Newuser1111 on 2008-06-28
There's a problem.

7.10 doesn't work (stops working on startup) and 7.04 has an error so far,

> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes> <No>(here's a picture[(link)](http://playstationportablestuff.googlepages.com/P1010002.JPG) of it.)
Should I choose Yes or No?

I chose Yes and now it says,
> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Ubuntu 2.6.20-15-generic #2 SMP Sun
Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
      Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
      to make sure you have the latest version.
Module Loader present
Markers (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 28 13:40:39 2008
(==) Using config file: "/etc/Z11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found.

<Ok>
Note: This was installed using a different computer than the one it's being ran on.

--Edit---
> **Pumalite said:**
> [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)I'll try that one, except #7 will be "manual" instead of "guided - use entire disk"

Now to wait for it to finish downloading, which it says will take 3 hours.

---

### Post by Partyboi2 on 2008-06-28
> 7.10 doesn't work (stops working on startup) and 7.04 has an error so far,

 	Quote:
 	 	 		 Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes> <No> 			 		7.10 doesn't work (stops working on startup) and 7.04 has an error so far,

 	Quote:
 	 	 		 Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes> <No> 			 		

What graphics card are you using?

---

### Post by Newuser1111 on 2008-06-28
> **Partyboi2 said:**
> What graphics card are you using?
The Windows Device Manager says it is:
NVIDIA GeForce 7000M / nForce 610M

Nvidia Control Panel says:
> NVIDIA System Information report created on: 06/28/2008 20:03:22
System name: DJK-PC

[Display]
Processor:		AMD Turion(tm) 64 X2 Mobile Technology TL-58 (1902 MHz)
Operating System:	Microsoft Windows Vista (Service Pack 1)
DirectX version:	10.0 
GPU processor:		GeForce 7000M / nForce 610M
ForceWare version:	156.66
Total available graphics memory:	799 MB
Dedicated video memory:	64 MB
System video memory:	0 MB
Shared system memory:	735 MB
Video BIOS version:	5.67.32.16.00
IRQ:			16

[Components]

nvCplUIR.dll		1.4.200.11		NVIDIA Control Panel
nvCpl.cpl		1.4.200.11		NVIDIA Control Panel Applet
nvExpBar.dll		1.4.200.11		NVIDIA Control Panel
nvCplUI.exe		1.4.200.11		NVIDIA Control Panel
nvViTvSR.dll		7.15.11.5666		NVIDIA Video and TV Server
nvViTvS.dll		7.15.11.5666		NVIDIA Video and TV Server
nvDispSR.dll		7.15.11.5666		NVIDIA Display Server
NVMCTRAY.DLL		7.15.11.5666		NVIDIA Media Center Library
nvDispS.dll		7.15.11.5666		NVIDIA Display Server
NVCPL.DLL		7.15.11.5666		NVIDIA Compatible Windows 2000 Display driver, Version 156.66 
nvGameSR.dll		7.15.11.5666		NVIDIA 3D Settings Server
nvGameS.dll		7.15.11.5666		NVIDIA 3D Settings Server

So it has something to do with my graphics card? Not my CD?

---

### Post by Partyboi2 on 2008-06-28
Try using safe graphics mode to install (option 2)
If that does not work when you get to the part where it is giving you the error message press Ctrl+Alt+F2 to get to a terminal then type
```
sudo dpkg-reconfigure xserver-xorg
``` choose  nv  for graphics and work your way through the questions choosing the default answers if unsure. 
then type
```
startx
```If  nv  does not work you will need to redo and choose vesa. Hopefully this will get you to a working desktop where you can install the correct driver for your card.

Edit: Another option could be to try using the alternate cd

---

### Post by Newuser1111 on 2008-06-29
> **Partyboi2 said:**
> Try using safe graphics mode to install (option 2)
If that does not work when you get to the part where it is giving you the error message press Ctrl+Alt+F2 to get to a terminal then type
```
sudo dpkg-reconfigure xserver-xorg
``` choose  nv  for graphics and work your way through the questions choosing the default answers if unsure. 
then type
```
startx
```If  nv  does not work you will need to redo and choose vesa. Hopefully this will get you to a working desktop where you can install the correct driver for your card.

Edit: Another option could be to try using the alternate cdI press Ctrl+Alt+F2 and it then it says "ubuntu login:" and it won't let me log in no matter what username and password I try.
I did use the 7.04 Alternate CD.
I'll try re-installing it, something must have gone wrong during the setup.

---

### Post by Partyboi2 on 2008-06-29
If you have already install ubuntu, boot into recovery mode and
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Newuser1111 on 2008-06-29
> **Newuser1111 said:**
> I press Ctrl+Alt+F2 and it then it says "ubuntu login:" and it won't let me log in no matter what username and password I try.
I did use the 7.04 Alternate CD.
I'll try re-installing it, something must have gone wrong during the setup.
Somehow, I skipped the part of user setup and the clock on the previous install.

Didn't see that other reply before,
I've already started reinstalling. It might be almost done.(92%)

Edit: It's finished installing and now I can login.

So far "startx" still doesn't work.

Edit: Ok, now it's at the desktop. (vesa worked)

Edit: WiFi doesn't work and how do I get the right driver for NVIDIA?
Edit: Got it connected to the internet using Ethernet, I would prefer WiFi as soon as possible.

Trying to use the driver I got from here:
[http://www.nvidia.com/object/linux_display_ia32_173.14.09.html](http://www.nvidia.com/object/linux_display_ia32_173.14.09.html)

I got this error:
>   ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).


---

### Post by Partyboi2 on 2008-06-29
System>Admin>Restricted DriversFor your nvidia problem try enabling the restricted driver under.
If that does not work there are another 2 options.
1. Download the driver directly from [[COLOR=Blue]Nvidia[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and install it or
2. Use [[COLOR=Blue]envy[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html") to install the driver. (easiest)

To find out what wireless card you are using, open a terminal (Applications>Accessories>Terminal) and type
```
lspci -v | less
```Look through the list for your wireless details
If you are using a usb wireless device use
```
lsusb
```

---

### Post by Partyboi2 on 2008-06-29
> I got this error:
 	Quote:
 	 	 		 			 				  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com/"). 			 		

Boot into recovery mode and install it from there.

---

### Post by Newuser1111 on 2008-06-29
The driver from restricted drivers manager doesn't work, Now it's just at a black screen after startup.

Recovery mode, the driver's setup had some errors.


So how can I undo what the Restricted Drivers Manager did?

---

### Post by Partyboi2 on 2008-06-29
Make sure you have build-essential package installed.
```
sudo apt-get install build-essential
```
then try install it from recovery mode again. Let us know what the errors are.

---

### Post by Partyboi2 on 2008-06-29
Go back to the restricted drivers (System>Admin>Restricted Drivers) and untick the box.

---

### Post by Newuser1111 on 2008-06-29
> **Partyboi2 said:**
> Make sure you have build-essential package installed.
```
sudo apt-get install build-essential
```
then try install it from recovery mode again. Let us know what the errors are.It won't accept my CD.
> Media change: please insert the disc labeled
'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in drive '/cdrom/' and press enter
I put the CD in and when I press enter, it just asks again.

And
> **Partyboi2 said:**
> Go back to the restricted drivers (System>Admin>Restricted Drivers) and untick the box.How can I do that without getting back into startx(which just gives the black screen.)?

---

### Post by Partyboi2 on 2008-06-29
> How can I do that without getting back into startx(which just gives the black screen.)?                                                                                     Boot into recovery mode and reconfigure the xserver again choosing vesa
```
dpkg-reconfigure xserver-xorg
```then 
```
startx
```Once you get to a working desktop go to Software Sources  (System>Admin>Software Sources) on the first tab (ubuntu software) make sure all are ticked except source code Then Under "Installable from cd-rom/dvd untick the cdrom box. 
After you have closed the window and it has updated the sources.list, go back to a terminal and install build-essential
```
sudo apt-get install build-essential
```Once it has installed restart your system into recovery mode then download the nvidia driver
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/NVIDIA-Linux-x86-173.14.09-pkg1.run

``` After it has downloaded start the installer
```
sh NVIDIA-Linux-x86-173.14.09-pkg1.run                              
```
after the install, reconfigure xserver but this time choose nvidia
```
dpkg-reconfigure xserver-xorg
``` Then 
```
startx
```or
reboot

---

### Post by Newuser1111 on 2008-06-29
Still doesn't work.


I got wifi working by following some instructions from another thread but I still can't get Nvidia working.

[QUOTE=Partyboi2]System>Admin>Restricted DriversFor your nvidia problem try enabling the restricted driver under.
If that does not work there are another 2 options.
1. Download the driver directly from Nvidia and install it or
2. Use envy to install the driver. (easiest)[/QUOTE]None of those worked.
Envy just made X server stop working.

So is there anything else I can do?

---

### Post by Newuser1111 on 2008-06-29
Will Ubuntu 8.04 help?

---

### Post by upchucky on 2008-06-29
I have a usb 160 gig drive that i use to install and test different linux flavors, atm it has 7.10 on it.

I had to use supergrub to get it working right, and manually edit the config files to get nvidia 6800 working.

at the moment I can boot from it or just use it to store stuff as it also auto mounts when I dont boot from it.

---

### Post by Newuser1111 on 2008-06-29
It's installed fine, just having problems with my laptop's hardware(drivers).

---

### Post by Newuser1111 on 2008-06-30
Is anyone going to help?

> Still doesn't work.


I got wifi working by following some instructions from another thread but I still can't get Nvidia working.

[QUOTE]Originally Posted by Partyboi2
System>Admin>Restricted DriversFor your nvidia problem try enabling the restricted driver under.
If that does not work there are another 2 options.
1. Download the driver directly from Nvidia and install it or
2. Use envy to install the driver. (easiest)
None of those worked.
Envy just made X server stop working.

So is there anything else I can do?[/QUOTE]
> Will Ubuntu 8.04 help?

---

### Post by Partyboi2 on 2008-06-30
Have a look at /var/log/nvidia-installer.log for why its not installing.

---

### Post by Newuser1111 on 2008-06-30
> **Partyboi2 said:**
> Have a look at /var/log/nvidia-installer.log for why its not installing.
This is what it says,
> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Jun 29 14:35:05 2008
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
-> Installing NVIDIA driver version 173.14.09.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.20-15-generic/build'
-> Kernel output path: '/lib/modules/2.6.20-15-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.20-15-gener
   ic/build SYSOUT=/lib/modules/2.6.20-15-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.20-15-generic/build SUBDIRS
   =/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tmp_ver
   sions
   rm -f /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tmp_versio
   ns/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.0
   9-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL
   __ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wun
   def -Wstrict-prototypes -Wno-
   trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=
   3 -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -m
   accumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-poin
   ter -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign
   -I/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv -Wall -Wimplici
   t -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-
   arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error 
   -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.09\" -UDEBUG -U_DE
   BUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv
   )"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6062/NVIDIA-Linux
   -x86-173.14.09-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz6062/NVIDIA-Linux-x86-17
   3.14.09-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KER
   NEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -
   Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -
   O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586 
   -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i38
   6/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-a
   fter-statement -Wno-pointer-sign -I/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.0
   9
   -pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-sub
   scripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-co
   mpare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_ST
   RING=\"173.14.09\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" 
   -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"
   -c -o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tmp_nv-vm.
   o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KE
   RNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586
   -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i38
   6/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-a
   fter-statement -Wno-pointer-sign -I/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.0
   9-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-su
   bscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"173.14.09\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s"
   -D"KBUILD_BASENAME=KBUILD_STR(os
   _agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6062/NVIDIA-L
   inux-x86-173.14.09-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz6062/NVIDIA-Linu
   x-x86-173.14.09-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include 
   -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  
   -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-c
   ommon -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -marc
   h=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/
   asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclar
   ation-after-statement -Wno-pointer-sign -I/tmp/selfgz6062/NVIDIA-Linux-x86-1
   73.14.09-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -W
   char-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -
   Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VE
   RSION_STRING=\"173.14.09\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR
   (s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUI
   LD_STR(nvidia)" -c -o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/.tmp_os-interface.o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr
   /src/nv/os-interface.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -
   D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march
   =i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/a
   sm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclara
   tion-after-statement -Wn
   o-pointer-sign -I/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv 
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-q
   ual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.09\
   " -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAM
   E=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp
   /selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tmp_os-registry.o /t
   mp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KE
   RNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586
   -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i38
   6/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-a
   fter-statement -Wno-pointer-sign -I/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.0
   9-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-su
   bscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"173.14.09\" -UDEBU
   G -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD
   _STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6062/N
   VIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz6062/NVID
   IA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KE
   RNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586
   -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i38
   6/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-a
   fter-statement -Wno-pointer-sign -I/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.0
   9-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-su
   bscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-c
   ompare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_S
   TRING=\"173.14.09\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s"
   -D"KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)
   " -c -o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tmp_nvac
   pi.o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -m elf_i386 -m elf_i386  -r -o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.
   09-pkg1/usr/src/nv/nvidia.o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/
   usr/src/nv/nv-kernel.o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/s
   rc/nv/nv.o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv-vm.
   o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/os-agp.o /tmp/s
   elfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/os-interface.o /tmp/sel
   fgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/
   nv/os-registry.o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/
   nv-i2c.o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nvacpi.o
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.20-15-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.20-15-generic/Modu
   le.symvers -I /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/Mod
   ule.symvers -o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/Mo
   dule.symvers -w  /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/
   nvidia.o
   WARNING: could not find /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D
   __KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -W
   all -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-
   strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred-s
   tack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outg
   oing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-st
   ack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_S
   TR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUI
   LD_STR(nvidia)" -DMODULE -c -o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pk
   g1/usr/src/nv/nvidia.mod.o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/u
   sr/src/nv/nvidia.mod.c
     ld -m elf_i386 -m elf_i386 -r -o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.0
   9-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/
   usr/src/nv/nvidia.o /tmp/selfgz6062/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/
   nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [   25.432000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
   [   25.432000] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
   [   25.432000] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
   [   32.092000] NET: Registered protocol family 17
   [   32.244000] ppdev: user-space parallel port driver
   [   32.908000] apm: BIOS not found.
   [   33.156000] Bluetooth: Core ver 2.11
   [   33.160000] NET: Registered protocol family 31
   [   33.160000] Bluetooth: HCI device and connection manager initialized
   [   33.160000] Bluetooth: HCI socket layer initialized
   [   33.188000] Bluetooth: L2CAP ver 2.8
   [   33.188000] Bluetooth: L2CAP socket layer initialized
   [   33.340000] Bluetooth: RFCOMM socket layer initialized
   [   33.340000] Bluetooth: RFCOMM TTY layer initialized
   [   33.340000] Bluetooth: RFCOMM ver 1.8
   [   34.164000] NET: Registered protocol family 10
   [   34.164000] lo: Disabled Privacy Extensions
   [   44.424000] eth2: no IPv6 routers present
   [   61.132000] NTFS driver 2.1.28 [Flags: R/O MODULE].
   [   61.132000] NTFS-fs warning (device sdb1): parse_options(): Option utf8
   is no longer supported, using option nls=utf8. Please use option nls=utf8 in
   the future and make sure utf8 is compiled either as a module or into the
   kernel.
   [   61.560000] NTFS volume version 3.1.
   [  650.180000] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
   [  650.180000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LGPU] -> GSI 16
   (level, low) -> IRQ 22
   [  650.184000] PCI: Setting latency timer of device 0000:00:12.0 to 64
   [  650.184000] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.09  Wed
   Jun  4 23:43:17 PDT 2008
-> Installing both new and classic TLS OpenGL libraries.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (173.14.09):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: N
   o)
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86
   (version: 173.14.09) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details.

---

### Post by chunchengch on 2008-06-30
> **Grizzlitiger said:**
> ... because booting from a usb drive is very prone to errors ...

I absolutely do not agree this.

I have Ubuntu 8.04 Chinese version installed on my ASUS laptop, and Ubuntu 8.04 English version installed on an old 10G portable HDD, both of them work perfectly.

I use my laptop for more than 12 hours everyday, so I build a portable Ubuntu to rescue data in case the laptop HDD breaks down one day.

---

### Post by upchucky on 2008-06-30
Just woke up, gettin brain unscrambled.

It looks like the nvidia driver is installed and the next step is to edit the xorg file. (as the output you posted here says edit the file that applies to your system, most are xorg.conf)
and is located in /etc/X11

I am posting my xorg here, dont try to use it as it is tweaked for my sys, yours will be a bit different but the basics are the same for settings

look for the screen and resolution settings.

do not edit the section that has "failsafe" this is where you get the lowest screen setting if and when you break your normal setting.
you can see where i have several mode selections hashed out #
you can try using them one at a time to find the ones that work.




# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"               "7"
        Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
#	Horizsync	31.5	-	64.0
#	Vertrefresh	56.0	-	65.0
	Gamma	1
######added from working xorg file on usb drive#####
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
######end of addition###################
#  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
#  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
#  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
#  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
#  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
#  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
	# 
	Identifier	"monitor1"
	Gamma	1
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
######added from my old working bery conf########
        Option          "UseFBDev"              "true"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "backingstore"          "true"
        Option          "AddARGBGLXVisuals"     "true"
        Option          "TripleBuffer"          "true"
######end of addition#####
	Screen	0
EndSection

Section "Device"
	# 
	Identifier	"device1"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
######added from my old working bery conf########
        Option          "UseFBDev"              "true"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "backingstore"          "true"
        Option          "AddARGBGLXVisuals"     "true"
        Option          "TripleBuffer"          "true"
######end of addition#####
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
#		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
                Modes      "1920x1200" "1024x678" "960x600" "840x600" "1280x960" "800x600"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Screen"
	# 
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

#######added from my working beryl conf########
Section "DRI"
        Mode    0666
EndSection
##########end of addition########

---

### Post by Newuser1111 on 2008-06-30
I tried editing it several times, still says that there's no screens.

---

### Post by upchucky on 2008-06-30
post your xorg.conf here

---

### Post by Newuser1111 on 2008-06-30
I got it working.

All I had to do was install Ubuntu 8.04.

---

