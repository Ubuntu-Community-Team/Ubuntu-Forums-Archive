---
title: "Login impossible after update"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by NHerby on 2014-12-30
Hi,

After a big KDE update including most of the Kxxxx apps, I cannot login anymore. After the login screen, I have a black screen with my mouse cursor and nothing else.

I started in recovery mode to launch KDE from command line but it fails:```
Fatal server error: Could not create lock file in /tmp/.tX0-lock  

xinit: giving up 
xinit: unable to connect to x server: Connection refused 
xinit: server error 
xauth error in locking authority file /root/.Xauthority
```
Tried to remove this folder ("rm -f /tmp/.tX0-lock") but no luck.
Also tried to delete .Xauthority. A new file is created after a login attempt but this didn't help either.
I really don't know what to do to get this fixed.

---

### Post by QIII on 2014-12-30
Did you mount the file system read/write from recovery?

---

### Post by NHerby on 2014-12-30
> **QIII said:**
> Did you mount the file system read/write from recovery?In recovery, I don't have RW access on the disk and don't know how to do to mount the system disk with RW access.
However, after a login attempt, I can use ctrl+alt+F2 then I have full access.

---

### Post by QIII on 2014-12-30
From the command line in recovery mode, issue the following:

```
mount -o remount,rw /
``` to mount read/write.

Then try

```
X -configure
``` and let us know what happens

---

