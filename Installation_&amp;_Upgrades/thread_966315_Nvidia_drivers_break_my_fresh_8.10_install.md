---
title: "Nvidia drivers break my fresh 8.10 install"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by iSTRONG on 2008-11-01
I was on 8.04 and it all worked fine.
Then i did a fresh install of 8.10 Ibex and the install went with no problem.
I ran update manager and installed 6 new packages & rebooted. No problem.
I clicked on the restricted drivers and installed.activated nvidia 177 and rebooted. PROBLEM!
On reboot, ubuntu goes to command line. Asks me to enter username&password (no GUI).
After i do that, it goes to command prompt.

I'm a bit of a n00b. Things I've tried:
sudo startx
--> says Fatal Error: no screen found then goes back to command prompt

sudo dpkg-reconfigure xserver-xorg
--> doesn't fix problem

I've also tried recovery mode ---> fix xserver
--> doesn't fix problem

I've also tried editing xorg.conf and changing "nvidia" to "nv"
--> no help

Any ideas?


```


Here is my Xorg.0.log file:

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux Desktop-Ubuntu 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  1 11:32:24 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 8

(!!) More than one possible primary device found
(--) PCI: (0@1:0:0) nVidia Corporation G80 [GeForce 8800 GTS] rev 162, Mem @ 0xf8000000/16777216, 0xc0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
(--) PCI: (0@4:0:0) nVidia Corporation GeForce 8400 GS rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.80  Wed Oct  1 15:09:29 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
Primary device is not PCI
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: 
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found
```

---

### Post by iSTRONG on 2008-11-01
also forgot to say that it's x64 ubuntu

---

### Post by adieb on 2008-11-01
as far as I remember it is not possible to build the nvidia kernel module on a ubuntu-server maschine.
Ther server-kernel doesnt have some compiled in options the nvidia module needs.

But it is strange that changin to nv doenst help

---

### Post by adieb on 2008-11-01
please post your /etc/X11/xorg.conf

---

### Post by iSTRONG on 2008-11-01
it's not the server edition. It's the desktop edition...

here is my xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by lifelesspoet on 2008-11-01
same problem here.  running 64 bit xubuntu with 2 8800 gts 512's in sli

---

### Post by MountainX on 2008-11-01
I am running 8.04 with nVidia drivers. I am considering upgrading to 8.10 and this thread caught my attention. 

Has anyone tried using EnvyNG to resolve this problem?

You might also want to check:

