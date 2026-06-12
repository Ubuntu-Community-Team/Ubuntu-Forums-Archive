---
title: "problem with video driver nvidia."
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by joeypoey85 on 2011-08-19
Hi, im hoping someone could give me some assistance with this problem I'm having with my video driver on Ubuntu 11.4.

This is my first time using linux but I have been an experienced windows user for years, finally at the age of 26 I decided to try a linux flavor. Anyway, I installed 11.4 (32bit, not sure if that makes a difference) on my Samsung SF510 Laptop (64bit) with onboard NVIDIA 310M chipset.

After the installation:

I installed nvidia-current and reboot. So i open "nvidia-settings" and a message comes up saying: "Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server"

In the devices manager it says my driver is activated but not in use (proprietary) nvidia-current. 

In the video section of my XORG.CONF it reads:

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

After generating the xorg.conf with command: nvidia-settings
and restart it stops at AppArmor ok. I have to remove the xorg.conf or I can't get back in. 

I have video its just 3d im looking for? I don't know if its because my card isnt supported on this new ubuntu version? if thats the case if anyone knows some other version or distro? 

as i said im on 11.4 and i was refered by a friend that ubuntu would be one of the easy ones for someone new to linux. 

or maybe i should try the 64bit 11.4, or the 32bit 10.4.

Can someone clear this up for me cus Ive done alot of searching(im a pro googler) and i see some people experiencing the exact same thing to me but not sure if they got it fixed yet.

I'm looking for a fast operating system that i can run wow on and maybe some crappy fps games like quake2/3. even if its on low settings :p i cant deal with windows lag anymore. 

on one forum the guy said to extract the EDID file from your windows. cus he said the EDID file is what i was missing from the xorg.conf video section. So I get this program called "Phoenix" to extract the EDID from my windows registry, then I export the file to either a .raw or .hex format. Anyway, when I brought up the EDID list, there was 5 of em. So I thought, which one do i extract? each of them have different properties, I tried the one that shows the most video res. Anyway heres the list.

HARDWARE ID            MANUFACTURER         DESCRIPTION

SAM0200                MONITOR\SAM0200
SEC3245                @monitor.inf
SEC3250
SEC3255
SHP0FFC

In the "color/eastablished timings" tab for SHP0FFC, 11 out of 17
of the video modes have a check mark beside it, the other ID's come up as having no check marks or maybe like 2 or 3. so i chose that one (SHP0FFC) from the list of 5 and exported the .raw, pointed to it in my xorg.conf according to what the guy on the forum said. Reboot, still cant get past that AppArmor OK check screen. sometimes it stops at different places.

I've done the mesa utils 3d test and it said "GLX" missing on display.

Also tried installing manually using sh command from recovery root console, I tried the nvidia-173 driver.

...I don't know what else to do..

Please any advice would be appreciated. I've been searching for 2 days and starting to lose hope :<

Thanks in advance,
Joe

---

### Post by joeypoey85 on 2011-08-19
Just wanna add a couple things.


#1: I was also told in another forum that it had something to do with memory but i dont know if I want to mess with that, could have an effect on my computer it raised too high n such.

-

#2: i've also seen a xorg.conf video section code that seems to work for sony's, it reads:

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
Option "ConnectedMonitor" "DFP-0"
Option "CustomEDID" "DFP-0:/etc/X11/sonycw.bin"
EndSection

as per another forum, I added this below to my xorg.conf:

Option "ConnectedMonitor" "DFP-0"
Option "CustomEDID" "DFP-0:/etc/X11/EDID_FILE.raw" ##extract edid information from windows

stops at check screen againn. Restart the x serve ,try starting it, same thing. :/

---

### Post by dino99 on 2011-08-19
you should not need xorg.conf as actual kernel directly deals with X, so to remove it into a terminal:

sudo rm /etc/X11/xorg.conf

