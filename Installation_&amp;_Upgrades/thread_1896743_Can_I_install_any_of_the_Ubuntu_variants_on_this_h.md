---
title: "Can I install any of the Ubuntu variants on this hardware?"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by Cyberdot on 2011-12-17
Hello all!

I want to set up a new computer for my new Chinese au-pair.
Is the following hardware powerful enough to run any of the Ubuntu variants at a decent speed?

description: Motherboard
        product: MS-6714
description: USB Controller
        product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
description: Host bridge
        product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
description: CPU
        product: Intel(R) Celeron(R) CPU 2.00GHz
        size: 2280MHz
        width: 32 bits
        clock: 114MHz
description: DIMM
        slot: DIMM1
        size: 1024MiB
        slot: DIMM2
        size: 512MiB
description: VGA compatible controller
        product: NV17 [GeForce4 MX 440]
description: ATA Disk
        product: ST380011A
        size: 74GiB (80GB)

I know this is old and slow, but it will only be used for Internet surfing, QQ and skype for chatting as well as watching some videos. Is this machine powerful enough to run any of the newer releases, or should I look back for an old Ubuntu release?

Thanks for any replies.

---

### Post by MAFoElffen on 2011-12-17
> **Cyberdot said:**
> Hello all!

I want to set up a new computer for my new Chinese au-pair.
Is the following hardware powerful enough to run any of the Ubuntu variants at a decent speed?

description: Motherboard
        product: MS-6714
description: USB Controller
        product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
description: Host bridge
        product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
description: CPU
        product: Intel(R) Celeron(R) CPU 2.00GHz
        size: 2280MHz
        width: 32 bits
        clock: 114MHz
description: DIMM
        slot: DIMM1
        size: 1024MiB
        slot: DIMM2
        size: 512MiB
description: VGA compatible controller
        product: NV17 [GeForce4 MX 440]
description: ATA Disk
        product: ST380011A
        size: 74GiB (80GB)

I know this is old and slow, but it will only be used for Internet surfing, QQ and skype for chatting as well as watching some videos. Is this machine powerful enough to run any of the newer releases, or should I look back for an old Ubuntu release?

Thanks for any replies.
Welcome to Ubuntu...

Yes, it will run all variants. With your graphics (NV17) use "nomodeset" as a boot option for the LiveCD and on the first reboot. Additional Drivers should show the Nouveau Experimental 3D driver, use that. The driver is better than any other for that GPU. Even then, in Ubuntu, it won't run Unity 3D or Gnome3... but will still run Unity 2D and Gnome3 Classic.

In the other Variants, you won't have any difference with graphics.

---

### Post by JC Cheloven on 2011-12-17
A single thing to add: for old hardware you will probably get a more responsive system with [LUbuntu]("http://lubuntu.net/"). It's what it is meant for.

JC

---

### Post by Cyberdot on 2011-12-17
> **MAFoElffen said:**
> Welcome to Ubuntu...

Yes, it will run all variants. With your graphics (NV17) use "nomodeset" as a boot option for the LiveCD and on the first reboot. Additional Drivers should show the Nouveau Experimental 3D driver, use that. The driver is better than any other for that GPU. Even then, in Ubuntu, it won't run Unity 3D or Gnome3... but will still run Unity 2D and Gnome3 Classic.

In the other Variants, you won't have any difference with graphics.

Thank you for your very quick reply. I forgot to say I have already tried Ubuntu 11.10 using live-USB. But graphics was very slow. Menu is slow. Moving windows is also slow, maybe only 1 fps. And of course not able to watch video online, not even 360p using Youtube (I would guess 4-6 fps). I suspect this is a driver issue unless Ubuntu 11.10 is just very heavy to run. I will try again and look for the Nouveau driver, rather than the Nvidia 96.47.13 I used.

I am sorry to ask this, but how do I use the "nomodeset" when booting the live-USB, and will this affect the graphics performance?

---

### Post by Cyberdot on 2011-12-17
> **JC Cheloven said:**
> A single thing to add: for old hardware you will probably get a more responsive system with [LUbuntu]("http://lubuntu.net/"). It's what it is meant for.

JC

Thanks for this suggestion. I am downloading Lubuntu 11.10 now...

---

### Post by Cyberdot on 2011-12-17
I have found the Nomodeset option using F6 before booting from USB. I feel it did not change anything for me?. In "Additional Drivers" I found no Nouveau driver. How do I install this?

To explain how slow the graphics is in Ubuntu 11.10, In Firefox when I type text at normal speed the computer can not keep up. Also the main menu takes several seconds to show...

---

### Post by Cyberdot on 2011-12-17
As the motherboard (MS-6714 Ver. 1) also have onboard graphics I tried to remove the Geforce card. After booting back into Ubuntu 11.10 the menu might be more responsive, but it's still to slow to be useable. Watching a video on Youtube is even more slow than on the nvidia. Only a few fps...

I still did not see any drivers in "Additional Drivers" for the onboard graphics. Can I find something using the package manager?

Also I noticed I have no sound. In the "Sound settings..." there is no devices listed under the "Hardware" tab. I need drivers for this also?

---

### Post by MAFoElffen on 2011-12-17
> **Cyberdot said:**
> I have found the Nomodeset option using F6 before booting from USB. I feel it did not change anything for me?. In "Additional Drivers" I found no Nouveau driver. How do I install this?