[http://albertomilone.com/](http://albertomilone.com/)

[http://albertomilone.com/wordpress/?p=292](http://albertomilone.com/wordpress/?p=292)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/40](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/40)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107)

---

### Post by Lagrange on 2008-11-01
same configuration as lifelesspoet, same problem. Seems like more gaming oriented configurations have not been tested in Beta...but the gamers might have a dual boot. Guess wie have to wait for a later edition of 8.10

---

### Post by Horomancer on 2008-11-01
Hmmm was going to do a fresh install of 8.10, but not it looks like sticking with a fresh hardy install would be better

---

### Post by iSTRONG on 2008-11-02
i fixed my problem by adding
BusID "XX:YY:Z"
to the device section of my xorg.conf
XX:YY:Z can be obtained through the command lspci (find primary video device PCI address)

Basically, the problem is that when you have 2 video cards, xserver doesn't make an assumption about which one is the primary one. So you have to specify it in xorg. conf.

Hope that helps someone.

---

### Post by yobster on 2008-11-02
I have the exact same problem, took me a while to discover that it was the Nvidia drivers doing it though.. and that it does it with 177 and 173

Could anyone explain in better detail how that fix works please?
I've been using Ubuntu since Feisty, but still wary about editing things without slightly more 'step-by-step' instructions. I've reinstalled my Intrepid 4 times because of this problem and I know it'll end up being 5+ without a bit of help!

My lspci looks like this:

```
chris@chris-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
**02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)**
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

```

That's the bit I want right?
and then where/how exactly does it go in my xorg.conf?

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```


Thanks in advance ;)

---

### Post by yobster on 2008-11-02
bump :)

---

### Post by wizardStan on 2008-11-02
I have just had great success with this solution.
The problem: two video cards, and X doesn't know which to use.  Presumably the old versions of X just assumed one, but the new version that comes with 8.10 does not.
Solution:
replace
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```
with
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	BusId "X:0:0"
EndSection
```

replacing the "X:0:0" with whatever is your primary card.  2:0:0 in your case.  Mine was 1:0:0.  If the 2:0:0 results in a black screen, then you guessed wrong; plug your monitor into the other video card as that has been made primary.
Hopefully this helps!

---

### Post by yobster on 2008-11-02
yes! it worked! I had tried putting in 02:00.0 earlier and it didn't work so I gave up.
but came back here and put in 2:0:0
that gave me a black screen, which didn't change when I switched the plug and rebooted.
So I put in 3:0:0 and success, here I am!

Thanks!

---

### Post by iSTRONG on 2008-11-03
*deleted*

---

### Post by aikiwolfie on 2008-11-03
Okay this just isn't working for me. I've tried putting the BusID option in. Tried both values for my cards. "1:0:0" and "6:0:0". That didn't work. Tried changing the driver from "nvidia" to "nv". That didn't have any effect.

I've even run nvidia-xconfig. Add the BusID option to the xorg.conf file that it produces and it still doesn't work. I have two GeForce 7900s in an SLI configuration.

When my PC boots I get the following output:
```
Boot from (hd0,3) ext3   3f13443e-3680-410a-9c8d-76cf0be7d2c2
Starting up ...
Loading, pleasewait...
usplash: Setting mode 1600x1200 failed
usplash: Using mode 1280x1024
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/bd6d2e27-6682-4c40-a9a9-1fb43df5086a) = dev(8,3)
kinit: trying to resume from /dev/disk/by-uuid/bd6d2e27-6682-4c40-a9a9-1fb43df5086a
kinit: No resume image, doing normal boot...

Ubuntu 8.10 moonstone tty1

moonstone login:
```

What is "kinit"? Why is it trying to "resume" from an image? I did a reboot. I also get this after doing a complete shutdown after I install nvidia-glx-177.

---

### Post by aikiwolfie on 2008-11-03
Okay kinit seems to be something to do with sleep or hibernation mode. No idea why it's causing a problem here. But it is and it does it every time I try to install the driver.

Looks like my PC is just incompatible with Ubuntu 8.10. Which is a shame. I was so looking forward to it.

---

### Post by aikiwolfie on 2008-11-03
Okay kinit seems to be something to do with sleep or hibernation mode. No idea why it's causing a problem here. But it is and it does it every time I try to install the driver.

Looks like my PC is just incompatible with Ubuntu 8.10. Which is a shame. I was so looking forward to it.

---

### Post by aikiwolfie on 2008-11-03
Ok I think I've tried just about everything now. Just downloaded the 177.80 driver from the nvidia website and tried to install it. No change. I even stopped the xserver and tried to install the Ubuntu versions that way.

I'm giving up for now. I need my PC back in working order tomorrow. So it's back to 8.04.1 for me.

---

### Post by damien_vancouver on 2008-11-04
[CENTER][U]HOW TO GET THE NVIDIA DRIVER WORKING FOR NVIDIA SLI DUAL VIDEO CARDS UBUNTU INTREPID 8.10
HOW TO FIX BROKEN X WINDOWS TEXT ONLY NO GRAPHICAL DESKTOP AFTER INSTALLING THE NVIDIA DRIVER
[/U][/CENTER]

This problem should affect anyone with a SLI setup with 2 or 3 nvidia video cards, the first time you reboot after installing the nvidia restricted driver (which will happen if you turn on desktop effects on a newly installed Ubuntu / SLI system).  X Windows will fail to start saying "No Screen Found" and you will be stuck at a text login prompt!  Doh!!!!


**_Fast fix instructions for the experienced:_** 

[LIST=1]
[*]The BusId fix described in this thread has to go into the "Device" section in /etc/X11/xorg.conf, not into the "Screens" section.

[*]Use **lspci | grep -i vga** to find your cards BusIDs.  They will be something like 01:00.0 or 02:00.0.  These would translate to BusId "01:00:00" or BusId "02:00:0" in the xorg.conf.

[*]Edit /etc/X11/xorg.conf with sudo, find *Section "Device"* and try one or the other BusId line.

[*]Test X windows with **startx**.  Use **ctrl-alt-backspace** to get out of X windows.  Try the other BusID line if the first one doesn't work.

[*]Once you have it working, Restart gdm with **sudo /etc/init.d/gdm restart.  Rejoice.**
[/LIST]


**_Very Gentle instructions for beginners:_**

You will be starting from a broken system that only boots into text mode, and it will be prompting you for a username.  Type the commands shown in boldface.  Everything else is just a copy of what happened on my system so you know what else you will be seeing.

1. Login with your username/password you usually login with.  If you don't have a password set, just hit enter.

```
Ubuntu 8.10 yourmachine tty1

yourmachine login: **yourusername**
Password: **mypassword**

```

2. Remove any old possibly broken install of v173 or v177 nvidia drivers...

```
$ **sudo apt-get purge nvidia-glx-173 nvidia-glx-177**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-173 is not installed, so not removed
The following packages will be REMOVED:
  nvidia-glx-177*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 25.8MB disk space will be freed.
Do you want to continue [Y/n]? **[Enter]**
(Reading database ... 111389 files and directories currently installed.)
Removing nvidia-glx-177 ...
Purging configuration files for nvidia-glx-177 ...
dpkg - warning: while removing nvidia-glx-177, directory `/usr/lib/tls' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

3. Reinstall the v177 nvidia driver

```
$ **sudo apt-get install nvidia-glx-177**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-glx-177
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8931kB of archives.
After this operation, 25.8MB of additional disk space will be used.
Selecting previously deselected package nvidia-glx-177.
(Reading database ... 111345 files and directories currently installed.)
Unpacking nvidia-glx-177 (from .../nvidia-glx-177_177.80-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-glx-177 (177.80-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```


4. Let nvidia-xconfig make you a new /etc/X11/xorg.conf file:
```
$ **sudo nvidia-xconfig**

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

5. List the video card busID's with lspci:
```
$ **lspci | grep -i vga**
***03:00.0*** VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
***04:00.0 ***VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)

```

On my system, the cards are *03:00.0* and *04:00.0*.  These would go into xorg.conf as **BusId "03:00:00"** and **BusId "04:00:00"** respectively.  Your setup will probably show different numbers in the first field, and you might even have 3 video cards if you're using 3-way SLI.


Next you have to take a guess which card is which.  You have a 50/50 chance of getting it right... :)

Write down the two bus ID's on a piece of paper so you have them for the next step.

6. Edit /etc/X11/xorg.conf and add the BusId line to the Device section.  (use your favourite text editor instead of pico if you want)
```
$ ** sudo pico /etc/X11/xorg.conf **
```

Hit Ctrl-W and type:  **Section "Device"** to search for the right section.

Pico will find the Device section.  Mine looked like this:

```
Section "Device"
    Identifier     "Configured Video Device" 
    Driver         "nvidia"
EndSection
```


Add in the your first guess for the BusId line, so it looks like this:
```
Section "Device"
    Identifier     "Configured Video Device" 
    Driver         "nvidia"
    **BusId "04:00:00"**
EndSection
```


Now save the file with Ctrl-O and then exit pico with Ctrl-X.  You will be back at a $ command prompt.

7. See if X Windows starts using startx!
```
$ ** startx **
```

With any luck you see X-Windows startup!

If you see just a black screen or nothing happens, you go back to step 6 and edit xorg.conf, putting in the other possible BusId line..  Then re-try **startx** and it should work.  You can stop X windows now with **ctrl-alt-backspace** to get back to the prompt so you can repeat step 6.

The debugging output you see go by can be found in /var/log/Xorg.0.log, which you can look at with **less /var/log/Xorg.0.log**  (use space bar for next page, b for previous page, g for start of file, G for end of file, and q to quit).


Now it's time to stop the X windows we started with "startx" and try and start the gdm login manager:

8. Stop X-Windows if it's running.  Press: **Ctrl-Alt-Backspace** and X will die, leaving you back at the $ command prompt
 
9. repeat steps 6 and 7 again until you get the right BusId. 
Once you have a working configuration, restart gdm (the graphical login screen):
```

$ **sudo /etc/init.d/gdm start**

```

the usual Ubuntu login screen should start!

10. Graphical Linux is now back, rejoice!  

11. You should now be able to go into System -> preferences -> Appearance in Ubuntu and turn on the enhanced effects in the Visual Effects tab.   Try dragging windows around and shaking them.  Also try breaking them out to the left or right to switch them to a different desktop.  Try Windows-Tab instead of Alt-Tab to do fancy 3D window switching.  Cool!

---

### Post by aikiwolfie on 2008-11-09
Yeah I've done all that and it still doesn't work. A little deeper research has shown this bug can be triggered by any number of things. One of them being errors in the partition table.

I did mess around with my partitions a while back. Just experimenting. I think I might need to completly repartition my boot drive.

So for anybody else experiencing this problem. If you've tried the above fix and it doesn't work. Think long and hard about what else you've been doing to your system.

On the plus side 8.10 works fine on my Dell XPS M1330n. While I like some of the new features. The improvments aren't so huge I'm about to jump in and start deleting partitions on my desktop. It can wait for a quiet day when I have nothing better to do.

---

### Post by MadKraut on 2008-11-09
*deleted*

---

### Post by Newbie23 on 2008-11-12
Thanks Van_dam....it worked for me
However I lost my sound in doing so....help please.

---

### Post by aikiwolfie on 2008-11-15
Finally made it work! Thanks for all the help guys.

---

### Post by alaska.alex on 2009-02-24
> **damien_vancouver said:**
> [CENTER][U]HOW TO GET THE NVIDIA DRIVER WORKING FOR NVIDIA SLI DUAL VIDEO CARDS UBUNTU INTREPID 8.10
HOW TO FIX BROKEN X WINDOWS TEXT ONLY NO GRAPHICAL DESKTOP AFTER INSTALLING THE NVIDIA DRIVER
[/U][/CENTER]

You, sir, are my hero.

---