and your driver issue is common to nvidia users all around there, its a jockey issue wrongly reporting status

[https://bugs.launchpad.net/jockey/+bug/771788](https://bugs.launchpad.net/jockey/+bug/771788)

so no worry ;)

---

### Post by joeypoey85 on 2011-08-19
wait, so your telling me that it actually works and is just false reporting saying that it doesnt work?

so how come when i tried to run this game called paintball2, based on the quake2 engine, it said GLX missing on display? heres the output:

Paintball 2 -- Version 2.0
Execing configs/default.cfg.
Console initialized.

------- Sound initialization -------
LoadLibrary("./snd_oss.so")
/dev/dsp: No such file or directory
SNDDMA_Init: Could not open /dev/dsp.
------- Loading ref_pbgl.so -------
LoadLibrary("./ref_pbgl.so")
ref_gl version: PB2GL 0.32
Using libGL.so for OpenGL...
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "GLX" missing on display ":0.0".
W: couldn't get an RGBA, DOUBLEBUFFER, DEPTH, STENCIL visual
Xlib:  extension "GLX" missing on display ":0.0".
E: couldn't get an RGBA, DOUBLEBUFFER, DEPTH visual
ref_gl::R_SetMode() - Invalid mode.
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "GLX" missing on display ":0.0".
W: couldn't get an RGBA, DOUBLEBUFFER, DEPTH, STENCIL visual
Xlib:  extension "GLX" missing on display ":0.0".
E: couldn't get an RGBA, DOUBLEBUFFER, DEPTH visual
ref_gl::R_SetMode() - Could not revert to safe mode.
ref_gl::R_Init() - Could not R_SetMode().
Recursive shutdown.
Error: Error during initialization.
Make sure you have an OpenGL capable video card and that the latest drivers are installed.

---

### Post by Duncan Williams on 2011-08-19
Additional drivers should say if you are using nvidia current.
The main check is that you have `nvidia xserver settings' available.
Then you can change and set your video settings.

If `nvidia xserver settings' is showing in your menu then you have installed nvidia drivers.
Don't pay attention to the `this driver is activated but not in use' if you can use `nvidia xserver settings'

---

### Post by joeypoey85 on 2011-08-19
> **Duncan Williams said:**
> Additional drivers should say if you are using nvidia current.
The main check is that you have `nvidia xserver settings' available.
Then you can change and set your video settings.

If `nvidia xserver settings' is showing in your menu then you have installed nvidia drivers.
Don't pay attention to the `this driver is activated but not in use' if you can use `nvidia xserver settings'

yes nvidia-settings comes up, with an error message saying that i need to configure my xconf file and then restart the x server, and i can not change any settings in the window, theres is a bar on the side for possible categories(tabs) but nothing is present, just a blank white box.

I came across this site here and thought i'd use this "module": (acpi_call)