To explain how slow the graphics is in Ubuntu 11.10, In Firefox when I type text at normal speed the computer can not keep up. Also the main menu takes several seconds to show...
Look in your /var/log/Xorg.0.log file (or post here) to see if it is using Nouveau.  I fjust went through the change logs and it looks like Nouveau incorporated what was in Nouveau Experimental 3D and Now it's just "Nouveau."  If it's not being used, you could point it to it with an boiler plate xorg.conf file.

It that errored, then check for the files or just reinstall it:
```

sudo apt-get install xserver-xorg-video-nouveau libdrm-nouveau1a nouveau-firmware

```
As with the graphics being slow... I have an NV10 and an NV20.  People Gave me these to do dev testing.  They are slow.  If you use the NV driver, it's painful. The nouveau driver is better (still crawling compared to my SLI boxes!!!) but best graphics with those cards. Vesa is the best speed with that card, but the graphics are really grainy...

As I've told customers and friends, the best noticeable performance increase per dollar investment is in your graphics card.

Yes, Lubuntu is low overhead. Then Xubuntu. Then Ubuntu. Ubuntu in the past 2 versions, is very graphical... But you can still turn off those effects. The base on all 3 of those is still Ubuntu, with a different desktop package...

You bottle neck in resources is not memory, processor... rather the graphics.

---

### Post by Cyberdot on 2011-12-18
Thank you very much for your suggestions MAFoElffen.