### Post by MAFoElffen on 2014-12-30
Stop please... If you look at the error:
```

xauth error in locking authority file [COLOR=#ff0000]/root[/COLOR]/.Xauthority

```
There is not and should not be an .Xauthority file at that location. "*That*" is [COLOR=#ff0000]Not[/COLOR] an error. That is valid, but indicates another problem. The non-problem is that the user "root" does not have r/w access to any .Xauthority file so therefore does not have valid access to X. (..unless you explicitly add that manually, but not in the root directory!!!)

If you can't start X and there is an Xauth problem, that happens sometimes during updates. What is most common is that the update is done by root and when it reconfigs, the permissions on the User's /home/userName/.Xauthority sometimes msitakenly changes ownership to root.

Easy fix. At grub boot menu, recovery menu option. > At Recovery menu, Networking. That will also mount the filesystem. Then > select drop to root prompt.
```

cd /home/userName  # substitute the user's name to go to their home directory
rm ./.Xauthority
touch ./Xauthority
chmod 600 ./Xauthority
chown userName ./Xauthority # substitute username to change ownership to that user.
exit

```
Ownership and permissions will be set to that user. Continue to boot and you should be on your way. (fixed)

Sidenote for educational purposes: If you look at that file on a fresh new install, permissions are set to user r/w only, owner is user, no groups, no others.

---

### Post by NHerby on 2014-12-31
Unfortunately none of these solved the problem.
@[**[COLOR=#C61919][B]QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170")
Here's the return of "X -configure":
```
(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
    Configuration failed.
  ddxSigGiveUp: Closing log
Server terminated with error (2). Closing log file.
```
@[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1044547")
I did follow step by step your instructions but this had no effect.
The >Xauthority file in my home folder is -rw------- and is owned by myself.

BTW, forgot to mention that I have Kubuntu 12.04.5 LTS, KDE 4.8.2.

I have backup of my /home directory, /etc directory and the list of installed paquets so I'm wondering if it will not be easier/faster to reinstall everything and move to 14.04LTS at the same time. I didn't want to upgrade before since this system was very stable; but now...

---

### Post by QIII on 2014-12-31
Good catch MAFoElffen.

Didn't see that.  Old eyes.

---

### Post by MAFoElffen on 2014-12-31
With that error, please post your /var/log/Xorg.0.log file, that should show the cards, connected monitors and their responses back to the cards...

---

### Post by Bashing-om on 2014-12-31
et al;  Look'n 

At:
> 
cd /home/userName  # substitute the user's name to go to their home directory
rm ./.Xauthority
touch ./Xauthority
chmod 600 ./Xauthority
chown userName ./Xauthority # substitute username to change ownership to that user.
exit


Should not the file be a hidden file, such that the above is:
```

cd /home/userName  # substitute the user's name to go to their home directory
rm ./.Xauthority
touch ./.Xauthority
chmod 600 ./.Xauthority
chown userName ./.Xauthority # substitute username to change ownership to that user.
exit

```
@NHerby; for reference:
```

sysop@1404mini:~$ ls -al ./.Xauthority
-rw------- 1 sysop sysop 209 Aug  1 10:10 ./.Xauthority
sysop@1404mini:~$

```

[INDENT][INDENT]that silly little dot
[INDENT][INDENT][INDENT][INDENT]oh so significant
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MAFoElffen on 2014-12-31
Thankx... was my typo. But it looked like the OP caught that also and that wasn't the problem.

The error now is that X is reporting:
```

Number of created screens does not match number of detected devices.

```
Which is either a problem caused when the OP did the X config (xorg.conf error) or a problem with the hardware reporting between themselves on the hardware probe that Xorg does when it int's. That is a bit strange... as the X config would have probed that same hardware to create the xorg.conf. Not sure how that would change between that and now. (Should stil be the same, but something is still not right with that.)

The Xorg.0.log should show the problem there.... It also will show what hardware is present, what they are ID'ed as... what the xorg.conf is saying and how it's being interpreted.

---

### Post by NHerby on 2015-01-01
Just made a try with "that silly little dot":
```
herby@PC:~$  ls -al ./.Xauthority
-rw------- 1 herby herby 157 janv.  1 04:46  ./.Xauthority
```But this didn't help.

Here's the Xorg.0.log :

```
[    24.310] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    24.310] X Protocol Version 11, Revision 0
[    24.310] Build Operating System: Linux 2.6.42-70-generic x86_64 Ubuntu
[    24.310] Current Operating System: Linux PC 3.2.0-74-generic #109-Ubuntu SMP Tue Dec 9 16:45:49 UTC 2014 x86_64
[    24.310] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-74-generic root=UUID=4a037356-fc26-4437-a796-815c8dd2d1fe ro quiet splash
[    24.310] Build Date: 09 December 2014  11:10:55PM
[    24.310] xorg-server 2:1.11.4-0ubuntu10.16 (For technical support please see http://www.ubuntu.com/support) 
[    24.310] Current version of pixman: 0.30.2
[    24.310]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.310] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.310] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan  1 04:46:24 2015
[    24.310] (==) Using config file: "/etc/X11/xorg.conf"
[    24.310] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.310] (==) ServerLayout "Layout0"
[    24.310] (**) |-->Screen "Screen0" (0)
[    24.310] (**) |   |-->Monitor "Monitor0"
[    24.310] (**) |   |-->Device "Device0"
[    24.310] (**) |-->Screen "Screen1" (1)
[    24.310] (**) |   |-->Monitor "Monitor1"
[    24.310] (**) |   |-->Device "Device1"
[    24.310] (**) |-->Input Device "Keyboard0"
[    24.310] (**) |-->Input Device "Mouse0"
[    24.310] (**) Option "Xinerama" "0"
[    24.310] (==) Automatically adding devices
[    24.310] (==) Automatically enabling devices
[    24.310] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.310]     Entry deleted from font path.
[    24.310] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.310]     Entry deleted from font path.
[    24.310] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.310]     Entry deleted from font path.
[    24.310] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.310]     Entry deleted from font path.
[    24.310] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.310]     Entry deleted from font path.
[    24.310] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    24.310]     Entry deleted from font path.
[    24.310] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    24.310] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.310] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    24.310] (WW) Disabling Keyboard0
[    24.310] (WW) Disabling Mouse0
[    24.310] (II) Loader magic: 0x7fb67e13bb00
[    24.310] (II) Module ABI versions:
[    24.310]     X.Org ANSI C Emulation: 0.4
[    24.310]     X.Org Video Driver: 11.0
[    24.310]     X.Org XInput driver : 16.0
[    24.310]     X.Org Server Extension : 6.0
[    24.311] (--) PCI:*(0:1:0:0) 10de:1183:1043:841f rev 161, Mem @ 0xf6000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    24.311] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.311] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    24.311] (II) "extmod" will be loaded by default.
[    24.311] (II) "dbe" will be loaded by default.
[    24.311] (II) "glx" will be loaded by default.
[    24.311] (II) "record" will be loaded by default.
[    24.311] (II) "dri" will be loaded by default.
[    24.311] (II) "dri2" will be loaded by default.
[    24.311] (II) LoadModule: "extmod"
[    24.315] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.315] (II) Module extmod: vendor="X.Org Foundation"
[    24.315]     compiled for 1.11.3, module version = 1.0.0
[    24.315]     Module class: X.Org Server Extension
[    24.315]     ABI class: X.Org Server Extension, version 6.0
[    24.315] (II) Loading extension MIT-SCREEN-SAVER
[    24.315] (II) Loading extension XFree86-VidModeExtension
[    24.315] (II) Loading extension XFree86-DGA
[    24.315] (II) Loading extension DPMS
[    24.315] (II) Loading extension XVideo
[    24.315] (II) Loading extension XVideo-MotionCompensation
[    24.315] (II) Loading extension X-Resource
[    24.315] (II) LoadModule: "dbe"
[    24.315] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.315] (II) Module dbe: vendor="X.Org Foundation"
[    24.315]     compiled for 1.11.3, module version = 1.0.0
[    24.315]     Module class: X.Org Server Extension
[    24.315]     ABI class: X.Org Server Extension, version 6.0
[    24.315] (II) Loading extension DOUBLE-BUFFER
[    24.315] (II) LoadModule: "glx"
[    24.315] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    24.990] (II) Module glx: vendor="NVIDIA Corporation"
[    24.990]     compiled for 4.0.2, module version = 1.0.0
[    24.990]     Module class: X.Org Server Extension
[    24.990] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    24.990] (II) Loading extension GLX
[    24.990] (II) LoadModule: "record"
[    24.990] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.990] (II) Module record: vendor="X.Org Foundation"
[    24.990]     compiled for 1.11.3, module version = 1.13.0
[    24.990]     Module class: X.Org Server Extension
[    24.990]     ABI class: X.Org Server Extension, version 6.0
[    24.990] (II) Loading extension RECORD
[    24.990] (II) LoadModule: "dri"
[    24.990] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.991] (II) Module dri: vendor="X.Org Foundation"
[    24.991]     compiled for 1.11.3, module version = 1.0.0
[    24.991]     ABI class: X.Org Server Extension, version 6.0
[    24.991] (II) Loading extension XFree86-DRI
[    24.991] (II) LoadModule: "dri2"
[    24.991] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.991] (II) Module dri2: vendor="X.Org Foundation"
[    24.991]     compiled for 1.11.3, module version = 1.2.0
[    24.991]     ABI class: X.Org Server Extension, version 6.0
[    24.991] (II) Loading extension DRI2
[    24.991] (II) LoadModule: "nvidia"
[    24.991] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    25.175] (II) Module nvidia: vendor="NVIDIA Corporation"
[    25.175]     compiled for 4.0.2, module version = 1.0.0
[    25.175]     Module class: X.Org Video Driver
[    25.175] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    25.175] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    25.175] (++) using VT number 8

[    25.186] (II) Loading sub module "fb"
[    25.186] (II) LoadModule: "fb"
[    25.186] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.186] (II) Module fb: vendor="X.Org Foundation"
[    25.186]     compiled for 1.11.3, module version = 1.0.0
[    25.186]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.186] (II) Loading sub module "wfb"
[    25.186] (II) LoadModule: "wfb"
[    25.186] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    25.186] (II) Module wfb: vendor="X.Org Foundation"
[    25.186]     compiled for 1.11.3, module version = 1.0.0
[    25.186]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.186] (II) Loading sub module "ramdac"
[    25.186] (II) LoadModule: "ramdac"
[    25.186] (II) Module "ramdac" already built-in
[    25.186] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    25.186] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    25.186] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.186] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    25.186] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    25.186] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.186] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    25.186] (==) NVIDIA(0): RGB weight 888
[    25.186] (==) NVIDIA(0): Default visual is TrueColor
[    25.186] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.186] (**) NVIDIA(0): Option "Stereo" "0"
[    25.186] (**) NVIDIA(0): Stereo disabled by request
[    25.186] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0; DFP-0: nvidia-auto-select +0+0; DFP-0: 1920x1080 +0+0; DFP-0: 1920x1080_60 +0+0; DFP-0: 1280x1024 +0+0; DFP-0: 1280x1024_75 +0+0; DFP-0: 1280x1024_60 +0+0; DFP-0: 1152x864 +0+0; DFP-0: 1152x864_75 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 1024x768_75 +0+0; DFP-0: 1024x768_60 +0+0; DFP-0: 800x600 +0+0; DFP-0: 800x600_75 +0+0; DFP-0: 800x600_60 +0+0; DFP-0: 640x480 +0+0; DFP-0: 640x480_75 +0+0; DFP-0: 640x480_60 +0+0; DFP-0: nvidia-auto-select +0+0; DFP-0: nvidia-auto-select +0+0; DFP-0: 1920x1080 +0+0; DFP-0: 1920x1080_60 +0+0; DFP-0: 1280x1024 +0+0; DFP-0: 1280x1024_75 +0+0; DFP-0: 1280x1024_60 +0+0; DFP-0: 1152x864 +0+0; DFP-0: 1152x864_75 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 1024x768_75 +0+0; DFP-0: 1024x768_60 +0+0; DFP-0: 800x600 +0+0; DFP-0: 800x600_75 +0+0; DFP-0: 800x600_60 +0+0; DFP-0: 640x480 +0+0; DFP-0: 640x480_75 +0+0; DFP-0: 640x480_60 +0+0"
[    25.186] (**) NVIDIA(1): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
[    25.186] (**) NVIDIA(0): Enabling 2D acceleration
[    25.924] (II) NVIDIA(GPU-0): Display (DELL U2312HM (DFP-0)) does not support NVIDIA 3D
[    25.924] (II) NVIDIA(GPU-0):     Vision stereo.
[    25.938] (II) NVIDIA(GPU-0): Display (LG Electronics LG TV (DFP-1)) does not support NVIDIA
[    25.938] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    25.938] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 660 Ti (GK104) at PCI:1:0:0 (GPU-0)
[    25.938] (--) NVIDIA(0): Memory: 2097152 kBytes
[    25.938] (--) NVIDIA(0): VideoBIOS: 80.04.4b.00.2e
[    25.938] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    25.938] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    25.947] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 660 Ti at PCI:1:0:0
[    25.947] (--) NVIDIA(0):     CRT-0
[    25.947] (--) NVIDIA(0):     DELL U2312HM (DFP-0) (connected)
[    25.947] (--) NVIDIA(0):     LG Electronics LG TV (DFP-1) (connected)
[    25.947] (--) NVIDIA(0):     DFP-2
[    25.947] (--) NVIDIA(0):     DFP-3
[    25.947] (--) NVIDIA(0):     DFP-4
[    25.947] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    25.947] (--) NVIDIA(0): DELL U2312HM (DFP-0): 330.0 MHz maximum pixel clock
[    25.947] (--) NVIDIA(0): DELL U2312HM (DFP-0): Internal Dual Link TMDS
[    25.947] (--) NVIDIA(0): LG Electronics LG TV (DFP-1): 165.0 MHz maximum pixel clock
[    25.947] (--) NVIDIA(0): LG Electronics LG TV (DFP-1): Internal Single Link TMDS
[    25.947] (--) NVIDIA(0): DFP-2: 165.0 MHz maximum pixel clock
[    25.947] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[    25.947] (--) NVIDIA(0): DFP-3: 330.0 MHz maximum pixel clock
[    25.947] (--) NVIDIA(0): DFP-3: Internal Single Link TMDS
[    25.947] (--) NVIDIA(0): DFP-4: 960.0 MHz maximum pixel clock
[    25.947] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[    25.947] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.947] (**) NVIDIA(0):     device DELL U2312HM (DFP-0) (Using EDID frequencies has
[    25.947] (**) NVIDIA(0):     been enabled on all display devices.)
[    25.958] (II) NVIDIA(0): Validated MetaModes:
[    25.958] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1920x1080+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1920x1080_60+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1280x1024+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1280x1024_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1280x1024_60+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1152x864+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1152x864_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1024x768+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1024x768_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1024x768_60+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:800x600+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:800x600_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:800x600_60+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:640x480+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:640x480_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:640x480_60+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1920x1080+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1920x1080_60+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1280x1024+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1280x1024_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1280x1024_60+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1152x864+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1152x864_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1024x768+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1024x768_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:1024x768_60+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:800x600+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:800x600_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:800x600_60+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:640x480+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:640x480_75+0+0"
[    25.958] (II) NVIDIA(0):     "DFP-0:640x480_60+0+0"
[    25.958] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    25.990] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
[    25.990] (--) NVIDIA(0):     option
[    25.990] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[    25.990] (==) NVIDIA(1): RGB weight 888
[    25.990] (==) NVIDIA(1): Default visual is TrueColor
[    25.990] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    25.990] (**) NVIDIA(1): Option "Stereo" "0"
[    25.990] (**) NVIDIA(1): Stereo disabled by request
[    25.990] (II) NVIDIA(1): NVIDIA GPU GeForce GTX 660 Ti (GK104) at PCI:1:0:0 (GPU-0)
[    25.990] (--) NVIDIA(1): Memory: 2097152 kBytes
[    25.990] (--) NVIDIA(1): VideoBIOS: 80.04.4b.00.2e
[    25.990] (II) NVIDIA(1): Detected PCI Express Link width: 16X
[    25.990] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    25.992] (--) NVIDIA(1): Valid display device(s) on GeForce GTX 660 Ti at PCI:1:0:0
[    25.992] (--) NVIDIA(1):     CRT-0
[    25.992] (--) NVIDIA(1):     DELL U2312HM (DFP-0) (connected)
[    25.992] (--) NVIDIA(1):     LG Electronics LG TV (DFP-1) (connected)
[    25.992] (--) NVIDIA(1):     DFP-2
[    25.992] (--) NVIDIA(1):     DFP-3
[    25.992] (--) NVIDIA(1):     DFP-4
[    25.992] (--) NVIDIA(1): CRT-0: 400.0 MHz maximum pixel clock
[    25.992] (--) NVIDIA(1): DELL U2312HM (DFP-0): 330.0 MHz maximum pixel clock
[    25.992] (--) NVIDIA(1): DELL U2312HM (DFP-0): Internal Dual Link TMDS
[    25.992] (--) NVIDIA(1): LG Electronics LG TV (DFP-1): 165.0 MHz maximum pixel clock
[    25.992] (--) NVIDIA(1): LG Electronics LG TV (DFP-1): Internal Single Link TMDS
[    25.992] (--) NVIDIA(1): DFP-2: 165.0 MHz maximum pixel clock
[    25.992] (--) NVIDIA(1): DFP-2: Internal Single Link TMDS
[    25.992] (--) NVIDIA(1): DFP-3: 330.0 MHz maximum pixel clock
[    25.992] (--) NVIDIA(1): DFP-3: Internal Single Link TMDS
[    25.992] (--) NVIDIA(1): DFP-4: 960.0 MHz maximum pixel clock
[    25.992] (--) NVIDIA(1): DFP-4: Internal DisplayPort
[    25.992] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.992] (**) NVIDIA(1):     device LG Electronics LG TV (DFP-1) (Using EDID
[    25.992] (**) NVIDIA(1):     frequencies has been enabled on all display devices.)
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1440x480" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1440x480".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x480" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     HorizSync check for mode "720x480".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     HorizSync check for mode "720x576".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.994] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.994] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (24.0 Hz); ignoring
[    25.994] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    25.994] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.994] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.994] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.994] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (30.0 Hz); ignoring
[    25.994] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    25.994] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.994] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.994] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.994] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.994] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    25.994] (II) NVIDIA(1): Validated MetaModes:
[    25.994] (II) NVIDIA(1):     "DFP-1:nvidia-auto-select+0+0"
[    25.994] (II) NVIDIA(1): Virtual screen size determined to be 1920 x 1080
[    25.996] (--) NVIDIA(1): DPI set to (69, 70); computed from "UseEdidDpi" X config
[    25.996] (--) NVIDIA(1):     option
[    25.996] (--) Depth 24 pixmap format is 32 bpp
[    25.996] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    25.996] (II) NVIDIA:     access.
[    26.000] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select+0+0"
[    26.054] (II) Loading extension NV-GLX
[    26.076] (==) NVIDIA(0): Disabling shared memory pixmaps
[    26.076] (==) NVIDIA(0): Backing store disabled
[    26.076] (==) NVIDIA(0): Silken mouse enabled
[    26.076] (**) NVIDIA(0): DPMS enabled
[    26.076] (II) Loading extension NV-CONTROL
[    26.077] (II) Loading sub module "dri2"
[    26.077] (II) LoadModule: "dri2"
[    26.077] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.077] (II) Module dri2: vendor="X.Org Foundation"
[    26.077]     compiled for 1.11.3, module version = 1.2.0
[    26.077]     ABI class: X.Org Server Extension, version 6.0
[    26.077] (II) NVIDIA(0): [DRI2] Setup complete
[    26.077] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    26.077] (--) RandR disabled
[    26.079] (II) NVIDIA(1): Setting mode "DFP-1:nvidia-auto-select+0+0"
[    26.240] (==) NVIDIA(1): Disabling shared memory pixmaps
[    26.240] (==) NVIDIA(1): Backing store disabled
[    26.240] (==) NVIDIA(1): Silken mouse enabled
[    26.240] (**) NVIDIA(1): DPMS enabled
[    26.240] (II) Loading sub module "dri2"
[    26.240] (II) LoadModule: "dri2"
[    26.240] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.240] (II) Module dri2: vendor="X.Org Foundation"
[    26.240]     compiled for 1.11.3, module version = 1.2.0
[    26.240]     ABI class: X.Org Server Extension, version 6.0
[    26.240] (II) NVIDIA(1): [DRI2] Setup complete
[    26.240] (II) NVIDIA(1): [DRI2]   VDPAU driver: nvidia
[    26.240] (--) RandR disabled
[    26.240] (II) Initializing built-in extension Generic Event Extension
[    26.241] (II) Initializing built-in extension SHAPE
[    26.241] (II) Initializing built-in extension MIT-SHM
[    26.241] (II) Initializing built-in extension XInputExtension
[    26.241] (II) Initializing built-in extension XTEST
[    26.241] (II) Initializing built-in extension BIG-REQUESTS
[    26.241] (II) Initializing built-in extension SYNC
[    26.241] (II) Initializing built-in extension XKEYBOARD
[    26.241] (II) Initializing built-in extension XC-MISC
[    26.241] (II) Initializing built-in extension SECURITY
[    26.241] (II) Initializing built-in extension XINERAMA
[    26.241] (II) Initializing built-in extension XFIXES
[    26.241] (II) Initializing built-in extension RENDER
[    26.241] (II) Initializing built-in extension RANDR
[    26.241] (II) Initializing built-in extension COMPOSITE
[    26.241] (II) Initializing built-in extension DAMAGE
[    26.241] (II) Initializing extension GLX
[    26.327] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.328] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.328] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.328] (II) LoadModule: "evdev"
[    26.328] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.328] (II) Module evdev: vendor="X.Org Foundation"
[    26.328]     compiled for 1.11.3, module version = 2.7.0
[    26.328]     Module class: X.Org XInput Driver
[    26.328]     ABI class: X.Org XInput driver, version 16.0
[    26.328] (II) Using input driver 'evdev' for 'Power Button'
[    26.328] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.328] (**) Power Button: always reports core events
[    26.328] (**) evdev: Power Button: Device: "/dev/input/event1"
[    26.329] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.329] (--) evdev: Power Button: Found keys
[    26.329] (II) evdev: Power Button: Configuring as keyboard
[    26.329] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    26.329] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    26.329] (**) Option "xkb_rules" "evdev"
[    26.329] (**) Option "xkb_model" "pc105"
[    26.329] (**) Option "xkb_layout" "fr"
[    26.329] (II) XKB: reuse xkmfile /var/lib/xkb/server-1CA37FD61409D6C1EDB80880DF2DB1A574556A6A.xkm
[    26.330] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.330] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.330] (II) Using input driver 'evdev' for 'Power Button'
[    26.330] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.330] (**) Power Button: always reports core events
[    26.330] (**) evdev: Power Button: Device: "/dev/input/event0"
[    26.330] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.330] (--) evdev: Power Button: Found keys
[    26.330] (II) evdev: Power Button: Configuring as keyboard
[    26.330] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    26.330] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    26.330] (**) Option "xkb_rules" "evdev"
[    26.330] (**) Option "xkb_model" "pc105"
[    26.330] (**) Option "xkb_layout" "fr"
[    26.330] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event14)
[    26.330] (II) No input driver specified, ignoring this device.
[    26.330] (II) This device may have been added with another device file.
[    26.330] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[    26.330] (II) No input driver specified, ignoring this device.
[    26.330] (II) This device may have been added with another device file.
[    26.330] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event16)
[    26.330] (II) No input driver specified, ignoring this device.
[    26.330] (II) This device may have been added with another device file.
[    26.330] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event17)
[    26.330] (II) No input driver specified, ignoring this device.
[    26.330] (II) This device may have been added with another device file.
[    26.331] (II) config/udev: Adding input device CH PRODUCTS CH PRO PEDALS USB  (/dev/input/event3)
[    26.331] (II) No input driver specified, ignoring this device.
[    26.331] (II) This device may have been added with another device file.
[    26.331] (II) config/udev: Adding input device CH PRODUCTS CH PRO PEDALS USB  (/dev/input/js0)
[    26.331] (II) No input driver specified, ignoring this device.
[    26.331] (II) This device may have been added with another device file.
[    26.331] (II) config/udev: Adding input device Webcam C170 (/dev/input/event6)
[    26.331] (**) Webcam C170: Applying InputClass "evdev keyboard catchall"
[    26.331] (II) Using input driver 'evdev' for 'Webcam C170'
[    26.331] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.331] (**) Webcam C170: always reports core events
[    26.331] (**) evdev: Webcam C170: Device: "/dev/input/event6"
[    26.331] (--) evdev: Webcam C170: Vendor 0x46d Product 0x82b
[    26.331] (--) evdev: Webcam C170: Found keys
[    26.331] (II) evdev: Webcam C170: Configuring as keyboard
[    26.331] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4.2/1-1.4.2:1.0/input/input6/event6"
[    26.331] (II) XINPUT: Adding extended input device "Webcam C170" (type: KEYBOARD, id 8)
[    26.331] (**) Option "xkb_rules" "evdev"
[    26.331] (**) Option "xkb_model" "pc105"
[    26.331] (**) Option "xkb_layout" "fr"
[    26.331] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
[    26.331] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    26.331] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    26.331] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.331] (**) Logitech USB Optical Mouse: always reports core events
[    26.331] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event4"
[    26.331] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc019
[    26.331] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    26.331] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    26.331] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    26.331] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    26.331] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    26.331] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    26.331] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    26.331] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.331] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input4/event4"
[    26.331] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 9)
[    26.331] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    26.331] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    26.331] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    26.331] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    26.331] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    26.332] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    26.332] (II) No input driver specified, ignoring this device.
[    26.332] (II) This device may have been added with another device file.
[    26.332] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event10)
[    26.332] (II) No input driver specified, ignoring this device.
[    26.332] (II) This device may have been added with another device file.
[    26.332] (II) config/udev: Adding input device HDA Intel PCH Line-Out CLFE (/dev/input/event11)
[    26.332] (II) No input driver specified, ignoring this device.
[    26.332] (II) This device may have been added with another device file.
[    26.332] (II) config/udev: Adding input device HDA Intel PCH Line-Out Surround (/dev/input/event12)
[    26.332] (II) No input driver specified, ignoring this device.
[    26.332] (II) This device may have been added with another device file.
[    26.332] (II) config/udev: Adding input device HDA Intel PCH Line-Out Front (/dev/input/event13)
[    26.332] (II) No input driver specified, ignoring this device.
[    26.332] (II) This device may have been added with another device file.
[    26.332] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event7)
[    26.332] (II) No input driver specified, ignoring this device.
[    26.332] (II) This device may have been added with another device file.
[    26.332] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event8)
[    26.332] (II) No input driver specified, ignoring this device.
[    26.332] (II) This device may have been added with another device file.
[    26.332] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event9)
[    26.332] (II) No input driver specified, ignoring this device.
[    26.332] (II) This device may have been added with another device file.
[    26.333] (II) config/udev: Adding input device Saitek Saitek Pro Flight Yoke (/dev/input/event5)
[    26.333] (II) No input driver specified, ignoring this device.
[    26.333] (II) This device may have been added with another device file.
[    26.333] (II) config/udev: Adding input device Saitek Saitek Pro Flight Yoke (/dev/input/js1)
[    26.333] (II) No input driver specified, ignoring this device.
[    26.333] (II) This device may have been added with another device file.
[    26.333] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    26.333] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.333] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.333] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.333] (**) AT Translated Set 2 keyboard: always reports core events
[    26.333] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    26.333] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    26.333] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    26.333] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    26.333] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    26.333] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    26.333] (**) Option "xkb_rules" "evdev"
[    26.333] (**) Option "xkb_model" "pc105"
[    26.333] (**) Option "xkb_layout" "fr"
[    34.293] (II) NVIDIA(GPU-0): Display (DELL U2312HM (DFP-0)) does not support NVIDIA 3D
[    34.293] (II) NVIDIA(GPU-0):     Vision stereo.
[    34.293] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    34.293] (**) NVIDIA(0):     device DELL U2312HM (DFP-0) (Using EDID frequencies has
[    34.293] (**) NVIDIA(0):     been enabled on all display devices.)
[    34.307] (II) NVIDIA(GPU-0): Display (LG Electronics LG TV (DFP-1)) does not support NVIDIA
[    34.307] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    34.307] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display
[    34.307] (**) NVIDIA(1):     device LG Electronics LG TV (DFP-1) (Using EDID
[    34.307] (**) NVIDIA(1):     frequencies has been enabled on all display devices.)
[    34.307] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.307] (WW) NVIDIA(GPU-0):     mode "1440x480" is specified in the EDID; however, the
[    34.307] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    34.307] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    34.307] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1440x480".
[    34.307] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.307] (WW) NVIDIA(GPU-0):     mode "720x480" is specified in the EDID; however, the
[    34.307] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    34.307] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    34.307] (WW) NVIDIA(GPU-0):     HorizSync check for mode "720x480".
[    34.307] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.307] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    34.307] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    34.307] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    34.307] (WW) NVIDIA(GPU-0):     HorizSync check for mode "720x576".
[    34.307] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.307] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    34.307] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.307] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.307] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    34.308] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.308] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    34.308] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.308] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.308] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    34.308] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.308] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    34.308] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.308] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.308] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    34.308] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.308] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    34.308] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.308] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.308] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    34.308] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.308] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.308] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.308] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.308] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    34.308] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.308] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.308] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    34.308] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[    34.308] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[    34.308] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.308] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.308] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.308] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (24.0 Hz); ignoring
[    34.308] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    34.308] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.308] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.308] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.308] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (30.0 Hz); ignoring
[    34.308] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    34.308] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.308] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.308] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.308] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.308] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    34.755] (II) NVIDIA(GPU-0): Display (DELL U2312HM (DFP-0)) does not support NVIDIA 3D
[    34.755] (II) NVIDIA(GPU-0):     Vision stereo.
[    34.755] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    34.755] (**) NVIDIA(0):     device DELL U2312HM (DFP-0) (Using EDID frequencies has
[    34.755] (**) NVIDIA(0):     been enabled on all display devices.)
[    34.769] (II) NVIDIA(GPU-0): Display (LG Electronics LG TV (DFP-1)) does not support NVIDIA
[    34.769] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    34.769] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display
[    34.769] (**) NVIDIA(1):     device LG Electronics LG TV (DFP-1) (Using EDID
[    34.769] (**) NVIDIA(1):     frequencies has been enabled on all display devices.)
[    34.769] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.769] (WW) NVIDIA(GPU-0):     mode "1440x480" is specified in the EDID; however, the
[    34.769] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    34.769] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    34.769] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1440x480".
[    34.769] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.769] (WW) NVIDIA(GPU-0):     mode "720x480" is specified in the EDID; however, the
[    34.769] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    34.769] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    34.769] (WW) NVIDIA(GPU-0):     HorizSync check for mode "720x480".
[    34.769] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.769] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    34.769] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    34.769] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    34.769] (WW) NVIDIA(GPU-0):     HorizSync check for mode "720x576".
[    34.769] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.769] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    34.769] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.769] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.770] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    34.770] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.770] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    34.770] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.770] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.770] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    34.770] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.770] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    34.770] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.770] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.770] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    34.770] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.770] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    34.770] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.770] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.770] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    34.770] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.770] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.770] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.770] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.770] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    34.770] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.770] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.770] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    34.770] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[    34.770] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[    34.770] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.770] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.770] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.770] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (24.0 Hz); ignoring
[    34.770] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    34.770] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.770] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.770] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.770] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (30.0 Hz); ignoring
[    34.770] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    34.770] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    34.770] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    34.770] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    34.770] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    34.770] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
```
For info, I have a dell screen on the DVI port and and a LG TV on the HDMI.

---

### Post by MAFoElffen on 2015-01-01
Please post your /etc/X11/xorg.conf file so I can see it and change the Horizontal and Vertical sync lines for you (to set manually). 
```

[    25.992] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.992] (**) NVIDIA(1):     device LG Electronics LG TV (DFP-1) (Using EDID
[    25.992] (**) NVIDIA(1):     frequencies has been enabled on all display devices.)
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1440x480" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1440x480".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x480" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.7 kHz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     HorizSync check for mode "720x480".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (15.6 kHz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     HorizSync check for mode "720x576".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "720x576" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "720x576".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1280x720" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1280x720".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.993] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (28.000-68.000 kHz) would
[    25.993] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[    25.993] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[    25.993] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.993] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.994] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.994] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (24.0 Hz); ignoring
[    25.994] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    25.994] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.994] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.994] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.994] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (30.0 Hz); ignoring
[    25.994] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    25.994] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-1) contradicts itself:
[    25.994] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    25.994] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (58.000-63.000 Hz) would
[    25.994] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    25.994] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".



```
That is where is looks like it's having diffugalties. What Model number is the LG TV? (I'll need to compare the EDID that it reported, with what the manufacturer says it should be, then adjust from that.) Are you trying to mirror the two displays? Was that TV turned off when you did the X config?

...and does it work if you unplug the video cable from that TV?

---

### Post by NHerby on 2015-01-01
And here it is:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.64  (buildd@meitnerium)  Wed Nov  7 05:56:00 UTC 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1920 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL U2312HM"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TOSHIBA-TV"
    HorizSync       15.0 - 68.0
    VertRefresh     49.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660 Ti"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660 Ti"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0; DFP-0: nvidia-auto-select +0+0; DFP-0: 1920x1080 +0+0; DFP-0: 1920x1080_60 +0+0; DFP-0: 1280x1024 +0+0; DFP-0: 1280x1024_75 +0+0; DFP-0: 1280x1024_60 +0+0; DFP-0: 1152x864 +0+0; DFP-0: 1152x864_75 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 1024x768_75 +0+0; DFP-0: 1024x768_60 +0+0; DFP-0: 800x600 +0+0; DFP-0: 800x600_75 +0+0; DFP-0: 800x600_60 +0+0; DFP-0: 640x480 +0+0; DFP-0: 640x480_75 +0+0; DFP-0: 640x480_60 +0+0; DFP-0: nvidia-auto-select +0+0; DFP-0: nvidia-auto-select +0+0; DFP-0: 1920x1080 +0+0; DFP-0: 1920x1080_60 +0+0; DFP-0: 1280x1024 +0+0; DFP-0: 1280x1024_75 +0+0; DFP-0: 1280x1024_60 +0+0; DFP-0: 1152x864 +0+0; DFP-0: 1152x864_75 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 1024x768_75 +0+0; DFP-0: 1024x768_60 +0+0; DFP-0: 800x600 +0+0; DFP-0: 800x600_75 +0+0; DFP-0: 800x600_60 +0+0; DFP-0: 640x480 +0+0; DFP-0: 640x480_75 +0+0; DFP-0: 640x480_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by MAFoElffen on 2015-01-01
Wow, no wonder. X config though it was a different brand TV? (Toshiba?)

You didn't answer the other questions there, so:
1. You are trying to do dual-monitor? Meaning both your monitors will be turned on before you start the PC?

I ask this, because some start with the PC's monitor, then occassionally switch the input on their TV, to the PC, so they can look at things there  That is setup as a mirrored display, but the EDID has to be defined manually, so that the PC still see's something, when the input is disconnected from or the TV is not turned on... If one is off and you turn it on, the conf file says there are two, which would be different than what it sees... Unless I tell it to ignore one or both.

2. If dual-display, are you doing mirror or side-by-side (panorama)?

If mirror, then both need to have a common resolution and be set to that manually, in the xorg.conf file. At the moment, they are not. If panarama, which the conf file is now setup for, then you setup a big virtual desktop and tell each screen which part of that to display. Easiest if both are the same resolution.

4. What brand and model TV? 

Because I now see two brands and still don't know a model of... Because your conf file ID'ed it as something different, which may be why it now has conflicts with that.

5. I need to know "how" you want to use your Monitors, so I have an idea of how to set that up for you.

*** So yes, need that feedback from you to be able to help you.

---

### Post by NHerby on 2015-01-01
I only use the TV to display videos (XBMC) so most of the time, it's off. And I only switch it on when it's movie time ;).
It is set up side by side (panorama) and the TV is a LG 32LF20FR.
This TV was off when I installed the updates. The 2 screens are 1920x1080.

Hope you have all the infos needed.

---

### Post by MAFoElffen on 2015-01-01
On the LG-- 1920x1080i or 1920x1080p? (I'm guessing "p"...) And you are using which HDMI ports on the  LG itself? (1,2,or 3?) Those effect the sync rates it wants to see...

---

### Post by MAFoElffen on 2015-01-01
Here's your new file to try... Backup the old before using this one:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.64  (buildd@meitnerium)  Wed Nov  7 05:56:00 UTC 2012
# Modified by MAFoElffen 2015.1.1

Section "ServerLayout"
    Identifier     "Layout0"
    # The defualt screen is Screen0, so should be left of Screen1
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 1920 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice" # this scetion is deprecated and will be ignored, now hot-plug dev's
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice" # this scetion is deprecated and will be ignored, now hot-plug dev's
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Dell"
    ModelName      "U2312HM"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # This is sometimes turned off, so skip trying to getthe physical EDID and supply 1920x180p resolutions 
    #   and sync rates, for the card to find, even if it is turned off.
    Identifier     "Monitor1"
    VendorName     "LG"
    ModelName      "32LF20FR"
    # Vendor service manual says the aspect ratio is 4:3 or 16:9 (switchable)
    # HorizSync       15.0 - 68.0
    # VertRefresh     49.0 - 61.0
    HorizSyns      27.0 - 68.0
    VertRefresh    24.0 - 60.0
    ## It's supported modes in that resolution
    # RGB-PC mode 1920x1080 h66.587 v59.93
    Modeline       "1980x1080_59a" 172.60 1920 2040 2248 2676 1080 1081 1084 1118 -hsync +vsync 
    # HDMI-DTV mode 1980x1080   67.432    59.94
    Modeline       "1980x1080_59b" 172.63 1920 2040 2248 2676 1080 1081 1084 1118 -hsync +vsync 
    # HDMI-DTV mode 1980x1080    67.50    60.00
    ModeLine       "1920x1080_60"  172.80 1920 2040 2248 2576 1080 1081 1084 1118 -hsync +vsync
    ModeLine       "1920x1080_60i"  77.60 1920 1952 2240 2272 1080 1104 1110 1135 -hsync +vsync
    # HDMI-DTV mode 1980x1080    56.25    50.00
    ModeLine      "1920x1080_50"   143.55  1920 1952 2494 2528 1080 1103 1112 1135 -hsync +vsync
    # HDMI-DTV mode 1980x1080    27.00    24.00
    Modeline       "1980x1080_24"   61.81  1920 1944 2136 2352 1080 1081 1084 1095 -hsync +vsync 
    # HDMI-DTV mode 1980x1080    33.75    30.00
    Modeline       "1980x1080_30"   80.18  1920 1984 2176 2432 1080 1081 1084 1099 -hsnc +vsync 
    Option         "UseEdidFreqs" "False"
    Option         "PreferredMode" "1920x1080_60"
    Option         "DPMS"
EndSection

Section "Device"   # Setup for DFP-0 to Dell
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660 Ti"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"   # Setup for DFP-1 to LG
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660 Ti"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "NoLogo" "True"
    # supply enough that is has EDID info without probing the Hardware
    Option         "UseEDID" "False"
    Option         "UseEdidDpi" "False"
    Option         "ModeValidation" "NoVesaModes, NoXServerModes, NoEdidModes"
    Option         "DPI" "95 x 94"
EndSection

Section "Screen" # Dell
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0" # Dell
    DefaultDepth    24
    Option         "Stereo" "0"
    Option          "metamodes" DFP-0: 1920x1080 +0+0; DFP-0: 1920x1080_60 +0+0;
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen" # LG
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1" # LG
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-1: 1920x1080_60  +0+0; DFP-1: 1920x1080_60i  +0+0; DFP-1: 1920x1080_50  +0+0; DFP-1: 1920x1080_59a  +0+0; DFP-1: 1920x1080_59b  +0+0; DFP-1: 1920x1080_24  +0+0; DFP-1: 1920x1080_30  +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by NHerby on 2015-01-02
Just gave a try with your xorg.conf
But no luck. I don't even reach the login screen. It seems to block while mounting the network drives. I'll try again in command line to see if I have an error more relevant.

On the other hand, I've tried to install Kubuntu 14.04 on another drive for test. I made a copy of the xorg.conf from this installation and tried to boot Kubuntu 12.04 with it but this also gives me a black screen after the login screen.

Edit:
Juste made a new try with the xorg.conf given above. On a normal boot, I'm stucked before the login screen :(.
In recovery mode here's what I have after "startx":
```
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0      [vsyscall]
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
```

In the meantime, after a few trial and error, I've managed to install Kubuntu 14.04 on a spare HDD. Last install was straight ahead and got almost everything back in about 4 hours. So I'll just give up with this broken 12.04 and move on to a fresh new install. It will definitively be faster than trying to fix this problem.

Thanks again [**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1044547") for your help, even if we didn't go very far.

---