[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

because im under the impression that my laptop is a hybrid (2 video cards, nvidia and intel).

i got to the last part ./test_off.sh

root@user1:/home/user1/Desktop/paintball2/acpi_call# chmod u+x test_off.sh
root@user1:/home/user1/Desktop/paintball2/acpi_call# ./test_off.sh
Trying \_SB.PCI0.P0P1.VGA._OFF: failed
Trying \_SB.PCI0.P0P2.VGA._OFF: failed
Trying \_SB_.PCI0.OVGA.ATPX: failed
Trying \_SB_.PCI0.OVGA.XTPX: failed
Trying \_SB.PCI0.P0P3.PEGP._OFF: failed
Trying \_SB.PCI0.P0P2.PEGP._OFF: works!
 
one of them works, does that change anything? well... the  output of "lspci -vnnn | grep VGA" is exactly the same so i doubt. try running the game again, same error message as above.

about to try the 2nd method (switcheroo) of turning off the intel card (which is what i think this is for)

let you know how it goes.

---

### Post by Duncan Williams on 2011-08-19
kewl, yes you would probably need to switch off (at bios level) onboard video if you wish to use a graphics card.

---

### Post by joeypoey85 on 2011-08-19
i tried the switcheroo module or w.e, got to near the end of the steps and it couldnt find the /sys/kernel/debug/vgaswitcheroo/ dir, so much for that.

also tried using this bumblebee module too from this link:

[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

****optirun glxgears output:***

user1@user1:~/asus-switcheroo/bumblebee$ optirun glxgears
 * Starting Bumblebee X server bumblebee                                        /usr/local/bin/bumblebee-enablecard: 1: &#65533;: not found
... * The Bumblebee Xserver failed to start. Please check /var/log/Xorg.8.log                                                                            [fail] 
bumblebee could not be started - optirun cannot be executed.


****glxgears output:***

user1@user1:~/asus-switcheroo/bumblebee$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
user1@user1:~/asus-switcheroo/bumblebee$

dont know what else to do :/

---

### Post by joeypoey85 on 2011-08-19
here's the bumblebee error report log from /var/log/Xorg.8.log if it makes any sense to anyone

[  5362.891] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  5362.891] X Protocol Version 11, Revision 0
[  5362.891] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  5362.891] Current Operating System: Linux user1-QX310-QX410-QX510-SF310-SF410-SF510 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011 i686
[  5362.891] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=3edabdaf-4f9a-4267-b4a2-e73b2451e1fd ro quiet splash vt.handoff=7
[  5362.891] Build Date: 21 May 2011  11:38:35AM
[  5362.891] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  5362.891] Current version of pixman: 0.20.2
[  5362.891]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[  5362.891] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  5362.891] (==) Log file: "/var/log/Xorg.8.log", Time: Fri Aug 19 07:37:58 2011
[  5362.892] (++) Using config file: "/etc/X11/xorg.conf.nvidia"
[  5362.892] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  5362.892] (==) ServerLayout "Layout0"
[  5362.892] (**) |-->Screen "Screen0" (0)
[  5362.892] (**) |   |-->Monitor "Monitor0"
[  5362.893] (**) |   |-->Device "Device0"
[  5362.893] (**) Option "AutoAddDevices" "false"
[  5362.893] (**) Not automatically adding devices
[  5362.893] (==) Automatically enabling devices
[  5362.893] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  5362.893]     Entry deleted from font path.
[  5362.893] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  5362.893]     Entry deleted from font path.
[  5362.893] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  5362.893]     Entry deleted from font path.
[  5362.893] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  5362.893]     Entry deleted from font path.
[  5362.893] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  5362.893]     Entry deleted from font path.
[  5362.893] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[  5362.893] (++) ModulePath set to "/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules"
[  5362.893] (**) Extension "Composite" is enabled
[  5362.893] (==) |-->Input Device "<default pointer>"
[  5362.893] (==) |-->Input Device "<default keyboard>"
[  5362.893] (==) The core pointer device wasn't specified explicitly in the layout.
    Using the default mouse configuration.
[  5362.893] (==) The core keyboard device wasn't specified explicitly in the layout.
    Using the default keyboard configuration.