I have tried out Lubuntu 11.10. Except for the many programs have "problems" and updates not working, it really performs better than Ubuntu 11.10. Better does not mean it's fast, only that menu's and browser both feel more responsive. (Also, I think it's a beautiful desktop when I moved the menu-panel to the top of the screen, looked almost like Gnome). But maybe not a fair comparison because Lubuntu use the faster Chromium browser. Still, it's not capable for watching a Youtube video of only 360p, and still too slow for general web surfing.

I checked the Xorg.0.log file (in Lubuntu), it had many Nouveau lines, so I think this is the driver in use. If this is the best driver for the NV17 card, and there is no options or settings to make it faster, we can agree that this card can not have a future without Windows.

Back to using on-board graphics, the Xorg.0.log said "Intel(R) 845G". Anything I can do to make this one faster?
And can I make the on-board AC97 sound working?

---

### Post by Cyberdot on 2011-12-18
Now I have tried the older Ubuntu 11.04 in Classic mode. It's really faster than 11.10, I feel same speed as Lubuntu 11.10. The menu's does still have lag, and I can type faster than the computer can update the screen. But when using the onboard Intel graphics, it's almost usable now. I can move windows without any delays. Also can scroll on web-pages in acceptable speed. But still can not do video playback more than 240p. 360p already have problems, and full-screen will move at maybe 6-10fps. I have tried to use HTML5 and not Abobe flash for video's, but I see no difference.

MAFoElffen, can you remember if you can watch any web-based movies on you NV10-NV20 cards?

---

### Post by MAFoElffen on 2011-12-18
> **Cyberdot said:**
> Thank you very much for your suggestions MAFoElffen.

I have tried out Lubuntu 11.10. Except for the many programs have "problems" and updates not working, it really performs better than Ubuntu 11.10. Better does not mean it's fast, only that menu's and browser both feel more responsive. (Also, I think it's a beautiful desktop when I moved the menu-panel to the top of the screen, looked almost like Gnome). But maybe not a fair comparison because Lubuntu use the faster Chromium browser. Still, it's not capable for watching a Youtube video of only 360p, and still too slow for general web surfing.

I checked the Xorg.0.log file (in Lubuntu), it had many Nouveau lines, so I think this is the driver in use. If this is the best driver for the NV17 card, and there is no options or settings to make it faster, we can agree that this card can not have a future without Windows.

Back to using on-board graphics, the Xorg.0.log said "Intel(R) 845G". Anything I can do to make this one faster?
And can I make the on-board AC97 sound working?
The onboard AC97 should work out of the box. (default settings have it muted, change them)

The onboard Intel 845G (i810 class) will work if you pull your NVidia card and connect a monitor to it.  Unfortunately, you may find that it's even slower than the nVidia NV17.

---

### Post by JC Cheloven on 2011-12-18
> **Cyberdot said:**
> 
I have tried out Lubuntu 11.10. Except for the many programs have "problems" and updates not working, it really performs better than Ubuntu 11.10. Better does not mean it's fast, only that menu's and browser both feel more responsive. 
We can try to solve those side problems. Perhaps some of them are merely a matter of configuration. 
Lubuntu should be more than responsive with your specs. If not, there is for sure an issue with your hardware drivers, most likely your gpu.

> (Also, I think it's a beautiful desktop when I moved the menu-panel to the top of the screen, looked almost like Gnome). 
:)

> But maybe not a fair comparison because Lubuntu use the faster Chromium browser. Still, it's not capable for watching a Youtube video of only 360p, and still too slow for general web surfing.
Be aware that perhaps flash is itself too heavy for your pc. But general surfing should be ok, either with firefox or chromium. Again the probable gpu issue.

> I checked the Xorg.0.log file (in Lubuntu), it had many Nouveau lines, so I think this is the driver in use. If this is the best driver for the NV17 card, and there is no options or settings to make it faster, we can agree that this card can not have a future without Windows.
Back to using on-board graphics, the Xorg.0.log said "Intel(R) 845G". Anything I can do to make this one faster?

Could you please post back the output of the command ```
lspci
``` at terminal, to see in a familiar (for me) format what you exactly have inside your box? Perhaps we could be more confident about ourselves that way ;) I expect to see something as "Intel 82845G VGA compatible controller", which [should have good support]("http://www.intel.com/support/graphics/sb/cs-010512.htm"). Also, instead of NV17 I expect to see something as GeForce256...

> And can I make the on-board AC97 sound working?
First try the simplest: in a terminal type ```
alsamixer
``` You'll be presented with a simple but functional mixer interface. Please read in the upper lines your card, and some tips. Then navigate to the apropriate item (perhaps "pc speakers") and raise the volume if it's muted. No joke.
If that doesn't work, [this]("http://www.ehow.com/how_7321451_install-media-ac97-linux.html") may be of help. 

JC

---

### Post by JC Cheloven on 2011-12-18
Oops several posts while I typed in!

> **Cyberdot said:**
> Now I have tried the older Ubuntu 11.04 in Classic mode. It's really faster than 11.10, I feel same speed as Lubuntu 11.10. The menu's does still have lag, and I can type faster than the computer can update the screen. But when using the onboard Intel graphics, it's almost usable now. I can move windows without any delays. Also can scroll on web-pages in acceptable speed. But still can not do video playback more than 240p. 360p already have problems, and full-screen will move at maybe 6-10fps. I have tried to use HTML5 and not Abobe flash for video's, but I see no difference.
IMO, "almost usable" is not an acceptable standard in your case. You should get a perfectly functional system, except perhaps for flash. Let's see if we can get there.
Also, any 11.04 -buntu was probably more responsive due to a linux kernel matter. In particular Lubuntu 11.04. But I was about to suggest you to try an even lighter distro called [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm"), it may give you a positive surprise (did for me).

---

### Post by MAFoElffen on 2011-12-18
> **Cyberdot said:**
> Now I have tried the older Ubuntu 11.04 in Classic mode. It's really faster than 11.10, I feel same speed as Lubuntu 11.10. The menu's does still have lag, and I can type faster than the computer can update the screen. But when using the onboard Intel graphics, it's almost usable now. I can move windows without any delays. Also can scroll on web-pages in acceptable speed. But still can not do video playback more than 240p. 360p already have problems, and full-screen will move at maybe 6-10fps. I have tried to use HTML5 and not Abobe flash for video's, but I see no difference.

MAFoElffen, can you remember if you can watch any web-based movies on you NV10-NV20 cards?
Yes, but a bit slow compared to others with better graphics cards. Just to be expected.  You know you can install Google Chrome on any variant right? Flash seems better on that browser.

---

### Post by Cyberdot on 2011-12-19
> **MAFoElffen said:**
> The onboard Intel 845G (i810 class) will work if you pull your NVidia card and connect a monitor to it.  Unfortunately, you may find that it's even slower than the nVidia NV17.

Sir, this is exactly what I have done. I pulled out the Geforce4 card and connected the monitor to the on-board VGA connector.

Performance vise, I am very sure it performed better than the Geforce4 card using both the stock drivers (Nouveau?) and the NV drivers (Nvidia proprietary). The menu and OS itself felt more responsive. Scrolling using both Firefox and Chromium was also more smooth. However, playing video was very slow on both. This is my feeling after testing Ubuntu 11.10, Ubuntu 11.04, Ubuntu 10.04.3 and Lubuntu 11.10.

I believe when all things is correct, then Nvidia card should be much faster than the simple on-board graphics controller!?

---

### Post by Cyberdot on 2011-12-19
> **MAFoElffen said:**
> Yes, but a bit slow compared to others with better graphics cards. Just to be expected.

By slow, you meaning it can not play it smooth, or you mean that full-screen video is completely unwatchable, playing at 2 to 6fps at most (360p resolution)?

> **MAFoElffen said:**
> You know you can install Google Chrome on any variant right? Flash seems better on that browser.

Yes, sure. I tried Chromium on Ubuntu as well. I feel it's faster than Firefox. Also I have tried HTML5 videos to avoid flash. Same slow playback.

---

### Post by Cyberdot on 2011-12-19
> **JC Cheloven said:**
> Oops several posts while I typed in!


IMO, "almost usable" is not an acceptable standard in your case. You should get a perfectly functional system, except perhaps for flash. Let's see if we can get there.
Also, any 11.04 -buntu was probably more responsive due to a linux kernel matter. In particular Lubuntu 11.04. But I was about to suggest you to try an even lighter distro called [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm"), it may give you a positive surprise (did for me).

Thank you for all your feedback.
You are correct, I feel the speed is really not acceptable. I know the hardware is very slow, but when basic surfing and video can be achieved at a decent performance using Windows, I hoped to get the same performance using Ubuntu.

I noticed Ubuntu 11.04 was significantly faster than Ubuntu 11.10. Speed same as Lubuntu 11.10. Based on this, I installed Ubuntu 10.04.3 last night. It performed even better. And menu and overall responsiveness is now at an acceptable level. But then there is the video playback issue. In Ubuntu 10.04 maybe it was even slower than Ubuntu 11.04.

I am taking your advice. Now I am downloading Lubuntu 11.04. Should I expect better performance than Ubuntu 10.04.3?

Puppy linux, can I make a bootable USB within Ubuntu?
I have downloaded the Ubuntu-package compatible version 5.2.8. Is this correct?

---

### Post by Cyberdot on 2011-12-19
This is when booting from a fresh Lubuntu 11.04 USB-stick:

```
ubuntu@ubuntu:~$ alsamixer
cannot open mixer: No such file or directory
```

```
ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
Xorg.0.log:
```
[    45.493] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    45.494] X Protocol Version 11, Revision 0
[    45.494] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    45.500] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    45.500] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    45.500] Build Date: 19 April 2011  03:33:17PM
[    45.500] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    45.505] Current version of pixman: 0.20.2
[    45.505] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    45.505] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.513] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 19 16:11:02 2011
[    45.542] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.584] (==) No Layout section.  Using the first Screen section.
[    45.584] (==) No screen section available. Using defaults.
[    45.584] (**) |-->Screen "Default Screen Section" (0)
[    45.584] (**) |   |-->Monitor "<default monitor>"
[    45.667] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    45.668] (==) Automatically adding devices
[    45.668] (==) Automatically enabling devices
[    45.674] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.674] 	Entry deleted from font path.
[    45.674] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    45.675] 	Entry deleted from font path.
[    45.675] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    45.675] 	Entry deleted from font path.
[    45.675] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    45.675] 	Entry deleted from font path.
[    45.675] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    45.675] 	Entry deleted from font path.
[    45.675] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    45.675] 	Entry deleted from font path.
[    45.676] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    45.676] 	Entry deleted from font path.
[    45.676] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	built-ins
[    45.676] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.676] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.676] (II) Loader magic: 0x81ffde0
[    45.676] (II) Module ABI versions:
[    45.676] 	X.Org ANSI C Emulation: 0.4
[    45.676] 	X.Org Video Driver: 10.0
[    45.676] 	X.Org XInput driver : 12.3
[    45.676] 	X.Org Server Extension : 5.0
[    45.705] (--) PCI:*(0:1:0:0) 10de:0171:0000:0000 rev 163, Mem @ 0xe8000000/16777216, 0xd8000000/134217728, 0xe0000000/524288, BIOS @ 0x????????/131072
[    45.705] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    45.708] (II) LoadModule: "extmod"
[    45.741] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    45.768] (II) Module extmod: vendor="X.Org Foundation"
[    45.768] 	compiled for 1.10.1, module version = 1.0.0
[    45.768] 	Module class: X.Org Server Extension
[    45.768] 	ABI class: X.Org Server Extension, version 5.0
[    45.768] (II) Loading extension MIT-SCREEN-SAVER
[    45.768] (II) Loading extension XFree86-VidModeExtension
[    45.768] (II) Loading extension XFree86-DGA
[    45.768] (II) Loading extension DPMS
[    45.768] (II) Loading extension XVideo
[    45.769] (II) Loading extension XVideo-MotionCompensation
[    45.769] (II) Loading extension X-Resource
[    45.769] (II) LoadModule: "dbe"
[    45.770] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    45.780] (II) Module dbe: vendor="X.Org Foundation"
[    45.780] 	compiled for 1.10.1, module version = 1.0.0
[    45.781] 	Module class: X.Org Server Extension
[    45.781] 	ABI class: X.Org Server Extension, version 5.0
[    45.781] (II) Loading extension DOUBLE-BUFFER
[    45.781] (II) LoadModule: "glx"
[    45.790] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    45.826] (II) Module glx: vendor="X.Org Foundation"
[    45.826] 	compiled for 1.10.1, module version = 1.0.0
[    45.826] 	ABI class: X.Org Server Extension, version 5.0
[    45.829] (==) AIGLX enabled
[    45.829] (II) Loading extension GLX
[    45.829] (II) LoadModule: "record"
[    45.933] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    45.944] (II) Module record: vendor="X.Org Foundation"
[    45.944] 	compiled for 1.10.1, module version = 1.13.0
[    45.944] 	Module class: X.Org Server Extension
[    45.944] 	ABI class: X.Org Server Extension, version 5.0
[    45.945] (II) Loading extension RECORD
[    45.945] (II) LoadModule: "dri"
[    45.946] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    45.971] (II) Module dri: vendor="X.Org Foundation"
[    45.971] 	compiled for 1.10.1, module version = 1.0.0
[    45.971] 	ABI class: X.Org Server Extension, version 5.0
[    45.971] (II) Loading extension XFree86-DRI
[    45.972] (II) LoadModule: "dri2"
[    45.973] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    45.978] (II) Module dri2: vendor="X.Org Foundation"
[    45.980] 	compiled for 1.10.1, module version = 1.2.0
[    45.980] 	ABI class: X.Org Server Extension, version 5.0
[    45.980] (II) Loading extension DRI2
[    45.980] (==) Matched nvidia as autoconfigured driver 0
[    45.980] (==) Matched nouveau as autoconfigured driver 1
[    45.980] (==) Matched nv as autoconfigured driver 2
[    45.980] (==) Matched vesa as autoconfigured driver 3
[    45.980] (==) Matched fbdev as autoconfigured driver 4
[    45.980] (==) Assigned the driver to the xf86ConfigLayout
[    45.981] (II) LoadModule: "nvidia"
[    46.000] (WW) Warning, couldn't open module nvidia
[    46.000] (II) UnloadModule: "nvidia"
[    46.000] (II) Unloading nvidia
[    46.000] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    46.000] (II) LoadModule: "nouveau"
[    46.001] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    46.518] (II) Module nouveau: vendor="X.Org Foundation"
[    46.518] 	compiled for 1.10.0, module version = 0.0.16
[    46.518] 	Module class: X.Org Video Driver
[    46.518] 	ABI class: X.Org Video Driver, version 10.0
[    46.518] (II) LoadModule: "nv"
[    46.520] (WW) Warning, couldn't open module nv
[    46.520] (II) UnloadModule: "nv"
[    46.520] (II) Unloading nv
[    46.520] (EE) Failed to load module "nv" (module does not exist, 0)
[    46.521] (II) LoadModule: "vesa"
[    46.521] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    46.740] (II) Module vesa: vendor="X.Org Foundation"
[    46.740] 	compiled for 1.10.0, module version = 2.3.0
[    46.740] 	Module class: X.Org Video Driver
[    46.740] 	ABI class: X.Org Video Driver, version 10.0
[    46.740] (II) LoadModule: "fbdev"
[    46.741] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    46.758] (II) Module fbdev: vendor="X.Org Foundation"
[    46.759] 	compiled for 1.10.0, module version = 0.4.2
[    46.759] 	ABI class: X.Org Video Driver, version 10.0
[    46.759] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    46.759] (II) NOUVEAU driver for NVIDIA chipset families :
[    46.759] 	RIVA TNT    (NV04)
[    46.759] 	RIVA TNT2   (NV05)
[    46.759] 	GeForce 256 (NV10)
[    46.759] 	GeForce 2   (NV11, NV15)
[    46.759] 	GeForce 4MX (NV17, NV18)
[    46.759] 	GeForce 3   (NV20)
[    46.759] 	GeForce 4Ti (NV25, NV28)
[    46.759] 	GeForce FX  (NV3x)
[    46.760] 	GeForce 6   (NV4x)
[    46.760] 	GeForce 7   (G7x)
[    46.760] 	GeForce 8   (G8x)
[    46.760] (II) VESA: driver for VESA chipsets: vesa
[    46.760] (II) FBDEV: driver for framebuffer: fbdev
[    46.760] (++) using VT number 7

