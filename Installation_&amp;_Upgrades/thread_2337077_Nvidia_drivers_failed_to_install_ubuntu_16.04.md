---
title: "Nvidia drivers failed to install ubuntu 16.04"
date: 2016-09-14
forum: Installation &amp; Upgrades
---

### Post by bram1221 on 2016-09-14
Hey,

After a few how to`s i still cannot install the nvidia drivers. 
I have a laptop with 1070 so i need at least version 367


[http://www.yourownlinux.com/2016/06/how-to-install-nvidia-367-27-stable-graphics-drivers-in-linux.html](http://www.yourownlinux.com/2016/06/how-to-install-nvidia-367-27-stable-graphics-drivers-in-linux.html)
```
at /var/log/nvidia-installer.log 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Sep 14 07:04:05 2016
installer version: 370.28


PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games


nvidia-installer command line:
    ./nvidia-installer


Unable to load: nvidia-installer ncurses v6 user interface


Using: nvidia-installer ncurses user interface
-> Detected 8 CPUs online; setting concurrency level to 8.
-> License accepted.
-> Installing NVIDIA driver version 370.28.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Are you sure you want to continue? (Answer: Continue installation)
-> Would you like to register the kernel module sources with DKMS? This will allow DKMS to automatically build a new module, if you install a different kernel later. (Answer: Yes)
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility libraries? (Answer: Yes)
-> Will install GLVND GLX client libraries.
Looking for install checker script at ./libglvnd_install_checker/check-libglvnd-install.sh
   executing: '/bin/sh ./libglvnd_install_checker/check-libglvnd-install.sh'...
   Checking for libglvnd installation.
   Checking libGLdispatch...
   Can't load library libGLdispatch.so.0: libGLdispatch.so.0: cannot open shared object file: No such file or directory
Will install libglvnd libraries.
-> Searching for conflicting files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (370.28):
   executing: '/sbin/ldconfig'...
-> done.
-> Driver file installation is complete.
-> Installing DKMS kernel module:
```

At this point i can wait 10min but nothing happend so i have to abort the installation and uninstall everything.


[https://sites.google.com/site/easylinuxtipsproject/12](https://sites.google.com/site/easylinuxtipsproject/12)

```
etting up nvidia-prime (0.8.2) ...Setting up nvidia-367 (367.44-0ubuntu0~gpu16.04.1) ...
INFO:Enable nvidia-367
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Removing old nvidia-367-367.44 DKMS files...


------------------------------
Deleting module version: 367.44
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-367-367.44 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-36-generic
Building for architecture x86_64
Building initial module for 4.4.0-36-generic

```

At this point i can wait 10min but nothing happend so i have to abort the installation and uninstall everything.
Can someone help me to install this driver ?

---

### Post by ubfan1 on 2016-09-14
Did you try installing the Nvidia drivers from the "Software Updater"/Settings button/Additional Drivers tab , then select the Nvidia driver you want (try the tested one first).?

---

### Post by Bashing-om on 2016-09-14
bram1221; Hello;

The 367 driver is available to us from our trusted PPA:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Once the source is installed, and system updated .. my experience is that "autoinstall" will install the 370 driver - that may work very well for your use case. OR one can explicitly direct to install the 367 version.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by bram1221 on 2016-09-15
> **ubfan1 said:**
> Did you try installing the Nvidia drivers from the "Software Updater"/Settings button/Additional Drivers tab , then select the Nvidia driver you want (try the tested one first).?

I`m using gnome3 