[  5362.893] (II) Loader magic: 0x81ffde0
[  5362.893] (II) Module ABI versions:
[  5362.893]     X.Org ANSI C Emulation: 0.4
[  5362.893]     X.Org Video Driver: 10.0
[  5362.894]     X.Org XInput driver : 12.3
[  5362.894]     X.Org Server Extension : 5.0
[  5362.895] (--) PCI:*(0:0:2:0) 8086:0046:144d:c08b rev 2, Mem @ 0xf3400000/4194304, 0xd0000000/268435456, I/O @ 0x0000e080/8
[  5362.895] (II) Open ACPI successful (/var/run/acpid.socket)
[  5362.895] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[  5362.895] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[  5362.895] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  5362.895] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[  5362.895] (II) "dri" will be loaded by default.
[  5362.895] (II) "dri2" will be loaded by default.
[  5362.895] (II) LoadModule: "dbe"
[  5362.896] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  5362.896] (II) Module dbe: vendor="X.Org Foundation"
[  5362.896]     compiled for 1.10.1, module version = 1.0.0
[  5362.896]     Module class: X.Org Server Extension
[  5362.896]     ABI class: X.Org Server Extension, version 5.0
[  5362.897] (II) Loading extension DOUBLE-BUFFER
[  5362.897] (II) LoadModule: "extmod"
[  5362.897] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  5362.898] (II) Module extmod: vendor="X.Org Foundation"
[  5362.898]     compiled for 1.10.1, module version = 1.0.0
[  5362.898]     Module class: X.Org Server Extension
[  5362.898]     ABI class: X.Org Server Extension, version 5.0
[  5362.898] (II) Loading extension MIT-SCREEN-SAVER
[  5362.898] (II) Loading extension XFree86-VidModeExtension
[  5362.898] (II) Loading extension XFree86-DGA
[  5362.898] (II) Loading extension DPMS
[  5362.898] (II) Loading extension XVideo
[  5362.898] (II) Loading extension XVideo-MotionCompensation
[  5362.898] (II) Loading extension X-Resource
[  5362.898] (II) LoadModule: "glx"
[  5362.898] (II) Loading /usr/lib/nvidia-current/xorg/libglx.so
[  5362.921] (II) Module glx: vendor="NVIDIA Corporation"
[  5362.921]     compiled for 4.0.2, module version = 1.0.0
[  5362.921]     Module class: X.Org Server Extension
[  5362.921] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:14:51 PDT 2011
[  5362.921] (II) Loading extension GLX
[  5362.921] (II) LoadModule: "record"
[  5362.921] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  5362.921] (II) Module record: vendor="X.Org Foundation"
[  5362.921]     compiled for 1.10.1, module version = 1.13.0
[  5362.921]     Module class: X.Org Server Extension
[  5362.921]     ABI class: X.Org Server Extension, version 5.0
[  5362.921] (II) Loading extension RECORD
[  5362.921] (II) LoadModule: "dri"
[  5362.922] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  5362.922] (II) Module dri: vendor="X.Org Foundation"
[  5362.922]     compiled for 1.10.1, module version = 1.0.0
[  5362.922]     ABI class: X.Org Server Extension, version 5.0
[  5362.922] (II) Loading extension XFree86-DRI
[  5362.922] (II) LoadModule: "dri2"
[  5362.922] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  5362.922] (II) Module dri2: vendor="X.Org Foundation"
[  5362.922]     compiled for 1.10.1, module version = 1.2.0
[  5362.922]     ABI class: X.Org Server Extension, version 5.0
[  5362.922] (II) Loading extension DRI2
[  5362.922] (II) LoadModule: "nvidia"
[  5362.922] (II) Loading /usr/lib/nvidia-current/xorg/nvidia_drv.so
[  5362.923] (II) Module nvidia: vendor="NVIDIA Corporation"
[  5362.923]     compiled for 4.0.2, module version = 1.0.0
[  5362.923]     Module class: X.Org Video Driver
[  5362.923] (II) LoadModule: "mouse"
[  5362.923] (II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
[  5362.923] (II) Module mouse: vendor="X.Org Foundation"
[  5362.923]     compiled for 1.9.99.902, module version = 1.6.99
[  5362.923]     Module class: X.Org XInput Driver
[  5362.923]     ABI class: X.Org XInput driver, version 12.3
[  5362.923] (II) LoadModule: "kbd"
[  5362.923] (WW) Warning, couldn't open module kbd
[  5362.923] (II) UnloadModule: "kbd"
[  5362.923] (II) Unloading kbd
[  5362.923] (EE) Failed to load module "kbd" (module does not exist, 0)
[  5362.923] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:57:12 PDT 2011
[  5362.923] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  5362.923] (--) using VT number 7