[    46.763] drmOpenDevice: node name is /dev/dri/card0
[    46.763] drmOpenDevice: open result is 10, (OK)
[    46.763] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    46.763] drmOpenDevice: node name is /dev/dri/card0
[    46.763] drmOpenDevice: open result is 10, (OK)
[    46.763] drmOpenByBusid: drmOpenMinor returns 10
[    46.763] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    46.763] (II) [drm] nouveau interface version: 0.0.16
[    46.764] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    46.764] (WW) Falling back to old probe method for vesa
[    46.764] (WW) Falling back to old probe method for fbdev
[    46.764] (II) Loading sub module "fbdevhw"
[    46.764] (II) LoadModule: "fbdevhw"
[    46.766] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    46.829] (II) Module fbdevhw: vendor="X.Org Foundation"
[    46.829] 	compiled for 1.10.1, module version = 0.0.2
[    46.829] 	ABI class: X.Org Video Driver, version 10.0
[    46.829] (II) Loading sub module "dri"
[    46.829] (II) LoadModule: "dri"
[    46.830] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    46.831] (II) Module dri: vendor="X.Org Foundation"
[    46.831] 	compiled for 1.10.1, module version = 1.0.0
[    46.831] 	ABI class: X.Org Server Extension, version 5.0
[    46.831] (II) NOUVEAU(0): Loaded DRI module
[    46.831] drmOpenDevice: node name is /dev/dri/card0
[    46.831] drmOpenDevice: open result is 12, (OK)
[    46.831] drmOpenDevice: node name is /dev/dri/card0
[    46.831] drmOpenDevice: open result is 12, (OK)
[    46.831] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    46.834] drmOpenDevice: node name is /dev/dri/card0
[    46.834] drmOpenDevice: open result is 12, (OK)
[    46.834] drmOpenByBusid: drmOpenMinor returns 12
[    46.834] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    46.835] (II) [drm] DRM interface version 1.4
[    46.835] (II) [drm] DRM open master succeeded.
[    46.835] (--) NOUVEAU(0): Chipset: "NVIDIA NV17"
[    46.835] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    46.835] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    46.835] (==) NOUVEAU(0): RGB weight 888
[    46.835] (==) NOUVEAU(0): Default visual is TrueColor
[    46.835] (==) NOUVEAU(0): Using HW cursor
[    46.835] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[    47.097] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    47.152] (II) NOUVEAU(0): Output TV-1 has no monitor section
[    47.324] (II) NOUVEAU(0): EDID for output VGA-1
[    47.324] (II) NOUVEAU(0): Manufacturer: ENC  Model: 1743  Serial#: 16843009
[    47.324] (II) NOUVEAU(0): Year: 2005  Week: 10
[    47.324] (II) NOUVEAU(0): EDID Version: 1.3
[    47.324] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    47.324] (II) NOUVEAU(0): Sync:  Separate
[    47.324] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 34  vert.: 28
[    47.324] (II) NOUVEAU(0): Gamma: 2.20
[    47.325] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    47.325] (II) NOUVEAU(0): First detailed timing is preferred mode
[    47.325] (II) NOUVEAU(0): redX: 0.635 redY: 0.337   greenX: 0.287 greenY: 0.613
[    47.325] (II) NOUVEAU(0): blueX: 0.144 blueY: 0.086   whiteX: 0.313 whiteY: 0.329
[    47.325] (II) NOUVEAU(0): Supported established timings:
[    47.325] (II) NOUVEAU(0): 720x400@70Hz
[    47.325] (II) NOUVEAU(0): 640x480@60Hz
[    47.325] (II) NOUVEAU(0): 640x480@67Hz
[    47.325] (II) NOUVEAU(0): 640x480@72Hz
[    47.325] (II) NOUVEAU(0): 640x480@75Hz
[    47.325] (II) NOUVEAU(0): 800x600@56Hz
[    47.325] (II) NOUVEAU(0): 800x600@60Hz
[    47.325] (II) NOUVEAU(0): 800x600@72Hz
[    47.325] (II) NOUVEAU(0): 800x600@75Hz
[    47.325] (II) NOUVEAU(0): 832x624@75Hz
[    47.326] (II) NOUVEAU(0): 1024x768@60Hz
[    47.326] (II) NOUVEAU(0): 1024x768@70Hz
[    47.326] (II) NOUVEAU(0): 1024x768@75Hz
[    47.326] (II) NOUVEAU(0): 1280x1024@75Hz
[    47.326] (II) NOUVEAU(0): 1152x864@75Hz
[    47.326] (II) NOUVEAU(0): Manufacturer's mask: 0
[    47.326] (II) NOUVEAU(0): Supported standard timings:
[    47.326] (II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    47.326] (II) NOUVEAU(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    47.326] (II) NOUVEAU(0): #2: hsize: 1280  vsize 960  refresh: 75  vid: 20353
[    47.326] (II) NOUVEAU(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    47.326] (II) NOUVEAU(0): Supported detailed timing:
[    47.326] (II) NOUVEAU(0): clock: 108.0 MHz   Image Size:  338 x 271 mm
[    47.326] (II) NOUVEAU(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    47.327] (II) NOUVEAU(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    47.327] (II) NOUVEAU(0): Serial No: 37993035
[    47.327] (II) NOUVEAU(0): Ranges: V min: 50 V max: 76 Hz, H min: 24 H max: 80 kHz, PixClock max 145 MHz
[    47.327] (II) NOUVEAU(0): Monitor name: L551
[    47.327] (II) NOUVEAU(0): EDID (in hex):
[    47.327] (II) NOUVEAU(0): 	00ffffffffffff0015c3431701010101
[    47.327] (II) NOUVEAU(0): 	0a0f010368221c78ea98c5a256499d24
[    47.327] (II) NOUVEAU(0): 	165054bfef8081808140814f714f0101
[    47.327] (II) NOUVEAU(0): 	010101010101302a009851002a403070
[    47.327] (II) NOUVEAU(0): 	1300520f1100001e000000ff00333739
[    47.327] (II) NOUVEAU(0): 	39333033350a20202020000000fd0032
[    47.327] (II) NOUVEAU(0): 	4c18500e000a202020202020000000fc
[    47.327] (II) NOUVEAU(0): 	004c3535310a20202020202020200042
[    47.327] (II) NOUVEAU(0): EDID vendor "ENC", prod id 5955
[    47.332] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    47.332] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    47.332] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    47.332] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    47.332] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    47.332] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    47.332] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    47.332] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    47.332] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    47.332] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    47.333] (II) NOUVEAU(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
[    47.334] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[    47.334] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    47.334] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    47.334] (II) NOUVEAU(0): Modeline "1280x960"x75.0  129.94  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
[    47.334] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    47.334] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    47.334] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    47.334] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    47.334] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    47.334] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    47.334] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    47.335] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    47.335] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    47.335] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    47.335] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    47.335] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    47.335] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    47.335] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    47.335] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    47.388] (II) NOUVEAU(0): EDID for output TV-1
[    47.388] (II) NOUVEAU(0): Output VGA-1 connected
[    47.388] (II) NOUVEAU(0): Output TV-1 disconnected
[    47.388] (II) NOUVEAU(0): Using exact sizes for initial modes
[    47.388] (II) NOUVEAU(0): Output VGA-1 using initial mode 1280x1024
[    47.388] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    47.388] (--) NOUVEAU(0): Virtual size is 1280x1024 (pitch 0)
[    47.388] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[    47.388] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    47.388] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[    47.389] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    47.389] (**) NOUVEAU(0):  Mode "1280x960": 129.9 MHz (scaled from 0.0 MHz), 75.2 kHz, 75.0 Hz
[    47.389] (II) NOUVEAU(0): Modeline "1280x960"x75.0  129.94  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
[    47.389] (**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[    47.389] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    47.389] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[    47.389] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    47.389] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[    47.389] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    47.389] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[    47.389] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    47.390] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    47.390] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    47.390] (**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
[    47.390] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    47.390] (**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
[    47.390] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    47.390] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    47.390] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    47.390] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    47.390] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    47.390] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    47.391] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    47.391] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
[    47.391] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    47.391] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[    47.391] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    47.391] (**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
[    47.391] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    47.391] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    47.392] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    47.392] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[    47.392] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    47.392] (**) NOUVEAU(0): Display dimensions: (340, 280) mm
[    47.392] (**) NOUVEAU(0): DPI set to (95, 92)
[    47.392] (II) Loading sub module "fb"
[    47.392] (II) LoadModule: "fb"
[    47.402] (II) Loading /usr/lib/xorg/modules/libfb.so
[    47.417] (II) Module fb: vendor="X.Org Foundation"
[    47.417] 	compiled for 1.10.1, module version = 1.0.0
[    47.417] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    47.417] (II) Loading sub module "exa"
[    47.417] (II) LoadModule: "exa"
[    47.418] (II) Loading /usr/lib/xorg/modules/libexa.so
[    47.432] (II) Module exa: vendor="X.Org Foundation"
[    47.432] 	compiled for 1.10.1, module version = 2.5.0
[    47.432] 	ABI class: X.Org Video Driver, version 10.0
[    47.432] (II) Loading sub module "shadowfb"
[    47.432] (II) LoadModule: "shadowfb"
[    47.434] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    47.457] (II) Module shadowfb: vendor="X.Org Foundation"
[    47.457] 	compiled for 1.10.1, module version = 1.0.0
[    47.457] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    47.457] (II) UnloadModule: "vesa"
[    47.457] (II) Unloading vesa
[    47.457] (II) UnloadModule: "fbdev"
[    47.457] (II) Unloading fbdev
[    47.458] (II) UnloadModule: "fbdevhw"
[    47.458] (II) Unloading fbdevhw
[    47.458] (--) Depth 24 pixmap format is 32 bpp
[    47.459] (II) NOUVEAU(0): Opened GPU channel 1
[    47.472] (II) NOUVEAU(0): [DRI2] Setup complete
[    47.472] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau_vieux
[    47.472] (II) NOUVEAU(0): GART: 128MiB available
[    47.507] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[    47.706] (II) EXA(0): Driver allocated offscreen pixmaps
[    47.706] (II) EXA(0): Driver registered support for the following operations:
[    47.706] (II)         Solid
[    47.707] (II)         Copy
[    47.707] (II)         Composite (RENDER acceleration)
[    47.707] (II)         UploadToScreen
[    47.707] (II)         DownloadFromScreen
[    47.707] (==) NOUVEAU(0): Backing store disabled
[    47.707] (==) NOUVEAU(0): Silken mouse enabled
[    47.707] (==) NOUVEAU(0): DPMS enabled
[    47.707] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    47.719] (--) RandR disabled
[    47.720] (II) Initializing built-in extension Generic Event Extension
[    47.720] (II) Initializing built-in extension SHAPE
[    47.720] (II) Initializing built-in extension MIT-SHM
[    47.720] (II) Initializing built-in extension XInputExtension
[    47.720] (II) Initializing built-in extension XTEST
[    47.720] (II) Initializing built-in extension BIG-REQUESTS
[    47.720] (II) Initializing built-in extension SYNC
[    47.720] (II) Initializing built-in extension XKEYBOARD
[    47.720] (II) Initializing built-in extension XC-MISC
[    47.720] (II) Initializing built-in extension SECURITY
[    47.720] (II) Initializing built-in extension XINERAMA
[    47.720] (II) Initializing built-in extension XFIXES
[    47.720] (II) Initializing built-in extension RENDER
[    47.720] (II) Initializing built-in extension RANDR
[    47.720] (II) Initializing built-in extension COMPOSITE
[    47.721] (II) Initializing built-in extension DAMAGE
[    47.721] (II) Initializing built-in extension GESTURE
[    47.806] (II) AIGLX: Trying DRI driver /usr/lib/dri/nouveau_vieux_dri.so
[    48.498] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    48.498] (II) AIGLX: enabled GLX_INTEL_swap_event
[    48.498] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    48.498] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    48.499] (II) AIGLX: Loaded and initialized nouveau_vieux
[    48.499] (II) GLX: Initialized DRI2 GL provider for screen 0
[    48.528] (II) NOUVEAU(0): NVEnterVT is called.
[    48.529] (II) NOUVEAU(0): Setting screen physical size to 338 x 270
[    48.529] resize called 1280 1024
[    49.522] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    50.964] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    50.965] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    50.965] (II) LoadModule: "evdev"
[    50.966] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.789] (II) Module evdev: vendor="X.Org Foundation"
[    51.789] 	compiled for 1.10.0.902, module version = 2.6.0
[    51.789] 	Module class: X.Org XInput Driver
[    51.789] 	ABI class: X.Org XInput driver, version 12.3
[    51.789] (II) Using input driver 'evdev' for 'Power Button'
[    51.789] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.818] (**) Power Button: always reports core events
[    51.818] (**) Power Button: Device: "/dev/input/event2"
[    51.818] (--) Power Button: Found keys
[    51.819] (II) Power Button: Configuring as keyboard
[    51.819] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    51.819] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    51.819] (**) Option "xkb_rules" "evdev"
[    51.819] (**) Option "xkb_model" "evdev"
[    51.819] (**) Option "xkb_layout" "us"
[    51.903] (II) XKB: generating xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
[    52.422] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    52.422] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    52.422] (II) Using input driver 'evdev' for 'Power Button'
[    52.422] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.423] (**) Power Button: always reports core events
[    52.423] (**) Power Button: Device: "/dev/input/event0"
[    52.423] (--) Power Button: Found keys
[    52.423] (II) Power Button: Configuring as keyboard
[    52.423] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    52.423] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    52.423] (**) Option "xkb_rules" "evdev"
[    52.423] (**) Option "xkb_model" "evdev"
[    52.423] (**) Option "xkb_layout" "us"
[    52.434] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    52.434] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    52.434] (II) Using input driver 'evdev' for 'Sleep Button'
[    52.434] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.434] (**) Sleep Button: always reports core events
[    52.434] (**) Sleep Button: Device: "/dev/input/event1"
[    52.435] (--) Sleep Button: Found keys
[    52.435] (II) Sleep Button: Configuring as keyboard
[    52.435] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    52.435] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    52.435] (**) Option "xkb_rules" "evdev"
[    52.435] (**) Option "xkb_model" "evdev"
[    52.435] (**) Option "xkb_layout" "us"
[    52.468] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    52.468] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    52.468] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    52.468] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.468] (**) AT Translated Set 2 keyboard: always reports core events
[    52.468] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    52.469] (--) AT Translated Set 2 keyboard: Found keys
[    52.469] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    52.469] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    52.469] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    52.469] (**) Option "xkb_rules" "evdev"
[    52.469] (**) Option "xkb_model" "evdev"
[    52.469] (**) Option "xkb_layout" "us"
[    52.471] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
[    52.472] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    52.472] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    52.472] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.472] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    52.472] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
[    52.472] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    52.472] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    52.472] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    52.472] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    52.473] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    52.473] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    52.473] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    52.473] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    52.473] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    52.473] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    52.473] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    52.473] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    52.474] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    52.474] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    52.474] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    52.475] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    52.475] (II) No input driver/identifier specified (ignoring)
[    66.972] (II) NOUVEAU(0): EDID vendor "ENC", prod id 5955
[    66.972] (II) NOUVEAU(0): Using hsync ranges from config file
[    66.973] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    66.973] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    66.973] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    66.973] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    66.974] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    66.974] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    66.974] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    66.974] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    66.974] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    66.974] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    66.974] (II) NOUVEAU(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
[    68.100] (II) NOUVEAU(0): EDID vendor "ENC", prod id 5955
[    68.100] (II) NOUVEAU(0): Using hsync ranges from config file
[    68.100] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    68.100] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    68.100] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    68.100] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    68.100] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    68.100] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    68.100] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    68.101] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    68.102] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    68.102] (II) NOUVEAU(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)