> **Bashing-om] [COLOR=#000000]bram1221 said:**
> 

[COLOR=#000000]The 367 driver is available to us from our trusted PPA:[/COLOR]
[https://launchpad.net/~graphics-driv...ive/ubuntu/ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa")

[COLOR=#000000]Once the source is installed, and system updated .. my experience is that "autoinstall" will install the 370 driver - that may work very well for your use case. OR one can explicitly direct to install the 367 version.
[/COLOR]
[COLOR=#000000]my bit to try and help[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#000000]
Look at the log below. Its not going futher then [/COLOR]Building initial module for 4.4.0-36-generic[COLOR=#000000]
[/COLOR]
```
Username@Computer:/home/Username# apt-cache showpkg nvidia-367Package: nvidia-367
Versions: 
367.44-0ubuntu0~gpu16.04.1 (/var/lib/apt/lists/ppa.launchpad.net_graphics-drivers_ppa_ubuntu_dists_xenial_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/ppa.launchpad.net_graphics-drivers_ppa_ubuntu_dists_xenial_main_binary-amd64_Packages
                  MD5: db73425c039b8373769e4e913811c2f4
 Description Language: en
                 File: /var/lib/apt/lists/ppa.launchpad.net_graphics-drivers_ppa_ubuntu_dists_xenial_main_i18n_Translation-en
                  MD5: db73425c039b8373769e4e913811c2f4




Reverse Depends: 
  libcuda1-367,nvidia-367 367.44
  nvidia-367:i386,nvidia-367
  nvidia-opencl-icd-367,nvidia-367 367.44
  nvidia-367-dev,nvidia-367 367.44
Dependencies: 
367.44-0ubuntu0~gpu16.04.1 - x11-common (2 1:7.0.0) make (0 (null)) sed (4 3.0) dkms (0 (null)) linux-libc-dev (0 (null)) libc6-dev (0 (null)) patch (0 (null)) acpid (0 (null)) lib32gcc1 (0 (null)) libc6-i386 (0 (null)) passwd (0 (null)) adduser (0 (null)) libc6 (2 2.2.5) libgl1 (0 (null)) libwayland-client0 (2 1.3.92) libwayland-server0 (2 1.2.0) libx11-6 (0 (null)) libxext6 (0 (null)) xorg-video-abi-11 (16 (null)) xorg-video-abi-12 (16 (null)) xorg-video-abi-13 (16 (null)) xorg-video-abi-14 (16 (null)) xorg-video-abi-15 (16 (null)) xorg-video-abi-18 (16 (null)) xorg-video-abi-19 (16 (null)) xorg-video-abi-20 (0 (null)) xserver-xorg-core (0 (null)) nvidia-persistenced (0 (null)) nvidia-persistenced:i386 (0 (null)) xorg-driver-binary (0 (null)) xorg-driver-binary:i386 (0 (null)) nvidia-settings (2 331.20) nvidia-prime (18 0.5) bumblebee (0 (null)) libcuda1-367 (0 (null)) nvidia-opencl-icd-367 (0 (null)) nvidia-persistenced (0 (null)) nvidia-persistenced:i386 (0 (null)) xorg-driver-binary (0 (null)) xorg-driver-binary:i386 (0 (null)) nvidia-367:i386 (32 (null)) 
Provides: 
367.44-0ubuntu0~gpu16.04.1 - xorg-driver-video (= ) xorg-driver-binary (= ) nvidia-persistenced (= ) nvidia-driver-binary (= ) 
Reverse Provides: 
Username@Computer:/home/Username# apt-get install nvidia-367
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libcuda1-367 nvidia-opencl-icd-367 nvidia-prime nvidia-settings
The following NEW packages will be installed:
  libcuda1-367 nvidia-367 nvidia-opencl-icd-367 nvidia-prime nvidia-settings
0 upgraded, 5 newly installed, 0 to remove and 90 not upgraded.
Need to get 2699 kB/76,1 MB of archives.
After this operation, 342 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 libcuda1-367 amd64 367.44-0ubuntu0~gpu16.04.1 [2699 kB]
Fetched 2699 kB in 0s (3123 kB/s)       
Selecting previously unselected package nvidia-367.
(Reading database ... 200801 files and directories currently installed.)
Preparing to unpack .../nvidia-367_367.44-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-367 (367.44-0ubuntu0~gpu16.04.1) ...
Selecting previously unselected package libcuda1-367.
Preparing to unpack .../libcuda1-367_367.44-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking libcuda1-367 (367.44-0ubuntu0~gpu16.04.1) ...
Selecting previously unselected package nvidia-opencl-icd-367.
Preparing to unpack .../nvidia-opencl-icd-367_367.44-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-opencl-icd-367 (367.44-0ubuntu0~gpu16.04.1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.2_amd64.deb ...
Unpacking nvidia-prime (0.8.2) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_370.28-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-settings (370.28-0ubuntu0~gpu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up nvidia-367 (367.44-0ubuntu0~gpu16.04.1) ...
update-alternatives: using /usr/lib/nvidia-367/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-367/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-367/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
INFO:Enable nvidia-367
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 123) ...
Adding new group `nvidia-persistenced' (GID 131) ...
Adding new user `nvidia-persistenced' (UID 123) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-367-367.44 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-36-generic
Building for architecture x86_64
Building initial module for 4.4.0-36-generic



```

---

### Post by Bashing-om on 2016-09-15
bram1221; Welll ..

Yeah something just ain't right .
What have we installed that might cause a conflict ?
show :
```

sudo find / -name "NVIDIA-Linux-*"
dpkg -l | grep -i nvidia
lsmod | grep nvidia
dkms status

``` and we consider what it will take to purge nVidia, and try to install again on a fresh slate.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by bram1221 on 2016-09-19
> **Bashing-om said:**
> bram1221; Welll ..

```

sudo find / -name "NVIDIA-Linux-*"
dpkg -l | grep -i nvidia
lsmod | grep nvidia
dkms status

```


```
root@Username-laptop:/home/Username# find / -name "NVIDIA-Linux-*"/home/Username/Downloads/NVIDIA-Linux-x86_64-367.27.run
/home/Username/Downloads/NVIDIA-Linux-x86_64-370.28.run
find: ‘/run/user/1000/gvfs’: Permission denied
/etc/NVIDIA-Linux-x86_64-367.27.run
/etc/NVIDIA-Linux-x86_64-370.28.run
root@Username-laptop:/home/Username# dpkg -l | grep -i nvidia
ii  bbswitch-dkms                               0.8-3ubuntu1                                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
rc  nvidia-367                                  367.44-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA binary driver - version 367.44
rc  nvidia-opencl-icd-367                       367.44-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA OpenCL ICD
rc  nvidia-prime                                0.8.2                                                       amd64        Tools to enable NVIDIA's Prime
rc  nvidia-settings                             370.28-0ubuntu0~gpu16.04.1                                  amd64        Tool for configuring the NVIDIA graphics driver
root@Username-laptop:/home/Username# lsmod | grep nvidia
root@Username-laptop:/home/Username# dkms status
bbswitch, 0.8, 4.4.0-36-generic, x86_64: installed
i915-4.6.3-4.4.0, 1, 4.4.0-31-generic, x86_64: installed
i915-4.6.3-4.4.0, 1, 4.4.0-36-generic, x86_64: installed
root@Username-laptop:/home/Username# 



```

---

### Post by Bashing-om on 2016-09-19
bram1221; Hey ...

Look'n promise'n .
We know that you have attempted a install of the driver from nVidia. while doable it is not recommended - can be a pain to maintain .
We can see that no driver is available for the nVidia card : marked "rc" .
What I propose is to remove the OEM attempt, remove bbswitch-dkms ( insure that BumbleBee is not installed) and 
 Let's go with a driver from our PPA - If this card is a late build - that will be maintained by the system.

So now the question is ... what driver to install ?
Post back the results:
```

lspci -k | grep -EA2 'VGA|3D' 

```
and I will match the card to the proper recommended driver. ( we can also accept what the system thinks is the better driver, from what we set up to choose from ) 


[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by bram1221 on 2016-09-20
```
[sudo] password for Username: root@Username-laptop:/home/Username# lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
	DeviceName:  Onboard IGD
	Subsystem: CLEVO/KAPOK Computer Skylake Integrated Graphics
--
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1be1 (rev a1)
	Subsystem: CLEVO/KAPOK Computer Device 6a03
	Kernel modules: nvidiafb, nouveau
root@Username-laptop:/home/Username# dpkg -l | grep -i bumble
root@Username-laptop:/home/Username# 

```

I have a nvidia 1070 card so if i`m right i need at least driver [COLOR=#000000][FONT=&quot]367

[/FONT][/COLOR]The other nvidia drivers are removed with --uninstall parameter otherwise the hole system wont start(restart loop xorg).

---

### Post by Bucky Ball on 2016-09-20
> **ubfan1 said:**
> Did you try installing the Nvidia drivers from the "Software Updater"/Settings button/Additional Drivers tab , then select the Nvidia driver you want (try the tested one first).?

Gnome 3 doesn't have the Additional Drivers GUI?

* After a bit of research, it appears it does. Easiest way to do it, or at least try, before getting elbow (or neck) deep in a terminal.

---

### Post by bram1221 on 2016-09-20
> **Bucky Ball said:**
> Gnome 3 doesn't have the Additional Drivers GUI?

* After a bit of research, it appears it does. Easiest way to do it, or at least try, before getting elbow (or neck) deep in a terminal.


Yeah i have found the option. I have select Using Nvidia Binary Driver version 367. 
When i`ll click on apply i see a blue bar. But after waiting 10min its not finished look at attachment. At this point i cannot see any progress.. Looks like its the same when i use apt-get install nvidia-367.

Edit: those are my running process right now:

```

[FONT=Verdana]root      1605  0.0  0.0  19868  1044 pts/4    S+   12:24   0:00 grep --color=auto dpkg
[/FONT][FONT=Verdana]root     31042  0.0  0.0  22640  8116 pts/6    SNs+ 11:51   0:00 /usr/bin/dpkg --status-fd 60 --configure nvidia-367:amd64 libcuda1-367:amd64 nvidia-opencl-icd-367:amd64 nvidia-prime:amd64 nvidia-settings:amd64[/FONT]
[FONT=Verdana]root     31043  0.0  0.0  10124  2184 pts/6    SN+  11:51   0:00 /bin/sh /var/lib/dpkg/info/nvidia-367.postinst configure[/FONT]

```

edit2:

less /var/log/apt/term.log

```

------ removed lines ------
Log started: 2016-09-20  11:51:08Selecting previously unselected package nvidia-367.
(Reading database ... 202344 files and directories currently installed.)
Preparing to unpack .../nvidia-367_367.44-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-367 (367.44-0ubuntu0~gpu16.04.1) ...
Selecting previously unselected package libcuda1-367.
Preparing to unpack .../libcuda1-367_367.44-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking libcuda1-367 (367.44-0ubuntu0~gpu16.04.1) ...
Selecting previously unselected package nvidia-opencl-icd-367.
Preparing to unpack .../nvidia-opencl-icd-367_367.44-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-opencl-icd-367 (367.44-0ubuntu0~gpu16.04.1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.2_amd64.deb ...
Unpacking nvidia-prime (0.8.2) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_370.28-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-settings (370.28-0ubuntu0~gpu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up nvidia-367 (367.44-0ubuntu0~gpu16.04.1) ...
update-alternatives: using /usr/lib/nvidia-367/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-367/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-367/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
INFO:Enable nvidia-367
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 124) ...
Adding new group `nvidia-persistenced' (GID 131) ...
Adding new user `nvidia-persistenced' (UID 124) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-367-367.44 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-36-generic
Building for architecture x86_64
Building initial module for 4.4.0-36-generic

```

Edit 3: Looks like its almost the same problem : [https://ubuntuforums.org/showthread.php?t=2324360&page=2](https://ubuntuforums.org/showthread.php?t=2324360&page=2)

cat /var/lib/dkms/nvidia-367/367.44/build/make.log
```
[FONT=Verdana]DKMS make.log for nvidia-367-367.44 for kernel 4.4.0-36-generic (x86_64)[/FONT][FONT=Verdana]Tue Sep 20 11:51:22 CEST 2016[/FONT]
[FONT=Verdana]make "CC=cc"  KBUILD_VERBOSE= -C /lib/modules/4.4.0-36-generic/build M=/var/lib/dkms/nvidia-367/367.44/build ARCH=x86_64 NV_KERNEL_SOURCES=/lib/modules/4.4.0-36-generic/build NV_KERNEL_OUTPUT=/lib/modules/4.4.0-36-generic/build NV_KERNEL_MODULES="nvidia nvidia-uvm nvidia-modeset nvidia-drm" INSTALL_MOD_DIR=kernel/drivers/video modules[/FONT]
[FONT=Verdana]make[1]: Entering directory '/usr/src/linux-headers-4.4.0-36-generic'[/FONT]
[FONT=Verdana]  SYMLINK /var/lib/dkms/nvidia-367/367.44/build/nvidia/nv-kernel.o[/FONT]
[FONT=Verdana]  SYMLINK /var/lib/dkms/nvidia-367/367.44/build/nvidia-modeset/nv-modeset-kernel.o[/FONT]
[FONT=Verdana] CONFTEST: remap_pfn_range[/FONT]
[FONT=Verdana] CONFTEST: follow_pfn[/FONT]
[FONT=Verdana] CONFTEST: INIT_WORK[/FONT]
[FONT=Verdana] CONFTEST: vmap[/FONT]
```

I only need the nvidia for HDMI / thunderbolt output :(
ore is there a workaround for this ? 

I have windows for the games and linux for work. So i dont have to install nvidia if thats not necessary

---

### Post by Bashing-om on 2016-09-20
bram1221; Yuk ...

Skylake and nVidia hybrid graphics, We may have a problem:
There is an open bug report on this issue that to this time has no resolution, 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516)

Do you think it applies to your situation ?

[INDENT][INDENT]not a perfect world
[/INDENT][/INDENT]

---

### Post by bram1221 on 2016-09-21
> **Bashing-om said:**
> bram1221; Yuk ...

Skylake and nVidia hybrid graphics, We may have a problem:
There is an open bug report on this issue that to this time has no resolution, 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516)

Do you think it applies to your situation ?[INDENT][INDENT]not a perfect world
[/INDENT]
[/INDENT]


He can install a driver i dont come so far. But yeah it can be related.

At this point i dont have any xorg.conf. When i create one with xorg -configure i`ll and up with a loop but thats possible because i cannot finishe any nvidia installation

This is my xorg when i create one:

```
Section "ServerLayout"    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection


Section "Module"
    Load  "glx"
EndSection


Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection


Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "WrappedFB"              # [<bool>]
        #Option     "GLXVBlank"              # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapLimit"              # <i>
        #Option     "AsyncUTSDFS"            # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # <i>
    Identifier  "Card0"
    Driver      "nouveau"
    BusID       "PCI:1:0:0"
EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection 
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection



```

Edit: Maby another question. Do i need the nvidia for thunderbolt and HDMI to work ?

---

### Post by Bucky Ball on 2016-09-21
> **bram1221 said:**
> Do i need the nvidia for thunderbolt and HDMI to work ?

If the HDMI and Thunderbolt connections are on the NVidia card and hanging out the back of your computer, yes, I imagine so. Without the drivers doubt the card is enabled.

---

### Post by bram1221 on 2016-09-21
Is there any way to find out ? 

```
# xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     60.02*+  59.93    47.99  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

# lshw -class display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: iomemory:2f0-2ef irq:127 memory:2ffe000000-2ffeffffff memory:60000000-6fffffff ioport:f000(size=64)

# lspci -vt
-[0000:00]-+-00.0  Intel Corporation Sky Lake Host Bridge/DRAM Registers
           +-01.0-[01]----00.0  NVIDIA Corporation Device 1be1
           +-02.0  Intel Corporation Skylake Integrated Graphics
           +-14.0  Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller
           +-14.2  Intel Corporation Sunrise Point-H Thermal subsystem
           +-16.0  Intel Corporation Sunrise Point-H CSME HECI #1
           +-17.0  Intel Corporation Sunrise Point-H SATA Controller [AHCI mode]
           +-1c.0-[02-6c]--
           +-1c.4-[6d]--+-00.0  Realtek Semiconductor Co., Ltd. Device 5287
           |            \-00.1  Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           +-1c.6-[6e]----00.0  Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter
           +-1f.0  Intel Corporation Sunrise Point-H LPC Controller
           +-1f.2  Intel Corporation Sunrise Point-H PMC
           +-1f.3  Intel Corporation Sunrise Point-H HD Audio
           \-1f.4  Intel Corporation Sunrise Point-H SMBus





```

---

### Post by Bashing-om on 2016-09-21
bram1221l Hey ,,,

I am of a mind to clean all out, and start again fresh, installing the 367 driver from our PPA. 
To clean :
```

sudo NVIDIA-Linux-x86_64-367.27.run --uninstall
sudo NVIDIA-Linux-x86_64-370.28.run --uninstall
sudo apt-get remove --purge nvidia* bbswitch-dkms
sudo rm /etc/X11/xorg.conf 

```

add our PPA to the sources:
```

sudo add-apt-repository ppa:graphics-drivers/ppa

```

and now reinstall:
```

sudo apt update
sudo apt install nvidia-367 bbswitch-dkms nvidia-settings nvidia-prime
sudo apt upgrade

```

Now see what our handy-work looks like:
```

sudo reboot

```

Now when you come back up IF all is not good, let's look then at what X thinks:
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]I am all for see'n
[INDENT][INDENT][INDENT]what might happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bram1221 on 2016-09-22
> **Bashing-om said:**
> bram1221l Hey ,,,


THanks for helping but the install dont get futher ill wait for 10min Building initial module for 4.4.0-38-generic

```
[sudo] password for Username: root@Username-laptop:/home/Username# cd /etc/
root@Username-laptop:/etc# NVIDIA-Linux-x86_64-367.27.run --uninstall
NVIDIA-Linux-x86_64-367.27.run: command not found
root@Username-laptop:/etc# ./NVIDIA-Linux-x86_64-367.27.run --uninstall
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 367.27.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
root@Username-laptop:/etc# ./NVIDIA-Linux-x86_64-370.28.run --uninstall
bash: ./NVIDIA-Linux-x86_64-370.28.run: Permission denied
root@Username-laptop:/etc# chmod +x ./NVIDIA-Linux-x86_64-370.28.run
root@Username-laptop:/etc# ./NVIDIA-Linux-x86_64-370.28.run --uninstall
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 370.28..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
root@Username-laptop:/etc# apt-get remove --purge nvidia* bbswitch-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-325-updates' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note, selecting 'nvidia-331-dev' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-glx' for glob 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-370-dev' for glob 'nvidia*'
Note, selecting 'nvidia' for glob 'nvidia*'
Note, selecting 'nvidia-driver' for glob 'nvidia*'
Note, selecting 'nvidia-364-dev' for glob 'nvidia*'
Note, selecting 'nvidia-358-dev' for glob 'nvidia*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-686-pae' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-dev' for glob 'nvidia*'
Note, selecting 'nvidia-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-346-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-smi' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-prime' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia*'
Note, selecting 'nvidia-nsight' for glob 'nvidia*'
Note, selecting 'nvidia-common' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-amd64' for glob 'nvidia*'
Note, selecting 'nvidia-current-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia*'
Note, selecting 'nvidia-current' for glob 'nvidia*'
Note, selecting 'nvidia-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia*'
Note, selecting 'nvidia-367-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-dev' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-361-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note, selecting 'nvidia-355-dev' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-355' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-358' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-364' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-367' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-370' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-486' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-355' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-358' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-364' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-367' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-370' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304-dev' for glob 'nvidia*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304' for glob 'nvidia*'
Note, selecting 'nvidia-310' for glob 'nvidia*'
Note, selecting 'nvidia-313' for glob 'nvidia*'
Note, selecting 'nvidia-319' for glob 'nvidia*'
Note, selecting 'nvidia-325' for glob 'nvidia*'
Note, selecting 'nvidia-331' for glob 'nvidia*'
Note, selecting 'nvidia-334' for glob 'nvidia*'
Note, selecting 'nvidia-337' for glob 'nvidia*'
Note, selecting 'nvidia-340' for glob 'nvidia*'
Note, selecting 'nvidia-343' for glob 'nvidia*'
Note, selecting 'nvidia-346' for glob 'nvidia*'
Note, selecting 'nvidia-349' for glob 'nvidia*'
Note, selecting 'nvidia-352' for glob 'nvidia*'
Note, selecting 'nvidia-355' for glob 'nvidia*'
Note, selecting 'nvidia-358' for glob 'nvidia*'
Note, selecting 'nvidia-361' for glob 'nvidia*'
Note, selecting 'nvidia-364' for glob 'nvidia*'
Note, selecting 'nvidia-367' for glob 'nvidia*'
Note, selecting 'nvidia-370' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-vdpau-driver' is not installed, so not removed
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-glx' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-kernel-amd64' is not installed, so not removed
Package 'nvidia-kernel-686-pae' is not installed, so not removed
Package 'nvidia-kernel-486' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-smi' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-304-dev' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-304-updates-dev' is not installed, so not removed
Package 'nvidia-340-updates-uvm' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-dev' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-346-updates-dev' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-dev' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-352-updates-dev' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-361-updates-dev' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-dev' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-current-updates-dev' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-experimental-304-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-304' is not installed, so not removed
Package 'nvidia-opencl-icd-304-updates' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-libopencl1-304' is not installed, so not removed
Package 'nvidia-libopencl1-304-updates' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-346' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-persistenced' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-opencl-icd-331' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-340-updates-dev' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-340-updates' is not installed, so not removed
Package 'nvidia-355-dev' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-libopencl1-355' is not installed, so not removed
Package 'nvidia-opencl-icd-355' is not installed, so not removed
Package 'nvidia-358-dev' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-libopencl1-358' is not installed, so not removed
Package 'nvidia-opencl-icd-358' is not installed, so not removed
Package 'nvidia-361-dev' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-364-dev' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-libopencl1-364' is not installed, so not removed
Package 'nvidia-opencl-icd-364' is not installed, so not removed
Package 'nvidia-367-dev' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-370-dev' is not installed, so not removed
Package 'nvidia-370' is not installed, so not removed
Package 'nvidia-libopencl1-370' is not installed, so not removed
Package 'nvidia-opencl-icd-370' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386 libjansson4 libxnvctrl0 linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
  screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  bbswitch-dkms* nvidia-367* nvidia-opencl-icd-367* nvidia-prime* nvidia-settings*
0 upgraded, 0 newly installed, 5 to remove and 89 not upgraded.
After this operation, 36,9 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 234955 files and directories currently installed.)
Removing bbswitch-dkms (0.8-3ubuntu1) ...


-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.8
Kernel:  4.4.0-36-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.


-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.8
Kernel:  4.4.0-38-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-38-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.


------------------------------
Deleting module version: 0.8
completely from the DKMS tree.
------------------------------
Done.
Removing nvidia-367 (367.44-0ubuntu0~gpu16.04.1) ...
Purging configuration files for nvidia-367 (367.44-0ubuntu0~gpu16.04.1) ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-opencl-icd-367 (367.44-0ubuntu0~gpu16.04.1) ...
Purging configuration files for nvidia-opencl-icd-367 (367.44-0ubuntu0~gpu16.04.1) ...
Removing nvidia-prime (0.8.2) ...
Purging configuration files for nvidia-prime (0.8.2) ...
Removing nvidia-settings (370.28-0ubuntu0~gpu16.04.1) ...
Purging configuration files for nvidia-settings (370.28-0ubuntu0~gpu16.04.1) ...
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
root@Username-laptop:/etc# add-apt-repository ppa:graphics-drivers/ppa
 Fresh drivers from upstream, currently shipping Nvidia.


## Current Status


We currently recommend: `nvidia-367`, Nvidia's current long lived branch.
For GeForce 8 and 9 series GPUs use `nvidia-340`
For GeForce 6 and 7 series GPUs use `nvidia-304`


nvidia-370 is the current BETA release!


## What we're working on right now:


- Normal driver updates
- Investigating how to bring this goodness to distro on a cadence.


## WARNINGS:


This PPA is currently in testing, you should be experienced with packaging before you dive in here. Give us a few days to sort out the kinks.


Volunteers welcome! See also: https://github.com/mamarley/nvidia-graphics-drivers/


### How you can help:


## Install PTS and benchmark your gear:


    sudo apt-get install phoronix-test-suite


Run the benchmark:


    phoronix-test-suite default-benchmark openarena xonotic tesseract gputest unigine-valley


and then say yes when it asks you to submit your results to openbechmarking.org. Then grab a cup of coffee, it takes a bit for the benchmarks to run. Depending on the version of Ubuntu you're using it might preferable for you to grabs PTS from upstream directly: http://www.phoronix-test-suite.com/?k=downloads


## Share your results with the community:


Post a link to your results (or any other feedback to): https://launchpad.net/~graphics-drivers-testers


Remember to rerun and resubmit the benchmarks after driver upgrades, this will allow us to gather a bunch of data on performance that we can share with everybody.


If you run into old documentation referring to other PPAs, you can help us by consolidating references to this PPA.


If someone wants to go ahead and start prototyping on `software-properties-gtk` on what the GUI should look like, please start hacking!


## Help us Help You!


We use the donation funds to get the developers hardware to test and upload these drivers, please consider donating to the "community" slider on the donation page if you're loving this PPA:


http://www.ubuntu.com/download/desktop/contribute
 More info: https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpo81tfe_u/secring.gpg' created
gpg: keyring `/tmp/tmpo81tfe_u/pubring.gpg' created
gpg: requesting key 1118213C from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpo81tfe_u/trustdb.gpg: trustdb created
gpg: key 1118213C: public key "Launchpad PPA for Graphics Drivers Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
root@Username-laptop:/etc# apt update
Hit:1 http://nl.archive.ubuntu.com/ubuntu xenial InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                                     
Hit:3 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease                      
Hit:4 http://nl.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                       
Hit:5 http://nl.archive.ubuntu.com/ubuntu xenial-backports InRelease                                                     
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                                           
Hit:7 http://security.ubuntu.com/ubuntu xenial-security InRelease                                    
Get:9 https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease [3651 B]
Err:9 https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 56A3DEF863961D39
Hit:10 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease
Reading package lists... Done 
W: GPG error: https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 56A3DEF863961D39
E: The repository 'https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
root@Username-laptop:/etc# rm /etc/X11/xorg.conf
rm: cannot remove '/etc/X11/xorg.conf': No such file or directory
root@Username-laptop:/etc# apt install nvidia-367 bbswitch-dkms nvidia-settings nvidia-prime
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libcuda1-367 nvidia-opencl-icd-367
Suggested packages:
  bumblebee
The following NEW packages will be installed:
  bbswitch-dkms libcuda1-367 nvidia-367 nvidia-opencl-icd-367 nvidia-prime nvidia-settings
0 upgraded, 6 newly installed, 0 to remove and 89 not upgraded.
Need to get 0 B/76,1 MB of archives.
After this operation, 342 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Selecting previously unselected package nvidia-367.
(Reading database ... 234942 files and directories currently installed.)
Preparing to unpack .../nvidia-367_367.44-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-367 (367.44-0ubuntu0~gpu16.04.1) ...
Selecting previously unselected package libcuda1-367.
Preparing to unpack .../libcuda1-367_367.44-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking libcuda1-367 (367.44-0ubuntu0~gpu16.04.1) ...
Selecting previously unselected package nvidia-opencl-icd-367.
Preparing to unpack .../nvidia-opencl-icd-367_367.44-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-opencl-icd-367 (367.44-0ubuntu0~gpu16.04.1) ...
Selecting previously unselected package bbswitch-dkms.
Preparing to unpack .../bbswitch-dkms_0.8-3ubuntu1_amd64.deb ...
Unpacking bbswitch-dkms (0.8-3ubuntu1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.2_amd64.deb ...
Unpacking nvidia-prime (0.8.2) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_370.28-0ubuntu0~gpu16.04.1_amd64.deb ...
Unpacking nvidia-settings (370.28-0ubuntu0~gpu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up nvidia-367 (367.44-0ubuntu0~gpu16.04.1) ...
update-alternatives: using /usr/lib/nvidia-367/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-367/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-367/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
INFO:Enable nvidia-367
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 124) ...
Adding new group `nvidia-persistenced' (GID 131) ...
Adding new user `nvidia-persistenced' (UID 124) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-367-367.44 DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-38-generic
Building for architecture x86_64
Building initial module for 4.4.0-38-generic


Progress: [ 61%] [####################################################################################################################.........................................................................] 



```

---

### Post by Bucky Ball on 2016-09-22
> **Bashing-om said:**
> I am of a mind to clean all out, and start again fresh, installing the 367 driver from our PPA. 


Good idea. That initially probably would have avoided this. But hopefully its been a learning experience ...

---

### Post by bram1221 on 2016-09-22
Yup i did a fresh install ubuntu gnome and install nvidia. At this point everythings works great :)

Thanks

---

### Post by Bucky Ball on 2016-09-22
Excellent news and well persisted. :)

Please mark thread as solved to help others. See thread tools at top right or link in my signature. Good luck and enjoy.

---