[  5362.923] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[  5362.924] (EE) No devices detected.
[  5362.924] 
Fatal server error:
[  5362.924] no screens found
[  5362.924] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  5362.924] Please also check the log file at "/var/log/Xorg.8.log" for additional information.
[  5362.924]

---

### Post by Duncan Williams on 2011-08-19
Probably need to purge all existing video drivers and then correctly install nvidia drivers. From the standard repository (at first). and make sure you have disabled `onboard video' in BIOS.

---

### Post by joeypoey85 on 2011-08-19
> **Duncan Williams said:**
> Probably need to purge all existing video drivers and then correctly install nvidia drivers. From the standard repository (at first). and make sure you have disabled `onboard video' in BIOS.

thanks for the replies guys.

i used the purge command to get rid of all nvidia (" apt-get remove --purge nvidia* ") before installing the nvidia-current. i will try installing from the repository see if that makes a difference.

also i checked and im pretty sure theres no option for anything related to video in my bios, but i could double check. ill also check if theres any bios updates for my computer though i doubt it cus its fairly new.

edit: also going to try the bumblebee steps again (from [http://linux-hybrid-graphics.blogspot.com/2011/05/testers-needed-intelnvidia-bumblebee.html](http://linux-hybrid-graphics.blogspot.com/2011/05/testers-needed-intelnvidia-bumblebee.html)) after purging, worth a shot :p

---

### Post by joeypoey85 on 2011-08-20
ok i tried purging and installing nvidia-current from the repository like you said. also tried the bumblebee again after purging, about to do a bios update and reboot. dont know what else to do..

anyone have any suggestions?

waiting patiently.
joe

---

### Post by Duncan Williams on 2011-08-20
[http://ubuntuforums.org/showthread.php?t=1392766](http://ubuntuforums.org/showthread.php?t=1392766)

[http://www.nvidia.com/object/product_geforce_310_us.html](http://www.nvidia.com/object/product_geforce_310_us.html)

---

### Post by joeypoey85 on 2011-08-20
> **Duncan Williams said:**
> [http://ubuntuforums.org/showthread.php?t=1392766](http://ubuntuforums.org/showthread.php?t=1392766)

[http://www.nvidia.com/object/product_geforce_310_us.html](http://www.nvidia.com/object/product_geforce_310_us.html)

i'm going to try that sony edid information bin file, i tried the custom EDID that i extracted from windows.

and the second link you posted is for the nvidia310, my card is a 310m (edit: chip sorry)

---

### Post by Duncan Williams on 2011-08-20
[http://www.nvidia.com/object/product_geforce_310m_us.html](http://www.nvidia.com/object/product_geforce_310m_us.html)

---

### Post by Duncan Williams on 2011-08-20
[IMG]http://files.myopera.com/DuncanWilliams/usercss/310m.png[/IMG]

---

### Post by Duncan Williams on 2011-08-20
[IMG]http://files.myopera.com/DuncanWilliams/usercss/310m-linux.png[/IMG]

---

### Post by Duncan Williams on 2011-08-20
sorry for the double post, first screenshot was for windows, duhhhh..

---

### Post by joeypoey85 on 2011-08-30
I've tried about everything I can think of at this point. Thinking about trying a different ubuntu version.

Edit: 
Maybe 10.04?

Anyone know a version that might work for my NVIDIA 310M graphics chip for my Samsung SF550 laptop?

or have any idea of something else I could try?

---

### Post by Hakunka-Matata on 2011-08-30
+1 on 10.04, or 10.10, I actually do like them better on days I just need to get things done.
That being said, through all the posts on this thread there is no reference to the **Sticky** [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
 
That thread has HEAPS of discussion on graphics gotchas
Good Luck

BTW:  what does ```
sudo lshw -C display
``` show.

---