```

---

### Post by JC Cheloven on 2011-12-19
Thanks for the outputs.

At least one line for your "audio device" is missing from your lspci. 
That's bad. It means your AC97 audio is not even being recognised by the system. Of course alsamixer doesn't start as there is nothing to mix.
 
This leaves us to [the link]("http://www.ehow.com/how_7321451_install-media-ac97-linux.html") I gave you before. It explains that the old-late90's AC97 may not be recognised by modern linux distributions, and how to use ndiswrapper to use the windows drivers for this under linux.

As for your graphics, I don't see as supported your GeForce4 MX 440 in the [current NVidia]("http://www.nvidia.com/object/linux-display-ia32-290.10-driver.html") driver page (nor nv 17 mention).
--> But it appear in [this legacy]("http://www.nvidia.com/object/linux-display-ia32-96.43.20-driver.html") page of the nvidia site !
Please download and install that (previously uninstalling any other one).

I hope we are getting closer with this, regarding the ubuntu path.

As for the other suggested path (puppy), it's a completely different distro, although lately it became ubuntu compatible or ubuntu based to some extent. I'd go for a different release of that you mention. I think you'll have better chances with the [long term support "WaryPuppy"]("http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm"), or even with a legacy version as 4.2.1 or 4.3.1. Google a little for these versions (for example I found [this]("http://www.espaciolinux.com/2009/10/puppy-linux-4-3-1/")). The release path is a bit messy in puppy though :) And not, you can't create a puppy usb from Ubuntu's tool (but you can use use unebootin... forget it, just burn a cd).

Side note: I like to bring back to life old computers. If possible, I try to stick with an ubuntu base, even starting from a command-line system and adding only a windows manager (usually openbox). If not possible, I try puppy next. For the most severe cases, I try  slitaz.

Hope this all helps
JC

---

### Post by Cyberdot on 2011-12-20
> **JC Cheloven said:**
> As for your graphics, I don't see as supported your GeForce4 MX 440 in the [current NVidia]("http://www.nvidia.com/object/linux-display-ia32-290.10-driver.html") driver page (nor nv 17 mention).
--> But it appear in [this legacy]("http://www.nvidia.com/object/linux-display-ia32-96.43.20-driver.html") page of the nvidia site !
Please download and install that (previously uninstalling any other one).

I hope we are getting closer with this, regarding the ubuntu path.
Now I am running Lubuntu 11.04, which is faster than Lubuntu 11.10. But I feel Ubuntu 10.04 had the same performance. Anyway, I should be running one of the fastest -buntu release now, and still not able to play video.

I am running the Nouveau driver now, as this is the fastest one, suggested by MAFoElffen. I am aware that the Nvidia's recent driver does not support old GFX cards. I have tried NV 96.43.17 installed via synaptic. Can't say the performance changed. As a last option I will try this 96.43.20 driver you suggested.

> **JC Cheloven said:**
> As for the other suggested path (puppy), it's a completely different distro, although lately it became ubuntu compatible or ubuntu based to some extent. I'd go for a different release of that you mention. I think you'll have better chances with the [long term support "WaryPuppy"]("http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm"), or even with a legacy version as 4.2.1 or 4.3.1. Google a little for these versions (for example I found [this]("http://www.espaciolinux.com/2009/10/puppy-linux-4-3-1/")). The release path is a bit messy in puppy though :) And not, you can't create a puppy usb from Ubuntu's tool (but you can use use unebootin... forget it, just burn a cd).

Side note: I like to bring back to life old computers. If possible, I try to stick with an ubuntu base, even starting from a command-line system and adding only a windows manager (usually openbox). If not possible, I try puppy next. For the most severe cases, I try  slitaz.

Hope this all helps
JCOk, I will try this puppy release, thanks.

---

