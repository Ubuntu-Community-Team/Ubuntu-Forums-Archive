---
title: "Installation of Ubuntu 10.10"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by sim0s on 2010-11-28
Hey guys,

I have a Fujitsu Siemens xi 1547 laptop and I am trying to install ubuntu on it - inside windows 7.
I tried different approaches either via a bootable usb either via a cd but with no luck.
Specifically, in the usb installation all the procedure until the reboot was successful. After I was able to see the dual boot menu and when I chose to boot with ubuntu I had to chose from another menu either 1) normal mode, 2) no graphic mode etc... 
When choosing the 1st option it just shows the ubuntu home desktop screen and I am not able to do anything and had to halt the system. When chosing the 2nd option it finished the installation correctly and showed a terminal as I think that it should.

Before a while I burned a live cd and I tried to "Try Ubuntu without install" but the system freezes showing a screen with ubuntu logo.

Can anybody give me a hand please?

Thanks,
sim0s

PS: My laptop specs are: Intel Core Duo 2.16GhZ, 2GB DDR2 Ram,
ATI Radeon x1800.

---

### Post by C.S.Cameron on 2010-11-28
Have you checked the iso's MD5SUM?

---

### Post by sim0s on 2010-11-28
what's MD5SUM cameron and how should I use it?

According to its official site it is a software that matches the data you have on your hard drisk with the data on the server and it is to verify that they are not corrupted. Am I right?

---

### Post by sikander3786 on 2010-11-28
Check the MD5SUM as pointed above.

Or you may need some boot parameters.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Where are you now? I mean you are trying to boot the installed Ubuntu or trying installation again?

[COLOR="Red"]**Edit:**[/COLOR] For MD5SUM, see this.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by sim0s on 2010-11-28
I am trying to install ubuntu inside windows either with a usb either with a cd.
I don't know what's happening but the system freezes in all the ways that I am trying.

I have tried the md5sum and the result is the same!
So, it is not a problem of the downloaded ubuntu image!

To carry on, what's the best choice to install ubuntu inside windows? 
1) just using wubi
2) with bootable usb
3) live cd

I am asking this to choose the best option to start and report the errors coming out in order to provide me with some help

Thanks,
sim0s

---

### Post by sikander3786 on 2010-11-28
A proper dual boot is always better than a Wubi one. Wubi is just intended for a preview of Linux ;-) Not a long term solution.

For proper dual-boot,

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you wish to use Wubi, you just need to place your Ubuntu iso in the same folder as Wubi in Windows and just run the wubi.exe file to install it.

---

### Post by sim0s on 2010-11-28
Ok thanks a lot for your help.

But can I create a partition on my primary hard disk which has already installed windows 7 using the gparted from live cd?
Or, should I use any other partition manager software?
Because the disk management tool in windows does not allow you to create a partition with the size you want and has some restrictions.

---

### Post by dino99 on 2010-11-28
inside winblows, not the best idea :( for serious experience, and when burning always select slow speed.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO)

---

### Post by sim0s on 2010-11-28
Ok I created a new partition in the hard drive with 15GB capacity and then I tried to install ubuntu from live CD.

After booting from the CD, I selected the language and also selected the option to install ubuntu. The cpu after some process it shows only the ubuntu screen and a toolbar at the top of the screen with only the wireless, the sound volume and the power options. I am not able to do anything neither to scroll the mouse.

Anyone knows what to do?

[COLOR="Red"]Edit:[/COLOR]
I didn't pass through the procedure to select the partition and all the other details for the installation.

PS: I attach how the screen looks like  (without the toolbar at top).

---

### Post by sim0s on 2010-11-28
[COLOR="Red"]Update:[/COLOR]

I have changed the option in installing and chose to nomodeset (As some other guys advised to do to solve a similar problem).
Finally I can follow the installation procedure.
But, how this option affects the installation and the use of ubuntu?

---

### Post by sikander3786 on 2010-11-28
> **sim0s said:**
> [COLOR="Red"]Update:[/COLOR]

I have changed the option in installing and chose to nomodeset (As some other guys advised to do to solve a similar problem).
Finally I can follow the installation procedure.
But, how this option affects the installation and the use of ubuntu?
It won't effect the installation anyway. Just a graphic setting...

When you'll boot from the HDD, you might need to add **nomodeset** as well. When you boot your Ubuntu install and it ends up in a blank screen, follow the procedure below.

Press and hold down Shift key from your Bios screen. You'll see the Grub menu. Highlighting the first entry, press 'e' to edit it. Navigate to "quiet & splash", delete them and type "nomodeset" instead. Press Ctrl + X to continue boot. It would hopefully boot you to the desktop this time.

Go to System > Administration > Additional Drivers and install the recommended/current drivers for your graphics card and the problem will go away for ever ;-)

---

### Post by sim0s on 2010-11-28
thanks a lot sikander for your help.
I will try it right now and let you know about the results.

Btw, what's the difference in using the other options provided when pressing the f6 button in ubuntu menu? Is there any significant difference in the graphics, the user interface or the software?

PS: Isn't selecting nomodeset decreasing resolution?

---

### Post by sikander3786 on 2010-11-28
Yes that definitely decreases resolution and refresh rate I believe and syncs that properly with your monitor.

Other options in F6 menu are some power options etc, nothing to do with graphics.

And the user interface is the same whichever option you select ;-) They are just boot parameters for some specific hardware only. Once you install the proper drivers, everything would be just fine.

---

### Post by Arthur.Felty on 2010-11-28
Hello everyone!
 
I have one question about the install of Ubuntu. I just bought an new dell inspiron 15 and its going to be my linux workstation for c programming. But its running a 64 bit OS. Do I have to install Ubuntu 10.10 64bit amd? and will it work with a 32 bit OS without compatibility issues?

---

### Post by sikander3786 on 2010-11-28
> **Arthur.Felty said:**
> Hello everyone!
 
I have one question about the install of Ubuntu. I just bought an new dell inspiron 15 and its going to be my linux workstation for c programming. But its running a 64 bit OS. Do I have to install Ubuntu 10.10 64bit amd? and will it work with a 32 bit OS without compatibility issues?
So you intend to install Ubuntu in dual-boot to that existing 64-bit OS, right?

Yes you can install whether 32-bit or 64-bit, whichever you choose. Each OS runs independent of the other so no question of compatibility here.

Both have their own pros and cons, start a new thread for that or this would be called thread hijacking ;-)

---

### Post by sim0s on 2010-11-28
ok I will try it with nomodeset and install later the graphic card drivers.

Something else now,
I have created a 15gb unallocated partition and I want to assign it to the ubuntu system.

How should I allocate the capacity?
Should I create a swap directory and a home one? Or is it ok to proceed and allocate the whole partition to the "\" ??

---

### Post by sikander3786 on 2010-11-28
Having a separate /home is always a better choice because that saves all your configuration/personal files in case of a re-install.

But, with 15 GB of space, my partitioning setup would be

1. / partition, 13 GB, ext4, Mount Point /

2. Swap, 2 GB

In this case your /home would be on the same partition as / and in case of any hiccups, you'll need to extract your data from the / partition using a Live CD. Though that is pretty simple.

---

### Post by sim0s on 2010-11-28
Hopefully I managed to install ubuntu in my laptop. :D

But when I restart and view the boot menu there are 3 options for the ubuntu.
1) ubuntu with linux 2.6.35-22-generic
2) ubuntu with linux 2.6.35-22-generic (recovery mode)
3) Memory test (memtest86+)
4) Memory test (memtest86+, serial console 115200)
5) Windows 7 (loader) (on dev/sda1)

What are all these?
I thought that there would be only two options in boot loader,
windows 7 and ubuntu.

Any option what are all these and how to solve the issue?

---

### Post by sikander3786 on 2010-11-28
> **sim0s said:**
> Hopefully I managed to install ubuntu in my laptop. :D

But when I restart and view the boot menu there are 3 options for the ubuntu.
1) ubuntu with linux 2.6.35-22-generic
2) ubuntu with linux 2.6.35-22-generic (recovery mode)
3) Memory test (memtest86+)
4) Memory test (memtest86+, serial console 115200)
5) Windows 7 (loader) (on dev/sda1)

What are all these?
I thought that there would be only two options in boot loader,
windows 7 and ubuntu.

Any option what are all these and how to solve the issue?
This thread will help you tweak the Grub menu accordingly. For more info, look at **drs305's** signature there.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

I would advise to keep the Recovery Mode option in the Grub menu as some time later, you might need that for doing some commands, reconfiguring graphics or fixing broken packages.

---

### Post by sim0s on 2010-11-28
sikander,

"Go to System > Administration > Additional Drivers and install the recommended/current drivers for your graphics card and the problem will go away for ever"

I managed to boot into ubuntu by changing the quiet splash in boot screen and then I tried to update the graphic card drivers but I could only update the software modem.
When I restarted the laptop, the details when pressing "e" in bootloader were still the same and the quiet splash option was not change.

What did I do wrong?

---

### Post by sikander3786 on 2010-11-28
> **sim0s said:**
> sikander,

"Go to System > Administration > Additional Drivers and install the recommended/current drivers for your graphics card and the problem will go away for ever"

I managed to boot into ubuntu by changing the quiet splash in boot screen and then I tried to update the graphic card drivers but I could only update the software modem.
When I restarted the laptop, the details when pressing "e" in bootloader were still the same and the quiet splash option was not change.

What did I do wrong?
Yes that would revert to "quiet & splash" every boot.

Which graphics card have you got?

---

### Post by sim0s on 2010-11-28
It's an old graphic card...
ATI Radeon x1800

Can I manually install my graphic card drivers and fix this problem?
Is there any way to make booting into ubuntu automatic?
And why is that happening?

I am still confused about this issue!!! :(

---

### Post by sikander3786 on 2010-11-28
> **sim0s said:**
> It's an old graphic card...
ATI Radeon x1800

Can I manually install my graphic card drivers and fix this problem?
Is there any way to make booting into ubuntu automatic?
And why is that happening?

I am still confused about this issue!!! :(
It would be solved soon I hope :-)

With the default/generic drivers that are in use now, are you satisfied with the resolution? If yes, we can try to just make that "nomodeset" permanent and make your boot into Ubuntu without editing the Grub line every time.

Or you can install the open source ATI drives as directed here.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by sim0s on 2010-11-28
So, it is a problem of the ubuntu 10.10 version?


The resolution is quite good but I will try and update the drivers of my graphic card. But until I manage this can you please tell me how to make nomodeset permanent and change the grub file?

---

### Post by sikander3786 on 2010-11-28
It is a problem with X upstream so you'll find it in pretty much every Linux distro these days.

Edit /etc/default/grub by

```
gksudo gedit /etc/default/grub
```

You'll see this line,

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Delete "quiet splash" and type "nomodeset" so it looks like

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

Save and close.

Now update Grub by,

```
sudo update-grub
```

Reboot and see if that worked.

---

### Post by Penguin=) on 2010-11-28
Is everything ok now?

---

### Post by sim0s on 2010-11-28
Yeap, after changed the grub file the rebooting was just OK.

Do you know when this issue will be solved so that we can have the maximum resolution?
Because as I have seen many ubuntu users face this problem and they are disappointed by this fault.

Em....I will try and upload manually the drivers for the ATI Radeon x1800 according to the article sikander provided.

But when I am trying the command "sudo apt-get remove --purge xorg-driver-fglrx"

the result is:
"virtual packages like xorg-drive-fglrx can't be removed.
  0 upgraded, 0 newly installed, 0 to remove and 163 not upgraded"
Isn't fault this?

---

### Post by Penguin=) on 2010-11-28
Damn errors. 

This means that a file is corrupted, you're going to have to start a file named the code that you put in to get that error.

So you now can't get a error.

Tell me how it goes.

---

### Post by sim0s on 2010-11-28
Penguin,
what do you mean by that?

I am new to ubuntu OS.
Can you give me some details pls?

---

### Post by sikander3786 on 2010-11-28
> **sim0s said:**
> Yeap, after changed the grub file the rebooting was just OK.

Do you know when this issue will be solved so that we can have the maximum resolution?
Because as I have seen many ubuntu users face this problem and they are disappointed by this fault.

Em....I will try and upload manually the drivers for the ATI Radeon x1800 according to the article sikander provided.

But when I am trying the command "sudo apt-get remove --purge xorg-driver-fglrx"

the result is:
"virtual packages like xorg-drive-fglrx can't be removed.
  0 upgraded, 0 newly installed, 0 to remove and 163 not upgraded"
Isn't fault this?
Post the output of this one.

```
glxinfo | grep vendor
```

---

### Post by sim0s on 2010-11-28
the result is:


spy@Spy:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: DRI R300 Project

---

### Post by Arthur.Felty on 2010-11-28
sorry about that I'm pretty new to forums Ill start a new thread but I do appreciate the reply to that.

---

### Post by sikander3786 on 2010-11-28
> If you previously used the proprietary "fglrx" driver it is highly recommended to totally get rid of the fglrx package:

sudo apt-get remove --purge xorg-driver-fglrx

As you didn't install the proprietary drivers, you don't need to remove them ;-)

Continue with the install as suggested on the page I linked.

---

### Post by sim0s on 2010-11-28
sikander,

I have followed the steps up to configuration of x.org.
After, what should i follow: the new way or the old way that the article suggests.



PS: I followed the new way but I got lost to the article x kernel modeset.


Any idea what should I do next?

---

### Post by sikander3786 on 2010-11-28
New way is better.

I have read those pages again and what I understand is you only need to edit your /etc/default/grub and put in radeon.modeset=1 to enable KMS.

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

Change "nomodeset" to "radeon.modeset=1", save and close.

Reboot.

Then log in again and post the output of

```
dmesg | grep drm
```

---

### Post by sim0s on 2010-11-28
I can't interact with the system after changing nomodeset to radeon.modeset=1.

The screen blings constantly and it freezes.
Did we miss anything in the procedure and it is not just changing nomodeset to radeon.modeset=1?

Because there is a whole article on how to achieve this!!!!

---

### Post by sikander3786 on 2010-11-28
Change that radeon.modeset=1 back to nomodeset as you did previously from the Grub menu.

I don't think we missed anything else than we should have tried it without a reboot.

Switch to nomodeset and please let me know if you are able to boot to the desktop or not.

I have to leave now. Just waiting for you to boot the desktop successfully. Some other mate might jump in here or we would continue it later. I'd keep an eye on the thread ;-)

---

### Post by sim0s on 2010-11-28
Ok I changed the radeon.modeset=1 to nomodeset as it was at the beginning and managed to log in to ubuntu again.

But, the resolution is not as good as it was with ubuntu 9.10 at the same laptop. Is the nomodeset the reason?


Also, is there a way to manually install my ati radeon x1800 drivers or to increase resolution?

---

### Post by sikander3786 on 2010-11-28
That might be because you were using the proprietary drivers on 9.10?

Please follow the steps below and keep the thread updated.

> Module loading issues on ATI

If you get "RADEONDRIGetVersion failed" in Xorg.0.log it is because of a race issue. The radeon module is not initialized in time before X is starting, and X will falsely believe that there is no KMS support and do its own modesetting...

To make sure the radeon modules is initialized before gdm (and X) is starting, insert "modprobe radeon" into your /etc/init/gdm.conf just before the gdm-binary is executed:

    ...
    initctl emit starting-dm DM=gdm

    modprobe radeon
    exec gdm-binary $CONFIG_FILE
end script

Missing firmware issue on ATI

If your /var/log/syslog has the line Cannot find  firmware file 'radeon/R600_rlc.bin' you should download it.

sudo wget -O /var/lib/firmware/`uname -r`/radeon/R600_rlc.bin [http://people.freedesktop.org/~agd5f/radeon_ucode/R600_rlc.bin](http://people.freedesktop.org/~agd5f/radeon_ucode/R600_rlc.bin)

Regards.

---

### Post by sim0s on 2010-11-28
I made the changes and inserted "modeprobe radeon" to gdm.conf file and also change the grub from "nomodeset" to "radeon.modeset=1" and restarted.

Unfortunately, there was no change and the system froze again and I had to halt it.


What's going on?
I think that I did what the manual advised but without any luck.

---

### Post by sikander3786 on 2010-11-28
> **sim0s said:**
> I made the changes and inserted "modeprobe radeon" to gdm.conf file and also change the grub from "nomodeset" to "radeon.modeset=1" and restarted.

Unfortunately, there was no change and the system froze again and I had to halt it.


What's going on?
I think that I did what the manual advised but without any luck.
What does the Xorg.0.log state?

System > Administration > Log File Viewer

---

### Post by sim0s on 2010-11-28
I am attaching the log file xorg.0.log

```

[[    35.274] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    35.274] X Protocol Version 11, Revision 0
[    35.274] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    35.274] Current Operating System: Linux Spy 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    35.274] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=7dcd1223-5689-4e8d-b393-e703940a0fc6 ro nomodeset
[    35.275] Build Date: 16 September 2010  05:39:22PM
[    35.275] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    35.275] Current version of pixman: 0.18.4
[    35.275]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    35.275] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    35.275] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 28 23:57:55 2010
[    35.585] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    35.594] (==) No Layout section.  Using the first Screen section.
[    35.594] (==) No screen section available. Using defaults.
[    35.594] (**) |-->Screen "Default Screen Section" (0)
[    35.594] (**) |   |-->Monitor "<default monitor>"
[    35.594] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    35.594] (==) Automatically adding devices
[    35.594] (==) Automatically enabling devices
[    35.595] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    35.595]     Entry deleted from font path.
[    35.595] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    35.595] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    35.595] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    35.595] (II) Loader magic: 0x81f8e00
[    35.595] (II) Module ABI versions:
[    35.595]     X.Org ANSI C Emulation: 0.4
[    35.595]     X.Org Video Driver: 8.0
[    35.595]     X.Org XInput driver : 11.0
[    35.595]     X.Org Server Extension : 4.0
[    35.596] (--) PCI:*(0:1:0:0) 1002:7102:1734:10ac rev 0, Mem @ 0xc0000000/268435456, 0xb0100000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    35.596] (II) Open ACPI successful (/var/run/acpid.socket)
[    35.596] (II) LoadModule: "extmod"
[    35.629] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    35.629] (II) Module extmod: vendor="X.Org Foundation"
[    35.629]     compiled for 1.9.0, module version = 1.0.0
[    35.629]     Module class: X.Org Server Extension
[    35.629]     ABI class: X.Org Server Extension, version 4.0
[    35.629] (II) Loading extension MIT-SCREEN-SAVER
[    35.629] (II) Loading extension XFree86-VidModeExtension
[    35.629] (II) Loading extension XFree86-DGA
[    35.630] (II) Loading extension DPMS
[    35.630] (II) Loading extension XVideo
[    35.630] (II) Loading extension XVideo-MotionCompensation
[    35.630] (II) Loading extension X-Resource
[    35.630] (II) LoadModule: "dbe"
[    35.630] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    35.630] (II) Module dbe: vendor="X.Org Foundation"
[    35.630]     compiled for 1.9.0, module version = 1.0.0
[    35.630]     Module class: X.Org Server Extension
[    35.630]     ABI class: X.Org Server Extension, version 4.0
[    35.630] (II) Loading extension DOUBLE-BUFFER
[    35.630] (II) LoadModule: "glx"
[    35.630] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    35.630] (II) Module glx: vendor="X.Org Foundation"
[    35.630]     compiled for 1.9.0, module version = 1.0.0
[    35.630]     ABI class: X.Org Server Extension, version 4.0
[    35.630] (==) AIGLX enabled
[    35.630] (II) Loading extension GLX
[    35.630] (II) LoadModule: "record"
[    35.631] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    35.631] (II) Module record: vendor="X.Org Foundation"
[    35.631]     compiled for 1.9.0, module version = 1.13.0
[    35.631]     Module class: X.Org Server Extension
[    35.631]     ABI class: X.Org Server Extension, version 4.0
[    35.631] (II) Loading extension RECORD
[    35.631] (II) LoadModule: "dri"
[    35.631] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    35.631] (II) Module dri: vendor="X.Org Foundation"
[    35.631]     compiled for 1.9.0, module version = 1.0.0
[    35.631]     ABI class: X.Org Server Extension, version 4.0
[    35.631] (II) Loading extension XFree86-DRI
[    35.631] (II) LoadModule: "dri2"
[    35.631] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    35.632] (II) Module dri2: vendor="X.Org Foundation"
[    35.632]     compiled for 1.9.0, module version = 1.2.0
[    35.632]     ABI class: X.Org Server Extension, version 4.0
[    35.632] (II) Loading extension DRI2
[    35.632] (==) Matched ati as autoconfigured driver 0
[    35.632] (==) Matched vesa as autoconfigured driver 1
[    35.632] (==) Matched fbdev as autoconfigured driver 2
[    35.632] (==) Assigned the driver to the xf86ConfigLayout
[    35.632] (II) LoadModule: "ati"
[    35.632] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    35.632] (II) Module ati: vendor="X.Org Foundation"
[    35.632]     compiled for 1.9.0, module version = 6.13.1
[    35.632]     Module class: X.Org Video Driver
[    35.632]     ABI class: X.Org Video Driver, version 8.0
[    35.632] (II) LoadModule: "radeon"
[    35.633] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    35.633] (II) Module radeon: vendor="X.Org Foundation"
[    35.633]     compiled for 1.9.0, module version = 6.13.1
[    35.633]     Module class: X.Org Video Driver
[    35.633]     ABI class: X.Org Video Driver, version 8.0
[    35.633] (II) LoadModule: "vesa"
[    35.633] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    35.633] (II) Module vesa: vendor="X.Org Foundation"
[    35.633]     compiled for 1.8.99.905, module version = 2.3.0
[    35.633]     Module class: X.Org Video Driver
[    35.633]     ABI class: X.Org Video Driver, version 8.0
[    35.633] (II) LoadModule: "fbdev"
[    35.634] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    35.634] (II) Module fbdev: vendor="X.Org Foundation"
[    35.634]     compiled for 1.8.99.905, module version = 0.4.2
[    35.634]     ABI class: X.Org Video Driver, version 8.0
[    35.634] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
    CEDAR
[    35.641] (II) VESA: driver for VESA chipsets: vesa
[    35.641] (II) FBDEV: driver for framebuffer: fbdev
[    35.641] (++) using VT number 7

[    35.642] (II) [KMS] drm report modesetting isn't supported.
[    35.642] (WW) Falling back to old probe method for vesa
[    35.642] (WW) Falling back to old probe method for fbdev
[    35.642] (II) Loading sub module "fbdevhw"
[    35.642] (II) LoadModule: "fbdevhw"
[    35.642] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    35.642] (II) Module fbdevhw: vendor="X.Org Foundation"
[    35.642]     compiled for 1.9.0, module version = 0.0.2
[    35.642]     ABI class: X.Org Video Driver, version 8.0
[    35.642] (EE) open /dev/fb0: No such file or directory
[    35.642] (II) RADEON(0): TOTO SAYS 00000000b0100000
[    35.642] (II) RADEON(0): MMIO registers at 0x00000000b0100000: size 64KB
[    35.642] (II) RADEON(0): PCI bus 1 card 0 func 0
[    35.643] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    35.643] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    35.643] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    35.643] (==) RADEON(0): Default visual is TrueColor
[    35.643] (II) Loading sub module "vgahw"
[    35.643] (II) LoadModule: "vgahw"
[    35.643] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    35.666] (II) Module vgahw: vendor="X.Org Foundation"
[    35.666]     compiled for 1.9.0, module version = 0.1.0
[    35.666]     ABI class: X.Org Video Driver, version 8.0
[    35.666] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    35.666] (==) RADEON(0): RGB weight 888
[    35.666] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    35.666] (--) RADEON(0): Chipset: "ATI Mobility Radeon X1800" (ChipID = 0x7102)
[    35.666] (--) RADEON(0): Linear framebuffer at 0x00000000c0000000
[    35.666] (II) RADEON(0): PCIE card detected
[    35.666] (II) Loading sub module "int10"
[    35.666] (II) LoadModule: "int10"
[    35.666] (II) Loading /usr/lib/xorg/modules/libint10.so
[    35.693] (II) Module int10: vendor="X.Org Foundation"
[    35.693]     compiled for 1.9.0, module version = 1.0.0
[    35.693]     ABI class: X.Org Video Driver, version 8.0
[    35.694] (II) RADEON(0): initializing int10
[    35.694] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    35.694] (II) RADEON(0): ATOM BIOS detected
[    35.694] (II) RADEON(0): ATOM BIOS Rom: 
[    35.694]     SubsystemVendorID: 0x1734 SubsystemID: 0x10ac
[    35.694]     IOBaseAddress: 0x2000
[    35.694]     Filename: BR19482M.BIN
[    35.694]     BIOS Bootup Message:  
Uniwill P72IA0 M58P 12P ATOM BIOS CRT/LCD/TV/DFP 400e/470m                   

[    35.694] (II) RADEON(0): Framebuffer space used by Firmware (kb): 20
[    35.694] (II) RADEON(0): Start of VRAM area used by Firmware: 0x1000000
[    35.694] (II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
[    35.694] (II) RADEON(0): AtomBIOS VRAM scratch base: 0x1000000
[    35.694] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    35.694] (II) RADEON(0): Default Engine Clock: 392000
[    35.694] (II) RADEON(0): Default Memory Clock: 252000
[    35.694] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1100000
[    35.694] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    35.694] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
[    35.694] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
[    35.694] (II) RADEON(0): Maximum Pixel Clock: 400000
[    35.694] (II) RADEON(0): Reference Clock: 27000
[    35.694] drmOpenDevice: node name is /dev/dri/card0
[    35.695] drmOpenDevice: open result is 11, (OK)
[    35.696] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    35.696] drmOpenDevice: node name is /dev/dri/card0
[    35.696] drmOpenDevice: open result is 11, (OK)
[    35.696] drmOpenByBusid: drmOpenMinor returns 11
[    35.696] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    35.697] (II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.33.0
[    35.697] (==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

[    35.697] (II) RADEON(0): Will try to use DMA for Xv image transfers
[    35.697] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    35.697] (II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
[    35.697] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (256 bit DDR SDRAM)
[    35.697] (II) RADEON(0): Color tiling enabled by default
[    35.697] (II) Loading sub module "ddc"
[    35.697] (II) LoadModule: "ddc"
[    35.697] (II) Module "ddc" already built-in
[    35.697] (II) Loading sub module "i2c"
[    35.697] (II) LoadModule: "i2c"
[    35.697] (II) Module "i2c" already built-in
[    35.697] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=90000 max=110000; xclk=40000
[    35.697] (WW) RADEON(0): LVDS Info:
XRes: 1440, YRes: 900, DotClock: 96300
HBlank: 320, HOverPlus: 64, HSyncWidth: 32
VBlank: 12, VOverPlus: 3, VSyncWidth: 3
[    35.697] (II) RADEON(0): Skipping TV-Out
[    35.697] (II) RADEON(0): Skipping Component Video
[    35.697] (II) RADEON(0): Output LVDS has no monitor section
[    35.697] (II) RADEON(0): Output DVI-0 has no monitor section
[    35.697] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    35.698] (II) RADEON(0): Port0:
[    35.698]   XRANDR name: LVDS
[    35.698]   Connector: LVDS
[    35.698]   LCD1: INTERNAL_LVTM1
[    35.698]   DDC reg: 0x0
[    35.698] (II) RADEON(0): Port1:
[    35.698]   XRANDR name: DVI-0
[    35.698]   Connector: DVI-I
[    35.698]   CRT1: INTERNAL_KLDSCP_DAC1
[    35.698]   DFP1: INTERNAL_KLDSCP_TMDS1
[    35.698]   DDC reg: 0x7e50
[    35.698] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    35.698] finished output detect: 0
[    35.698] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    35.736] Dac detection success
[    35.736] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    35.736] Unhandled monitor type 0
[    35.736] finished output detect: 1
[    35.736] finished all detect
[    35.736] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    35.736] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    35.736] (II) RADEON(0): Added native panel mode: 1440x900
[    35.736] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    35.736] (II) RADEON(0): Not using default mode "320x175" (doublescan mode not supported)
[    35.736] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    35.736] (II) RADEON(0): Not using default mode "320x200" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "360x200" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1024x768i" (interlace mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "512x384i" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    35.737] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    35.737] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    35.737] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    35.737] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    35.737] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    35.737] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    35.737] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    35.737] (II) RADEON(0): Not using default mode "416x312" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    35.738] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    35.738] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    35.738] (II) RADEON(0): Not using default mode "720x450" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    35.738] (II) RADEON(0): Not using default mode "800x512" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    35.738] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    35.738] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    35.738] (II) RADEON(0): Not using default mode "960x540" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    35.738] (II) RADEON(0): Not using default mode "960x600" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    35.738] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    35.738] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    35.738] (II) RADEON(0): Printing probed modes for output LVDS
[    35.738] (II) RADEON(0): Modeline "1440x900"x60.0   96.30  1440 1504 1536 1760  900 903 906 912 (54.7 kHz)
[    35.738] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[    35.738] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    35.738] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    35.738] (II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    35.738] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    35.738] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    35.738] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.738] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    35.738] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.738] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    35.738] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.738] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    35.776] Dac detection success
[    35.776] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    35.776] Unhandled monitor type 0
[    35.777] (II) RADEON(0): EDID for output DVI-0
[    35.777] (II) RADEON(0): Output LVDS connected
[    35.777] (II) RADEON(0): Output DVI-0 disconnected
[    35.777] (II) RADEON(0): Using exact sizes for initial modes
[    35.777] (II) RADEON(0): Output LVDS using initial mode 1440x900
[    35.777] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    35.777] (==) RADEON(0): DPI set to (96, 96)
[    35.777] (II) Loading sub module "fb"
[    35.777] (II) LoadModule: "fb"
[    35.777] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.777] (II) Module fb: vendor="X.Org Foundation"
[    35.777]     compiled for 1.9.0, module version = 1.0.0
[    35.777]     ABI class: X.Org ANSI C Emulation, version 0.4
[    35.777] (II) Loading sub module "ramdac"
[    35.777] (II) LoadModule: "ramdac"
[    35.777] (II) Module "ramdac" already built-in
[    35.777] (==) RADEON(0): Using EXA acceleration architecture
[    35.777] (II) Loading sub module "exa"
[    35.777] (II) LoadModule: "exa"
[    35.778] (II) Loading /usr/lib/xorg/modules/libexa.so
[    35.778] (II) Module exa: vendor="X.Org Foundation"
[    35.778]     compiled for 1.9.0, module version = 2.5.0
[    35.778]     ABI class: X.Org Video Driver, version 8.0
[    35.778] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    35.778] (II) UnloadModule: "vesa"
[    35.778] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    35.778] (II) UnloadModule: "fbdev"
[    35.778] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    35.778] (II) UnloadModule: "fbdevhw"
[    35.778] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    35.778] (--) Depth 24 pixmap format is 32 bpp
[    35.778] (II) RADEON(0): RADEONScreenInit c0000000 0 0
[    36.168] Output LCD1 disable success
[    36.171] Blank CRTC 0 success
[    36.176] Disable CRTC 0 success
[    36.176] Blank CRTC 1 success
[    36.176] Disable CRTC 1 success
[    36.176] (II) RADEON(0): Dynamic Power Management Disabled
[    36.176] (==) RADEON(0): Using 24 bit depth buffer
[    36.176] (II) RADEON(0): RADEONInitMemoryMap() : 
[    36.176] (II) RADEON(0):   mem_size         : 0x10000000
[    36.176] (II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000
[    36.176] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    36.176] (II) RADEON(0): Depth moves disabled by default
[    36.176] (II) RADEON(0): Allocating from a screen of 262112 kb
[    36.176] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00816000
[    36.176] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x0081a000
[    36.176] (II) RADEON(0): Will use 8280 kb for front buffer at offset 0x00000000
[    36.176] (II) RADEON(0): Will use 32 kb for PCI GART at offset 0x0fff8000
[    36.176] (II) RADEON(0): Will use 8280 kb for back buffer at offset 0x0081e000
[    36.176] (II) RADEON(0): Will use 8280 kb for depth buffer at offset 0x01034000
[    36.176] (II) RADEON(0): Will use 117760 kb for textures at offset 0x0184a000
[    36.176] (II) RADEON(0): Will use 119480 kb for X Server offscreen at offset 0x08b4a000
[    36.176] drmOpenDevice: node name is /dev/dri/card0
[    36.176] drmOpenDevice: open result is 11, (OK)
[    36.176] drmOpenDevice: node name is /dev/dri/card0
[    36.176] drmOpenDevice: open result is 11, (OK)
[    36.176] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    36.176] drmOpenDevice: node name is /dev/dri/card0
[    36.176] drmOpenDevice: open result is 11, (OK)
[    36.176] drmOpenByBusid: drmOpenMinor returns 11
[    36.176] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    36.176] (II) [drm] DRM interface version 1.3
[    36.176] (II) [drm] DRM open master succeeded.
[    36.176] (II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
[    36.176] (II) RADEON(0): [drm] framebuffer handle = 0xc0000000
[    36.176] (II) RADEON(0): [drm] added 1 reserved context for kernel
[    36.176] (II) RADEON(0): X context handle = 0x1
[    36.176] (II) RADEON(0): [drm] installed DRM signal handler
[    36.197] (II) RADEON(0): [pci] 32768 kB allocated with handle 0xf96ea000
[    36.197] (II) RADEON(0): [pci] ring handle = 0xf96ea000
[    36.197] (II) RADEON(0): [pci] Ring mapped at 0xb75fa000
[    36.197] (II) RADEON(0): [pci] Ring contents 0x00000000
[    36.197] (II) RADEON(0): [pci] ring read ptr handle = 0xf97eb000
[    36.197] (II) RADEON(0): [pci] Ring read ptr mapped at 0xb75f9000
[    36.197] (II) RADEON(0): [pci] Ring read ptr contents 0x00000000
[    36.197] (II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf97ec000
[    36.197] (II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xb738b000
[    36.197] (II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
[    36.197] (II) RADEON(0): [pci] GART texture map handle = 0xf99ec000
[    36.197] (II) RADEON(0): [pci] GART Texture map mapped at 0xb570b000
[    36.197] (II) RADEON(0): [drm] register handle = 0x26020000
[    36.197] (II) RADEON(0): [dri] Visual configs initialized
[    36.198] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    36.198] (II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0xcfffc000
[    36.198] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    36.208] (==) RADEON(0): Backing store disabled
[    36.208] (II) RADEON(0): [DRI] installation complete
[    36.211] (II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
[    36.211] (II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
[    36.211] (II) RADEON(0): [drm] dma control initialized, using IRQ 16
[    36.211] (II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
[    36.211] (WW) RADEON(0): DRI init changed memory map, adjusting ...
[    36.211] (WW) RADEON(0):   MC_FB_LOCATION  was: 0xcfffc000 is: 0xcfffc000
[    36.211] (WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0xffffffc0
[    36.211] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    36.211] (II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0xcfffc000
[    36.211] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    36.211] (II) RADEON(0): Direct rendering enabled
[    36.211] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    36.211] (II) RADEON(0): Setting EXA maxPitchBytes
[    36.211] (II) RADEON(0): num quad-pipes is 3
[    36.211] (II) EXA(0): Offscreen pixmap area of 122347520 bytes
[    36.212] (II) EXA(0): Driver registered support for the following operations:
[    36.212] (II)         Solid
[    36.212] (II)         Copy
[    36.212] (II)         Composite (RENDER acceleration)
[    36.212] (II)         UploadToScreen
[    36.212] (II)         DownloadFromScreen
[    36.212] (II) RADEON(0): Acceleration enabled
[    36.212] (==) RADEON(0): DPMS enabled
[    36.212] (==) RADEON(0): Silken mouse enabled
[    36.212] (II) RADEON(0): Set up textured video
[    36.218] Output LCD1 disable success
[    36.218] Blank CRTC 0 success
[    36.218] Disable CRTC 0 success
[    36.218] Blank CRTC 1 success
[    36.218] Disable CRTC 1 success
[    36.218] Output LCD1 disable success
[    36.218] Blank CRTC 0 success
[    36.218] Disable CRTC 0 success
[    36.219] Mode 1440x900 - 1760 912 0
[    36.219] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    36.219] (II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0xcfffc000
[    36.219] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    36.219] Picked PLL 0
[    36.219] best_freq: 96340
[    36.219] best_feedback_div: 157
[    36.219] best_frac_feedback_div: 0
[    36.219] best_ref_div: 4
[    36.219] best_post_div: 11
[    36.219] (II) RADEON(0): crtc(0) Clock: mode 96300, PLL 963400
[    36.219] (II) RADEON(0): crtc(0) PLL  : refdiv 4, fbdiv 0x9D(157), fracfbdiv 0, pdiv 11
[    36.221] Set CRTC 0 PLL success
[    36.221] Set CRTC Timing success
[    36.221] Set CRTC 0 Overscan success
[    36.221] Not using RMX
[    36.221] scaler 0 setup success
[    36.221] Set CRTC 0 Source success
[    36.221] crtc 0 YUV disable setup success
[    36.223] Output digital setup success
[    36.672] Output LCD1 enable success
[    36.672] Enable CRTC 0 success
[    36.672] Unblank CRTC 0 success
[    36.672] Blank CRTC 1 success
[    36.672] Disable CRTC 1 success
[    36.672] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    36.673] (--) RandR disabled
[    36.673] (II) Initializing built-in extension Generic Event Extension
[    36.673] (II) Initializing built-in extension SHAPE
[    36.673] (II) Initializing built-in extension MIT-SHM
[    36.673] (II) Initializing built-in extension XInputExtension
[    36.673] (II) Initializing built-in extension XTEST
[    36.673] (II) Initializing built-in extension BIG-REQUESTS
[    36.673] (II) Initializing built-in extension SYNC
[    36.673] (II) Initializing built-in extension XKEYBOARD
[    36.673] (II) Initializing built-in extension XC-MISC
[    36.673] (II) Initializing built-in extension SECURITY
[    36.673] (II) Initializing built-in extension XINERAMA
[    36.673] (II) Initializing built-in extension XFIXES
[    36.673] (II) Initializing built-in extension RENDER
[    36.673] (II) Initializing built-in extension RANDR
[    36.673] (II) Initializing built-in extension COMPOSITE
[    36.673] (II) Initializing built-in extension DAMAGE
[    36.673] (II) Initializing built-in extension GESTURE
[    36.686] (II) AIGLX: Screen 0 is not DRI2 capable
[    36.686] drmOpenDevice: node name is /dev/dri/card0
[    36.686] drmOpenDevice: open result is 12, (OK)
[    36.686] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    36.686] drmOpenDevice: node name is /dev/dri/card0
[    36.686] drmOpenDevice: open result is 12, (OK)
[    36.686] drmOpenByBusid: drmOpenMinor returns 12
[    36.686] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    36.725] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    36.725] (II) AIGLX: enabled GLX_SGI_make_current_read
[    36.725] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    36.725] (II) AIGLX: enabled GLX_texture_from_pixmap with driver support
[    36.725] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    36.725] (II) GLX: Initialized DRI GL provider for screen 0
[    36.726] (II) RADEON(0): Setting screen physical size to 380 x 238
[    36.747] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.757] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    36.757] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.757] (II) LoadModule: "evdev"
[    36.757] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.757] (II) Module evdev: vendor="X.Org Foundation"
[    36.757]     compiled for 1.9.0, module version = 2.3.2
[    36.757]     Module class: X.Org XInput Driver
[    36.757]     ABI class: X.Org XInput driver, version 11.0
[    36.757] (**) Power Button: always reports core events
[    36.757] (**) Power Button: Device: "/dev/input/event3"
[    36.772] (II) Power Button: Found keys
[    36.772] (II) Power Button: Configuring as keyboard
[    36.772] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    36.772] (**) Option "xkb_rules" "evdev"
[    36.772] (**) Option "xkb_model" "evdev"
[    36.772] (**) Option "xkb_layout" "gb"
[    36.775] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[    36.776] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    36.776] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    36.776] (**) Video Bus: always reports core events
[    36.776] (**) Video Bus: Device: "/dev/input/event6"
[    36.792] (II) Video Bus: Found keys
[    36.792] (II) Video Bus: Configuring as keyboard
[    36.792] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    36.792] (**) Option "xkb_rules" "evdev"
[    36.792] (**) Option "xkb_model" "evdev"
[    36.792] (**) Option "xkb_layout" "gb"
[    36.794] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    36.794] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.794] (**) Power Button: always reports core events
[    36.794] (**) Power Button: Device: "/dev/input/event1"
[    36.808] (II) Power Button: Found keys
[    36.808] (II) Power Button: Configuring as keyboard
[    36.808] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    36.808] (**) Option "xkb_rules" "evdev"
[    36.808] (**) Option "xkb_model" "evdev"
[    36.808] (**) Option "xkb_layout" "gb"
[    36.808] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    36.808] (II) No input driver/identifier specified (ignoring)
[    36.808] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    36.808] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    36.809] (**) Sleep Button: always reports core events
[    36.809] (**) Sleep Button: Device: "/dev/input/event2"
[    36.824] (II) Sleep Button: Found keys
[    36.824] (II) Sleep Button: Configuring as keyboard
[    36.824] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    36.824] (**) Option "xkb_rules" "evdev"
[    36.824] (**) Option "xkb_model" "evdev"
[    36.824] (**) Option "xkb_layout" "gb"
[    36.826] (II) config/udev: Adding input device Darfon USB Optical Mouse (/dev/input/event5)
[    36.826] (**) Darfon USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    36.826] (**) Darfon USB Optical Mouse: always reports core events
[    36.826] (**) Darfon USB Optical Mouse: Device: "/dev/input/event5"
[    36.840] (II) Darfon USB Optical Mouse: Found 3 mouse buttons
[    36.840] (II) Darfon USB Optical Mouse: Found scroll wheel(s)
[    36.840] (II) Darfon USB Optical Mouse: Found relative axes
[    36.840] (II) Darfon USB Optical Mouse: Found x and y relative axes
[    36.840] (II) Darfon USB Optical Mouse: Configuring as mouse
[    36.840] (**) Darfon USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    36.840] (**) Darfon USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.840] (II) XINPUT: Adding extended input device "Darfon USB Optical Mouse" (type: MOUSE)
[    36.840] (II) Darfon USB Optical Mouse: initialized for relative axes.
[    36.840] (II) config/udev: Adding input device Darfon USB Optical Mouse (/dev/input/mouse0)
[    36.840] (II) No input driver/identifier specified (ignoring)
[    36.845] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    36.845] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    36.845] (**) AT Translated Set 2 keyboard: always reports core events
[    36.845] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    36.856] (II) AT Translated Set 2 keyboard: Found keys
[    36.856] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    36.856] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    36.856] (**) Option "xkb_rules" "evdev"
[    36.856] (**) Option "xkb_model" "evdev"
[    36.856] (**) Option "xkb_layout" "gb"
[    36.856] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    36.856] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    36.856] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    36.856] (II) LoadModule: "synaptics"
[    36.857] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    36.857] (II) Module synaptics: vendor="X.Org Foundation"
[    36.857]     compiled for 1.9.0, module version = 1.2.2
[    36.857]     Module class: X.Org XInput Driver
[    36.857]     ABI class: X.Org XInput driver, version 11.0
[    36.857] (II) Synaptics touchpad driver version 1.2.2
[    36.857] (**) Option "Device" "/dev/input/event7"
[    36.905] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    36.905] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    36.905] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    36.905] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    36.905] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    36.937] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    36.937] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    36.953] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    36.953] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    36.953] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    36.953] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    36.953] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    36.985] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    36.985] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    36.985] (II) No input driver/identifier specified (ignoring)
[    37.240] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    37.240] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    37.240] (II) RADEON(0): Added native panel mode: 1440x900
[    37.277] Dac detection success
[    37.277] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    37.277] Unhandled monitor type 0
[    37.278] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    37.278] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    37.278] (II) RADEON(0): Added native panel mode: 1440x900
[    37.315] Dac detection success
[    37.315] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    37.315] Unhandled monitor type 0
[    37.333] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    37.333] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    37.333] (II) RADEON(0): Added native panel mode: 1440x900
[    37.370] Dac detection success
[    37.370] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    37.370] Unhandled monitor type 0
[    37.371] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    37.371] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    37.371] (II) RADEON(0): Added native panel mode: 1440x900
[    37.408] Dac detection success
[    37.408] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    37.408] Unhandled monitor type 0
[    46.847] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    46.847] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    46.847] (II) RADEON(0): Added native panel mode: 1440x900
[    46.880] Dac detection success
[    46.880] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    46.880] Unhandled monitor type 0
[    46.900] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    46.901] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    46.901] (II) RADEON(0): Added native panel mode: 1440x900
[    46.933] Dac detection success
[    46.933] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    46.933] Unhandled monitor type 0
[    46.934] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    46.934] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    46.934] (II) RADEON(0): Added native panel mode: 1440x900
[    46.966] Dac detection success
[    46.966] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    46.966] Unhandled monitor type 0
[    46.967] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    46.967] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    46.967] (II) RADEON(0): Added native panel mode: 1440x900
[    46.994] Dac detection success
[    46.994] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    46.994] Unhandled monitor type 0
[    50.496] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    50.496] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    50.496] (II) RADEON(0): Added native panel mode: 1440x900
[    50.533] Dac detection success
[    50.533] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    50.533] Unhandled monitor type 0
[    53.009] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    53.009] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    53.009] (II) RADEON(0): Added native panel mode: 1440x900
[    53.045] Dac detection success
[    53.045] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    53.045] Unhandled monitor type 0
[   535.220] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   535.220] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[   535.220] (II) RADEON(0): Added native panel mode: 1440x900
[   535.261] Dac detection success
[   535.261] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   535.261] Unhandled monitor type 0

```

---

### Post by sikander3786 on 2010-11-28
Attach this one also.

/var/log/syslog

And please edit your above post, delete [/quote] and [quote] from the end and start and type [/code] at the end and [code] at the beginning of that Xorg.0.log. It would format it accordingly. Same for the syslog also.

---

### Post by sim0s on 2010-11-28
This is the system log.
The 1st log at 00.38 is having radeon.modeset=1 and after 00.40 that is having nomodeset

```

[Nov 29 00:37:29 Spy kernel: [ 2408.998253] show_signal_msg: 9 callbacks suppressed
Nov 29 00:37:29 Spy kernel: [ 2408.998262] Xorg[1281]: segfault at 0 ip 080a24b2 sp bfeb9bfc error 4 in Xorg[8048000+1a7000]
Nov 29 00:37:29 Spy NetworkManager[924]: <info> (wlan0): device state change: 8 -> 3 (reason 38)
Nov 29 00:37:29 Spy NetworkManager[924]: <info> (wlan0): deactivating device (reason: 38).
Nov 29 00:37:29 Spy kernel: [ 2409.139609] [drm] Num pipes: 3
Nov 29 00:37:29 Spy gdm-simple-slave[2678]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 29 00:37:29 Spy acpid: client 1281[0:0] has disconnected
Nov 29 00:37:29 Spy acpid: client connected from 2680[0:0]
Nov 29 00:37:29 Spy acpid: 1 client rule loaded
Nov 29 00:37:29 Spy NetworkManager[924]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1706
Nov 29 00:37:29 Spy avahi-daemon[928]: Withdrawing address record for 192.168.0.2 on wlan0.
Nov 29 00:37:29 Spy avahi-daemon[928]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.2.
Nov 29 00:37:29 Spy kernel: [ 2409.352115] wlan0: deauthenticating from e8:be:81:71:66:33 by local choice (reason=3)
Nov 29 00:37:29 Spy avahi-daemon[928]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov 29 00:37:29 Spy wpa_supplicant[997]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 29 00:37:29 Spy kernel: [ 2409.366204] cfg80211: All devices are disconnected, going to restore regulatory settings
Nov 29 00:37:29 Spy kernel: [ 2409.366215] cfg80211: Restoring regulatory settings
Nov 29 00:37:29 Spy kernel: [ 2409.366222] cfg80211: Calling CRDA to update world regulatory domain
Nov 29 00:37:29 Spy NetworkManager[924]: <error> [1290991049.539751] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Nov 29 00:37:29 Spy kernel: [ 2409.385232] cfg80211: World regulatory domain updated:
Nov 29 00:37:29 Spy kernel: [ 2409.385237]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 29 00:37:29 Spy kernel: [ 2409.385241]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:37:29 Spy kernel: [ 2409.385244]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:37:29 Spy kernel: [ 2409.385247]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:37:29 Spy kernel: [ 2409.385250]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:37:29 Spy kernel: [ 2409.385253]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:37:30 Spy kernel: [ 2409.832147] [drm] Setting GART location based on new memory map
Nov 29 00:37:30 Spy kernel: [ 2409.835175] [drm] Loading R500 Microcode
Nov 29 00:37:30 Spy kernel: [ 2409.837900] [drm] Num pipes: 3
Nov 29 00:37:30 Spy kernel: [ 2409.837914] [drm] writeback test succeeded in 1 usecs
Nov 29 00:37:30 Spy NetworkManager[924]: <error> [1290991050.787731] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Nov 29 00:37:31 Spy gdm-session-worker[2737]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 29 00:37:31 Spy rtkit-daemon[1373]: Successfully made thread 2743 of process 2743 (n/a) owned by '113' high priority at nice level -11.
Nov 29 00:37:31 Spy rtkit-daemon[1373]: Supervising 1 threads of 1 processes of 1 users.
Nov 29 00:37:31 Spy rtkit-daemon[1373]: Successfully made thread 2746 of process 2743 (n/a) owned by '113' RT at priority 5.
Nov 29 00:37:31 Spy rtkit-daemon[1373]: Supervising 2 threads of 1 processes of 1 users.
Nov 29 00:37:31 Spy gdm-simple-greeter[2735]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Nov 29 00:37:31 Spy rtkit-daemon[1373]: Successfully made thread 2748 of process 2743 (n/a) owned by '113' RT at priority 5.
Nov 29 00:37:31 Spy rtkit-daemon[1373]: Supervising 3 threads of 1 processes of 1 users.
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 328.
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: snd_pcm_dump():
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: Soft volume PCM
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: Control: PCM Playback Volume
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: min_dB: -51
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: max_dB: 0
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: resolution: 256
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: Its setup is:
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   stream       : CAPTURE
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   access       : MMAP_INTERLEAVED
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   format       : S16_LE
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   subformat    : STD
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   channels     : 2
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   rate         : 44100
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   exact rate   : 44100 (44100/1)
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   msbits       : 16
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   buffer_size  : 88192
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   period_size  : 44096
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   period_time  : 999909
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   tstamp_mode  : ENABLE
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   period_step  : 1
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   avail_min    : 87310
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   period_event : 0
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   start_threshold  : -1
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   stop_threshold   : 1444937728
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   silence_threshold: 0
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   silence_size : 0
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   boundary     : 1444937728
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c: Its setup is:
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   stream       : CAPTURE
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   access       : MMAP_INTERLEAVED
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   format       : S16_LE
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   subformat    : STD
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   channels     : 2
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   rate         : 44100
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   exact rate   : 44100 (44100/1)
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   msbits       : 16
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   buffer_size  : 88192
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   period_size  : 44096
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   period_time  : 999909
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   tstamp_mode  : ENABLE
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   period_step  : 1
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   avail_min    : 87310
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   period_event : 0
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   start_threshold  : -1
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   stop_threshold   : 1444937728
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   silence_threshold: 0
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   silence_size : 0
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   boundary     : 1444937728
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   appl_ptr     : 87640
Nov 29 00:37:33 Spy pulseaudio[2743]: alsa-util.c:   hw_ptr       : 87640
Nov 29 00:37:35 Spy kernel: Kernel logging (proc) stopped.
Nov 29 00:37:35 Spy rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="873" x-info="http://www.rsyslog.com"] exiting on signal 15.
Nov 29 00:38:44 Spy kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 29 00:38:44 Spy rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="936" x-info="http://www.rsyslog.com"] (re)start
Nov 29 00:38:44 Spy rsyslogd: rsyslogd's groupid changed to 103
Nov 29 00:38:44 Spy rsyslogd: rsyslogd's userid changed to 101
Nov 29 00:38:44 Spy rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Nov 29 00:38:44 Spy kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 29 00:38:44 Spy kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 29 00:38:44 Spy kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
Nov 29 00:38:44 Spy kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 00000000000d6000 - 00000000000d8000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe90000 (usable)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 000000007fe90000 - 000000007fe9b000 (ACPI data)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 000000007fe9b000 - 000000007ff00000 (ACPI NVS)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Nov 29 00:38:44 Spy kernel: [    0.000000] DMI present.
Nov 29 00:38:44 Spy kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Nov 29 00:38:44 Spy kernel: [    0.000000] last_pfn = 0x7fe90 max_arch_pfn = 0x100000
Nov 29 00:38:44 Spy kernel: [    0.000000] MTRR default type: uncachable
Nov 29 00:38:44 Spy kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 29 00:38:44 Spy kernel: [    0.000000]   00000-9FFFF write-back
Nov 29 00:38:44 Spy kernel: [    0.000000]   A0000-BFFFF uncachable
Nov 29 00:38:44 Spy kernel: [    0.000000]   C0000-CFFFF write-protect
Nov 29 00:38:44 Spy kernel: [    0.000000]   D0000-DFFFF uncachable
Nov 29 00:38:44 Spy kernel: [    0.000000]   E0000-FFFFF write-protect
Nov 29 00:38:44 Spy kernel: [    0.000000] MTRR variable ranges enabled:
Nov 29 00:38:44 Spy kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Nov 29 00:38:44 Spy kernel: [    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
Nov 29 00:38:44 Spy kernel: [    0.000000]   2 disabled
Nov 29 00:38:44 Spy kernel: [    0.000000]   3 disabled
Nov 29 00:38:44 Spy kernel: [    0.000000]   4 disabled
Nov 29 00:38:44 Spy kernel: [    0.000000]   5 disabled
Nov 29 00:38:44 Spy kernel: [    0.000000]   6 disabled
Nov 29 00:38:44 Spy kernel: [    0.000000]   7 disabled
Nov 29 00:38:44 Spy kernel: [    0.000000] PAT not supported by CPU.
Nov 29 00:38:44 Spy kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 29 00:38:44 Spy kernel: [    0.000000] modified physical RAM map:
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 00000000000d6000 - 00000000000d8000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 0000000000100000 - 000000007fe90000 (usable)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 000000007fe90000 - 000000007fe9b000 (ACPI data)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 000000007fe9b000 - 000000007ff00000 (ACPI NVS)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 000000007ff00000 - 0000000080000000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Nov 29 00:38:44 Spy kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Nov 29 00:38:44 Spy kernel: [    0.000000] found SMP MP-table at [c00f7960] f7960
Nov 29 00:38:44 Spy kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Nov 29 00:38:44 Spy kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Nov 29 00:38:44 Spy kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Nov 29 00:38:44 Spy kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Nov 29 00:38:44 Spy kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
Nov 29 00:38:44 Spy kernel: [    0.000000] RAMDISK: 375ad000 - 37ff0000
Nov 29 00:38:44 Spy kernel: [    0.000000] Allocated new RAMDISK: 009a5000 - 013e7c3f
Nov 29 00:38:44 Spy kernel: [    0.000000] Move RAMDISK from 00000000375ad000 - 0000000037fefc3e to 009a5000 - 013e7c3e
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: RSDP 000f78b0 00014 (v00 PTLTD )
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: RSDT 7fe951a7 00044 (v01 PTLTD  Capell00 06040000  LTP 00000000)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: FACP 7fe9ae20 00074 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: DSDT 7fe95dec 05034 (v01 UW____ F28_____ 06040000 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: FACS 7fe9bfc0 00040
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: APIC 7fe9ae94 00068 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: HPET 7fe9aefc 00038 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: MCFG 7fe9af34 0003C (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: APIC 7fe9af70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: BOOT 7fe9afd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: SSDT 7fe95be2 0020A (v01 SataRe SataAhci 00001000 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: SSDT 7fe951eb 004F6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 29 00:38:44 Spy kernel: [    0.000000] 1158MB HIGHMEM available.
Nov 29 00:38:44 Spy kernel: [    0.000000] 887MB LOWMEM available.
Nov 29 00:38:44 Spy kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Nov 29 00:38:44 Spy kernel: [    0.000000]   low ram: 0 - 377fe000
Nov 29 00:38:44 Spy kernel: [    0.000000] Zone PFN ranges:
Nov 29 00:38:44 Spy kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Nov 29 00:38:44 Spy kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Nov 29 00:38:44 Spy kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007fe90
Nov 29 00:38:44 Spy kernel: [    0.000000] Movable zone start PFN for each node
Nov 29 00:38:44 Spy kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov 29 00:38:44 Spy kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Nov 29 00:38:44 Spy kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Nov 29 00:38:44 Spy kernel: [    0.000000]     0: 0x00000100 -> 0x0007fe90
Nov 29 00:38:44 Spy kernel: [    0.000000] On node 0 totalpages: 523808
Nov 29 00:38:44 Spy kernel: [    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c13e9020
Nov 29 00:38:44 Spy kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov 29 00:38:44 Spy kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 29 00:38:44 Spy kernel: [    0.000000]   DMA zone: 3952 pages, LIFO batch:0
Nov 29 00:38:44 Spy kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Nov 29 00:38:44 Spy kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Nov 29 00:38:44 Spy kernel: [    0.000000]   HighMem zone: 2318 pages used for memmap
Nov 29 00:38:44 Spy kernel: [    0.000000]   HighMem zone: 294276 pages, LIFO batch:31
Nov 29 00:38:44 Spy kernel: [    0.000000] Using APIC driver default
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov 29 00:38:44 Spy kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 29 00:38:44 Spy kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 29 00:38:44 Spy kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Nov 29 00:38:44 Spy kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Nov 29 00:38:44 Spy kernel: [    0.000000] nr_irqs_gsi: 40
Nov 29 00:38:44 Spy kernel: [    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
Nov 29 00:38:44 Spy kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Nov 29 00:38:44 Spy kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov 29 00:38:44 Spy kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d6000
Nov 29 00:38:44 Spy kernel: [    0.000000] PM: Registered nosave memory: 00000000000d6000 - 00000000000d8000
Nov 29 00:38:44 Spy kernel: [    0.000000] PM: Registered nosave memory: 00000000000d8000 - 00000000000e4000
Nov 29 00:38:44 Spy kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Nov 29 00:38:44 Spy kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
Nov 29 00:38:44 Spy kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 29 00:38:44 Spy kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Nov 29 00:38:44 Spy kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u2097152
Nov 29 00:38:44 Spy kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
Nov 29 00:38:44 Spy kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Nov 29 00:38:44 Spy kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519714
Nov 29 00:38:44 Spy kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=7dcd1223-5689-4e8d-b393-e703940a0fc6 ro radeon.modeset=1
Nov 29 00:38:44 Spy kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Nov 29 00:38:44 Spy kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 29 00:38:44 Spy kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 29 00:38:44 Spy kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 29 00:38:44 Spy kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 29 00:38:44 Spy kernel: [    0.000000] Initializing CPU#0
Nov 29 00:38:44 Spy kernel: [    0.000000] allocated 10478380 bytes of page_cgroup
Nov 29 00:38:44 Spy kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 29 00:38:44 Spy kernel: [    0.000000] Subtract (55 early reservations)
Nov 29 00:38:44 Spy kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Nov 29 00:38:44 Spy kernel: [    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
Nov 29 00:38:44 Spy kernel: [    0.000000]   #3 [00009a1000 - 00009a416c]             BRK
Nov 29 00:38:44 Spy kernel: [    0.000000]   #4 [00000f7970 - 0000100000]   BIOS reserved
Nov 29 00:38:44 Spy kernel: [    0.000000]   #5 [00000f7960 - 00000f7970]    MP-table mpf
Nov 29 00:38:44 Spy kernel: [    0.000000]   #6 [000009f000 - 000009fd71]   BIOS reserved
Nov 29 00:38:44 Spy kernel: [    0.000000]   #7 [000009feb5 - 00000f7960]   BIOS reserved
Nov 29 00:38:44 Spy kernel: [    0.000000]   #8 [000009fd71 - 000009feb5]    MP-table mpc
Nov 29 00:38:44 Spy kernel: [    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
Nov 29 00:38:44 Spy kernel: [    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
Nov 29 00:38:44 Spy kernel: [    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
Nov 29 00:38:44 Spy kernel: [    0.000000]   #12 [00009a5000 - 00013e8000]     NEW RAMDISK
Nov 29 00:38:44 Spy kernel: [    0.000000]   #13 [00013e8000 - 00013e9000]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #14 [00013e9000 - 00023e9000]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #15 [00023e9000 - 00023e9004]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #16 [00023e9040 - 00023e9100]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #17 [00023e9100 - 00023e9154]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #18 [00023e9180 - 00023ec180]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #19 [00023ec180 - 00023ec1f0]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #20 [00023ec200 - 00023f2200]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #21 [00023f2200 - 00023f2225]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #22 [00023f2240 - 00023f2267]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #23 [00023f2280 - 00023f2478]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #24 [00023f2480 - 00023f24c0]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #25 [00023f24c0 - 00023f2500]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #26 [00023f2500 - 00023f2540]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #27 [00023f2540 - 00023f2580]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #28 [00023f2580 - 00023f25c0]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #29 [00023f25c0 - 00023f2600]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #30 [00023f2600 - 00023f2640]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #31 [00023f2640 - 00023f2680]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #32 [00023f2680 - 00023f26c0]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #33 [00023f26c0 - 00023f2700]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #34 [00023f2700 - 00023f2740]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #35 [00023f2740 - 00023f2780]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #36 [00023f2780 - 00023f27c0]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #37 [00023f27c0 - 00023f2800]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #38 [00023f2800 - 00023f2840]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #39 [00023f2840 - 00023f2850]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #40 [00023f2880 - 00023f2890]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #41 [00023f28c0 - 00023f292e]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #42 [00023f2940 - 00023f29ae]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #43 [0002400000 - 000240e000]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #44 [0002600000 - 000260e000]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #45 [00023f49c0 - 00023f49c4]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #46 [00023f4a00 - 00023f4a04]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #47 [00023f4a40 - 00023f4a48]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #48 [00023f4a80 - 00023f4a88]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #49 [00023f4ac0 - 00023f4b68]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #50 [00023f4b80 - 00023f4be8]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #51 [00023f4c00 - 00023f8c00]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #52 [000240e000 - 000248e000]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #53 [000248e000 - 00024ce000]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000]   #54 [000260e000 - 000300c32c]         BOOTMEM
Nov 29 00:38:44 Spy kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007fe90)
Nov 29 00:38:44 Spy kernel: [    0.000000] Memory: 2048280k/2095680k available (4928k kernel code, 46952k reserved, 2336k data, 684k init, 1186376k highmem)
Nov 29 00:38:44 Spy kernel: [    0.000000] virtual kernel memory layout:
Nov 29 00:38:44 Spy kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Nov 29 00:38:44 Spy kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 29 00:38:44 Spy kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Nov 29 00:38:44 Spy kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Nov 29 00:38:44 Spy kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
Nov 29 00:38:44 Spy kernel: [    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
Nov 29 00:38:44 Spy kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
Nov 29 00:38:44 Spy kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov 29 00:38:44 Spy kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Nov 29 00:38:44 Spy kernel: [    0.000000] Hierarchical RCU implementation.
Nov 29 00:38:44 Spy kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Nov 29 00:38:44 Spy kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Nov 29 00:38:44 Spy kernel: [    0.000000]     Verbose stalled-CPUs detection is disabled.
Nov 29 00:38:44 Spy kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512
Nov 29 00:38:44 Spy kernel: [    0.000000] Console: colour VGA+ 80x25
Nov 29 00:38:44 Spy kernel: [    0.000000] console [tty0] enabled
Nov 29 00:38:44 Spy kernel: [    0.000000] hpet clockevent registered
Nov 29 00:38:44 Spy kernel: [    0.000000] Fast TSC calibration using PIT
Nov 29 00:38:44 Spy kernel: [    0.000000] Detected 2161.174 MHz processor.
Nov 29 00:38:44 Spy kernel: [    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4322.34 BogoMIPS (lpj=8644696)
Nov 29 00:38:44 Spy kernel: [    0.004100] pid_max: default: 32768 minimum: 301
Nov 29 00:38:44 Spy kernel: [    0.004163] Security Framework initialized
Nov 29 00:38:44 Spy kernel: [    0.004226] AppArmor: AppArmor initialized
Nov 29 00:38:44 Spy kernel: [    0.004271] Yama: becoming mindful.
Nov 29 00:38:44 Spy kernel: [    0.004373] Mount-cache hash table entries: 512
Nov 29 00:38:44 Spy kernel: [    0.004554] Initializing cgroup subsys ns
Nov 29 00:38:44 Spy kernel: [    0.004603] Initializing cgroup subsys cpuacct
Nov 29 00:38:44 Spy kernel: [    0.004651] Initializing cgroup subsys memory
Nov 29 00:38:44 Spy kernel: [    0.004704] Initializing cgroup subsys devices
Nov 29 00:38:44 Spy kernel: [    0.004751] Initializing cgroup subsys freezer
Nov 29 00:38:44 Spy kernel: [    0.004798] Initializing cgroup subsys net_cls
Nov 29 00:38:44 Spy kernel: [    0.004869] CPU: Physical Processor ID: 0
Nov 29 00:38:44 Spy kernel: [    0.004914] CPU: Processor Core ID: 0
Nov 29 00:38:44 Spy kernel: [    0.004960] mce: CPU supports 6 MCE banks
Nov 29 00:38:44 Spy kernel: [    0.005014] CPU0: Thermal monitoring enabled (TM2)
Nov 29 00:38:44 Spy kernel: [    0.005063] using mwait in idle threads.
Nov 29 00:38:44 Spy kernel: [    0.005113] Performance Events: Core events, core PMU driver.
Nov 29 00:38:44 Spy kernel: [    0.005236] ... version:                1
Nov 29 00:38:44 Spy kernel: [    0.005281] ... bit width:              40
Nov 29 00:38:44 Spy kernel: [    0.005327] ... generic registers:      2
Nov 29 00:38:44 Spy kernel: [    0.005371] ... value mask:             000000ffffffffff
Nov 29 00:38:44 Spy kernel: [    0.005418] ... max period:             000000007fffffff
Nov 29 00:38:44 Spy kernel: [    0.005465] ... fixed-purpose events:   0
Nov 29 00:38:44 Spy kernel: [    0.005510] ... event mask:             0000000000000003
Nov 29 00:38:44 Spy kernel: [    0.011074] ACPI: Core revision 20100428
Nov 29 00:38:44 Spy kernel: [    0.019046] ftrace: converting mcount calls to 0f 1f 44 00 00
Nov 29 00:38:44 Spy kernel: [    0.019098] ftrace: allocating 21758 entries in 43 pages
Nov 29 00:38:44 Spy kernel: [    0.020060] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 29 00:38:44 Spy kernel: [    0.020485] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 29 00:38:44 Spy kernel: [    0.062214] CPU0: Genuine Intel(R) CPU           T2600  @ 2.16GHz stepping 08
Nov 29 00:38:44 Spy kernel: [    0.064000] Booting Node   0, Processors  #1 Ok.
Nov 29 00:38:44 Spy kernel: [    0.008000] Initializing CPU#1
Nov 29 00:38:44 Spy kernel: [    0.152020] Brought up 2 CPUs
Nov 29 00:38:44 Spy kernel: [    0.152112] Total of 2 processors activated (8644.79 BogoMIPS).
Nov 29 00:38:44 Spy kernel: [    0.152677] devtmpfs: initialized
Nov 29 00:38:44 Spy kernel: [    0.153039] regulator: core version 0.5
Nov 29 00:38:44 Spy kernel: [    0.153116] Time:  0:38:10  Date: 11/29/10
Nov 29 00:38:44 Spy kernel: [    0.153201] NET: Registered protocol family 16
Nov 29 00:38:44 Spy kernel: [    0.153275] Trying to unpack rootfs image as initramfs...
Nov 29 00:38:44 Spy kernel: [    0.153383] EISA bus registered
Nov 29 00:38:44 Spy kernel: [    0.153393] ACPI: bus type pci registered
Nov 29 00:38:44 Spy kernel: [    0.153475] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Nov 29 00:38:44 Spy kernel: [    0.153479] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Nov 29 00:38:44 Spy kernel: [    0.153480] PCI: Using MMCONFIG for extended config space
Nov 29 00:38:44 Spy kernel: [    0.153484] PCI: Using configuration type 1 for base access
Nov 29 00:38:44 Spy kernel: [    0.160169] bio: create slab <bio-0> at 0
Nov 29 00:38:44 Spy kernel: [    0.161577] ACPI: EC: Look up EC in DSDT
Nov 29 00:38:44 Spy kernel: [    0.164293] ACPI: BIOS _OSI(Linux) query ignored
Nov 29 00:38:44 Spy kernel: [    0.165496] ACPI: SSDT 7fe95931 00228 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.166006] ACPI: Dynamic OEM Table Load:
Nov 29 00:38:44 Spy kernel: [    0.166127] ACPI: SSDT (null) 00228 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.166447] ACPI: SSDT 7fe956e1 001CB (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.166931] ACPI: Dynamic OEM Table Load:
Nov 29 00:38:44 Spy kernel: [    0.167050] ACPI: SSDT (null) 001CB (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.167584] ACPI: SSDT 7fe95b59 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.168106] ACPI: Dynamic OEM Table Load:
Nov 29 00:38:44 Spy kernel: [    0.168224] ACPI: SSDT (null) 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.168498] ACPI: SSDT 7fe958ac 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.168984] ACPI: Dynamic OEM Table Load:
Nov 29 00:38:44 Spy kernel: [    0.169104] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Nov 29 00:38:44 Spy kernel: [    0.434628] Freeing initrd memory: 10508k freed
Nov 29 00:38:44 Spy kernel: [   18.168077] ACPI: Interpreter enabled
Nov 29 00:38:44 Spy kernel: [   18.168132] ACPI: (supports S0 S3 S4 S5)
Nov 29 00:38:44 Spy kernel: [   18.168341] ACPI: Using IOAPIC for interrupt routing
Nov 29 00:38:44 Spy kernel: [   18.176012] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Nov 29 00:38:44 Spy kernel: [   18.176435] ACPI: No dock devices found.
Nov 29 00:38:44 Spy kernel: [   18.176484] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Nov 29 00:38:44 Spy kernel: [   18.177066] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Nov 29 00:38:44 Spy kernel: [   18.178129] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Nov 29 00:38:44 Spy kernel: [   18.178133] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
Nov 29 00:38:44 Spy kernel: [   18.178136] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Nov 29 00:38:44 Spy kernel: [   18.178139] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
Nov 29 00:38:44 Spy kernel: [   18.178142] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
Nov 29 00:38:44 Spy kernel: [   18.178145] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff] (ignored)
Nov 29 00:38:44 Spy kernel: [   18.178148] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
Nov 29 00:38:44 Spy kernel: [   18.178234] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Nov 29 00:38:44 Spy kernel: [   18.178238] pci 0000:00:01.0: PME# disabled
Nov 29 00:38:44 Spy kernel: [   18.178318] pci 0000:00:1b.0: reg 10: [mem 0xb0000000-0xb0003fff 64bit]
Nov 29 00:38:44 Spy kernel: [   18.178378] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Nov 29 00:38:44 Spy kernel: [   18.178383] pci 0000:00:1b.0: PME# disabled
Nov 29 00:38:44 Spy kernel: [   18.178479] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Nov 29 00:38:44 Spy kernel: [   18.178484] pci 0000:00:1c.0: PME# disabled
Nov 29 00:38:44 Spy kernel: [   18.178585] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Nov 29 00:38:44 Spy kernel: [   18.178590] pci 0000:00:1c.2: PME# disabled
Nov 29 00:38:44 Spy kernel: [   18.178656] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
Nov 29 00:38:44 Spy kernel: [   18.178718] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
Nov 29 00:38:44 Spy kernel: [   18.178780] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
Nov 29 00:38:44 Spy kernel: [   18.178842] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
Nov 29 00:38:44 Spy kernel: [   18.178900] pci 0000:00:1d.7: reg 10: [mem 0xb0004000-0xb00043ff]
Nov 29 00:38:44 Spy kernel: [   18.178962] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Nov 29 00:38:44 Spy kernel: [   18.178968] pci 0000:00:1d.7: PME# disabled
Nov 29 00:38:44 Spy kernel: [   18.179129] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Nov 29 00:38:44 Spy kernel: [   18.179188] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
Nov 29 00:38:44 Spy kernel: [   18.179240] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0068 (mask 0007)
Nov 29 00:38:44 Spy kernel: [   18.179298] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0200 (mask 000f)
Nov 29 00:38:44 Spy kernel: [   18.179406] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
Nov 29 00:38:44 Spy kernel: [   18.179414] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
Nov 29 00:38:44 Spy kernel: [   18.179422] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
Nov 29 00:38:44 Spy kernel: [   18.179429] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
Nov 29 00:38:44 Spy kernel: [   18.179437] pci 0000:00:1f.1: reg 20: [io  0x1880-0x188f]
Nov 29 00:38:44 Spy kernel: [   18.179493] pci 0000:00:1f.2: reg 10: [io  0x18c8-0x18cf]
Nov 29 00:38:44 Spy kernel: [   18.179501] pci 0000:00:1f.2: reg 14: [io  0x18ac-0x18af]
Nov 29 00:38:44 Spy kernel: [   18.179509] pci 0000:00:1f.2: reg 18: [io  0x18c0-0x18c7]
Nov 29 00:38:44 Spy kernel: [   18.179517] pci 0000:00:1f.2: reg 1c: [io  0x18a8-0x18ab]
Nov 29 00:38:44 Spy kernel: [   18.179525] pci 0000:00:1f.2: reg 20: [io  0x18b0-0x18bf]
Nov 29 00:38:44 Spy kernel: [   18.179533] pci 0000:00:1f.2: reg 24: [mem 0xb0004400-0xb00047ff]
Nov 29 00:38:44 Spy kernel: [   18.179570] pci 0000:00:1f.2: PME# supported from D3hot
Nov 29 00:38:44 Spy kernel: [   18.179575] pci 0000:00:1f.2: PME# disabled
Nov 29 00:38:44 Spy kernel: [   18.179638] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
Nov 29 00:38:44 Spy kernel: [   18.179719] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
Nov 29 00:38:44 Spy kernel: [   18.179725] pci 0000:01:00.0: reg 14: [io  0x2000-0x20ff]
Nov 29 00:38:44 Spy kernel: [   18.179731] pci 0000:01:00.0: reg 18: [mem 0xb0100000-0xb010ffff]
Nov 29 00:38:44 Spy kernel: [   18.179747] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Nov 29 00:38:44 Spy kernel: [   18.179764] pci 0000:01:00.0: supports D1 D2
Nov 29 00:38:44 Spy kernel: [   18.179774] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Nov 29 00:38:44 Spy kernel: [   18.179840] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov 29 00:38:44 Spy kernel: [   18.179889] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
Nov 29 00:38:44 Spy kernel: [   18.179893] pci 0000:00:01.0:   bridge window [mem 0xb0100000-0xb01fffff]
Nov 29 00:38:44 Spy kernel: [   18.179898] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Nov 29 00:38:44 Spy kernel: [   18.179958] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
Nov 29 00:38:44 Spy kernel: [   18.180005] pci 0000:00:1c.0:   bridge window [io  0x0000-0xf000] (disabled)
Nov 29 00:38:44 Spy kernel: [   18.180011] pci 0000:00:1c.0:   bridge window [mem 0xfac00000-0xfebfffff]
Nov 29 00:38:44 Spy kernel: [   18.180019] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Nov 29 00:38:44 Spy kernel: [   18.180177] pci 0000:04:00.0: reg 10: [mem 0xb0200000-0xb0200fff]
Nov 29 00:38:44 Spy kernel: [   18.180419] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
Nov 29 00:38:44 Spy kernel: [   18.180431] pci 0000:04:00.0: PME# disabled
Nov 29 00:38:44 Spy kernel: [   18.180501] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Nov 29 00:38:44 Spy kernel: [   18.180585] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
Nov 29 00:38:44 Spy kernel: [   18.180635] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
Nov 29 00:38:44 Spy kernel: [   18.180641] pci 0000:00:1c.2:   bridge window [mem 0xb0200000-0xb02fffff]
Nov 29 00:38:44 Spy kernel: [   18.180649] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Nov 29 00:38:44 Spy kernel: [   18.180721] pci 0000:05:04.0: reg 10: [mem 0xb0304000-0xb03047ff]
Nov 29 00:38:44 Spy kernel: [   18.180731] pci 0000:05:04.0: reg 14: [mem 0xb0300000-0xb0303fff]
Nov 29 00:38:44 Spy kernel: [   18.180794] pci 0000:05:04.0: supports D1 D2
Nov 29 00:38:44 Spy kernel: [   18.180796] pci 0000:05:04.0: PME# supported from D0 D1 D2 D3hot
Nov 29 00:38:44 Spy kernel: [   18.180802] pci 0000:05:04.0: PME# disabled
Nov 29 00:38:44 Spy kernel: [   18.180842] pci 0000:05:05.0: reg 10: [io  0x3000-0x30ff]
Nov 29 00:38:44 Spy kernel: [   18.180852] pci 0000:05:05.0: reg 14: [mem 0xb0304800-0xb03048ff]
Nov 29 00:38:44 Spy kernel: [   18.180888] pci 0000:05:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Nov 29 00:38:44 Spy kernel: [   18.180915] pci 0000:05:05.0: supports D1 D2
Nov 29 00:38:44 Spy kernel: [   18.180917] pci 0000:05:05.0: PME# supported from D1 D2 D3hot D3cold
Nov 29 00:38:44 Spy kernel: [   18.180923] pci 0000:05:05.0: PME# disabled
Nov 29 00:38:44 Spy kernel: [   18.180967] pci 0000:05:07.0: reg 10: [io  0x3850-0x385f]
Nov 29 00:38:44 Spy kernel: [   18.180976] pci 0000:05:07.0: reg 14: [io  0x3840-0x384f]
Nov 29 00:38:44 Spy kernel: [   18.180985] pci 0000:05:07.0: reg 18: [io  0x3830-0x383f]
Nov 29 00:38:44 Spy kernel: [   18.180995] pci 0000:05:07.0: reg 1c: [io  0x3820-0x382f]
Nov 29 00:38:44 Spy kernel: [   18.181005] pci 0000:05:07.0: reg 20: [io  0x3800-0x381f]
Nov 29 00:38:44 Spy kernel: [   18.181014] pci 0000:05:07.0: reg 24: [io  0x3400-0x34ff]
Nov 29 00:38:44 Spy kernel: [   18.181098] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
Nov 29 00:38:44 Spy kernel: [   18.181150] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
Nov 29 00:38:44 Spy kernel: [   18.181155] pci 0000:00:1e.0:   bridge window [mem 0xb0300000-0xb03fffff]
Nov 29 00:38:44 Spy kernel: [   18.181164] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Nov 29 00:38:44 Spy kernel: [   18.181167] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Nov 29 00:38:44 Spy kernel: [   18.181170] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Nov 29 00:38:44 Spy kernel: [   18.181193] pci_bus 0000:00: on NUMA node 0
Nov 29 00:38:44 Spy kernel: [   18.181198] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 29 00:38:44 Spy kernel: [   18.181409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
Nov 29 00:38:44 Spy kernel: [   18.181500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Nov 29 00:38:44 Spy kernel: [   18.181579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Nov 29 00:38:44 Spy kernel: [   18.181693] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Nov 29 00:38:44 Spy kernel: [   18.185895] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Nov 29 00:38:44 Spy kernel: [   18.186501] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *7 11 12 14 15)
Nov 29 00:38:44 Spy kernel: [   18.187062] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
Nov 29 00:38:44 Spy kernel: [   18.187622] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Nov 29 00:38:44 Spy kernel: [   18.188210] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Nov 29 00:38:44 Spy kernel: [   18.188848] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Nov 29 00:38:44 Spy kernel: [   18.189486] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 *4 5 6 7 10 12 14 15)
Nov 29 00:38:44 Spy kernel: [   18.190047] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
Nov 29 00:38:44 Spy kernel: [   18.190554] HEST: Table is not found!
Nov 29 00:38:44 Spy kernel: [   18.190688] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Nov 29 00:38:44 Spy kernel: [   18.190747] vgaarb: loaded
Nov 29 00:38:44 Spy kernel: [   18.190973] SCSI subsystem initialized
Nov 29 00:38:44 Spy kernel: [   18.191031] libata version 3.00 loaded.
Nov 29 00:38:44 Spy kernel: [   18.191031] usbcore: registered new interface driver usbfs
Nov 29 00:38:44 Spy kernel: [   18.191031] usbcore: registered new interface driver hub
Nov 29 00:38:44 Spy kernel: [   18.191031] usbcore: registered new device driver usb
Nov 29 00:38:44 Spy kernel: [   18.191031] ACPI: WMI: Mapper loaded
Nov 29 00:38:44 Spy kernel: [   18.191031] PCI: Using ACPI for IRQ routing
Nov 29 00:38:44 Spy kernel: [   18.191031] PCI: pci_cache_line_size set to 64 bytes
Nov 29 00:38:44 Spy kernel: [   18.191031] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
Nov 29 00:38:44 Spy kernel: [   18.191031] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
Nov 29 00:38:44 Spy kernel: [   18.191031] reserve RAM buffer: 000000007fe90000 - 000000007fffffff 
Nov 29 00:38:44 Spy kernel: [   18.191031] NetLabel: Initializing
Nov 29 00:38:44 Spy kernel: [   18.191031] NetLabel:  domain hash size = 128
Nov 29 00:38:44 Spy kernel: [   18.191031] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 29 00:38:44 Spy kernel: [   18.192015] NetLabel:  unlabeled traffic allowed by default
Nov 29 00:38:44 Spy kernel: [   18.192103] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Nov 29 00:38:44 Spy kernel: [   18.192157] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Nov 29 00:38:44 Spy kernel: [   18.192345] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Nov 29 00:38:44 Spy kernel: [   18.196019] Switching to clocksource tsc
Nov 29 00:38:44 Spy kernel: [   18.207144] AppArmor: AppArmor Filesystem Enabled
Nov 29 00:38:44 Spy kernel: [   18.207215] pnp: PnP ACPI init
Nov 29 00:38:44 Spy kernel: [   18.207282] ACPI: bus type pnp registered
Nov 29 00:38:44 Spy kernel: [   18.210988] pnp: PnP ACPI: found 11 devices
Nov 29 00:38:44 Spy kernel: [   18.211035] ACPI: ACPI bus type pnp unregistered
Nov 29 00:38:44 Spy kernel: [   18.211084] PnPBIOS: Disabled by ACPI PNP
Nov 29 00:38:44 Spy kernel: [   18.211142] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211193] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211243] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211295] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211345] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211395] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211446] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211496] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211549] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211607] system 00:06: [io  0x0680-0x069f] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211656] system 00:06: [io  0x0800-0x080f] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211705] system 00:06: [io  0x1000-0x107f] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211754] system 00:06: [io  0x1180-0x11bf] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211803] system 00:06: [io  0x1640-0x164f] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211854] system 00:07: [io  0x06a0-0x06af] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.211903] system 00:07: [io  0x06b0-0x06ff] has been reserved
Nov 29 00:38:44 Spy kernel: [   18.248068] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
Nov 29 00:38:44 Spy kernel: [   18.248125] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
Nov 29 00:38:44 Spy kernel: [   18.248182] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80400000-0x804fffff pref]
Nov 29 00:38:44 Spy kernel: [   18.248239] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
Nov 29 00:38:44 Spy kernel: [   18.248288] pci 0000:00:1c.2: BAR 13: assigned [io  0x5000-0x5fff]
Nov 29 00:38:44 Spy kernel: [   18.248338] pci 0000:01:00.0: BAR 6: assigned [mem 0xb0120000-0xb013ffff pref]
Nov 29 00:38:44 Spy kernel: [   18.248395] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Nov 29 00:38:44 Spy kernel: [   18.248443] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
Nov 29 00:38:44 Spy kernel: [   18.248494] pci 0000:00:01.0:   bridge window [mem 0xb0100000-0xb01fffff]
Nov 29 00:38:44 Spy kernel: [   18.248545] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Nov 29 00:38:44 Spy kernel: [   18.248604] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
Nov 29 00:38:44 Spy kernel: [   18.248653] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
Nov 29 00:38:44 Spy kernel: [   18.248705] pci 0000:00:1c.0:   bridge window [mem 0xfac00000-0xfebfffff]
Nov 29 00:38:44 Spy kernel: [   18.248757] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
Nov 29 00:38:44 Spy kernel: [   18.248818] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
Nov 29 00:38:44 Spy kernel: [   18.248867] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
Nov 29 00:38:44 Spy kernel: [   18.248919] pci 0000:00:1c.2:   bridge window [mem 0xb0200000-0xb02fffff]
Nov 29 00:38:44 Spy kernel: [   18.248972] pci 0000:00:1c.2:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
Nov 29 00:38:44 Spy kernel: [   18.249035] pci 0000:05:05.0: BAR 6: assigned [mem 0x80400000-0x8041ffff pref]
Nov 29 00:38:44 Spy kernel: [   18.249090] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
Nov 29 00:38:44 Spy kernel: [   18.249139] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
Nov 29 00:38:44 Spy kernel: [   18.249906] pci 0000:00:1e.0:   bridge window [mem 0xb0300000-0xb03fffff]
Nov 29 00:38:44 Spy kernel: [   18.249958] pci 0000:00:1e.0:   bridge window [mem 0x80400000-0x804fffff pref]
Nov 29 00:38:44 Spy kernel: [   18.250027]   alloc irq_desc for 16 on node -1
Nov 29 00:38:44 Spy kernel: [   18.250029]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   18.250035] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 29 00:38:44 Spy kernel: [   18.250087] pci 0000:00:01.0: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.250097] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Nov 29 00:38:44 Spy kernel: [   18.250146]   alloc irq_desc for 17 on node -1
Nov 29 00:38:44 Spy kernel: [   18.250148]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   18.250152] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 29 00:38:44 Spy kernel: [   18.250206] pci 0000:00:1c.0: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.250217] pci 0000:00:1c.2: enabling device (0000 -> 0003)
Nov 29 00:38:44 Spy kernel: [   18.250266]   alloc irq_desc for 18 on node -1
Nov 29 00:38:44 Spy kernel: [   18.250268]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   18.250272] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 29 00:38:44 Spy kernel: [   18.250325] pci 0000:00:1c.2: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.250334] pci 0000:00:1e.0: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.250339] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Nov 29 00:38:44 Spy kernel: [   18.250342] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Nov 29 00:38:44 Spy kernel: [   18.250345] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
Nov 29 00:38:44 Spy kernel: [   18.250347] pci_bus 0000:01: resource 1 [mem 0xb0100000-0xb01fffff]
Nov 29 00:38:44 Spy kernel: [   18.250350] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Nov 29 00:38:44 Spy kernel: [   18.250353] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
Nov 29 00:38:44 Spy kernel: [   18.250356] pci_bus 0000:02: resource 1 [mem 0xfac00000-0xfebfffff]
Nov 29 00:38:44 Spy kernel: [   18.250359] pci_bus 0000:02: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
Nov 29 00:38:44 Spy kernel: [   18.250362] pci_bus 0000:04: resource 0 [io  0x5000-0x5fff]
Nov 29 00:38:44 Spy kernel: [   18.250365] pci_bus 0000:04: resource 1 [mem 0xb0200000-0xb02fffff]
Nov 29 00:38:44 Spy kernel: [   18.250367] pci_bus 0000:04: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
Nov 29 00:38:44 Spy kernel: [   18.250370] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
Nov 29 00:38:44 Spy kernel: [   18.250373] pci_bus 0000:05: resource 1 [mem 0xb0300000-0xb03fffff]
Nov 29 00:38:44 Spy kernel: [   18.250376] pci_bus 0000:05: resource 2 [mem 0x80400000-0x804fffff pref]
Nov 29 00:38:44 Spy kernel: [   18.250379] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]
Nov 29 00:38:44 Spy kernel: [   18.250381] pci_bus 0000:05: resource 5 [mem 0x00000000-0xffffffff]
Nov 29 00:38:44 Spy kernel: [   18.250422] NET: Registered protocol family 2
Nov 29 00:38:44 Spy kernel: [   18.250537] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 29 00:38:44 Spy kernel: [   18.250844] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 29 00:38:44 Spy kernel: [   18.251514] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 29 00:38:44 Spy kernel: [   18.251871] TCP: Hash tables configured (established 131072 bind 65536)
Nov 29 00:38:44 Spy kernel: [   18.251920] TCP reno registered
Nov 29 00:38:44 Spy kernel: [   18.251967] UDP hash table entries: 512 (order: 2, 16384 bytes)
Nov 29 00:38:44 Spy kernel: [   18.252054] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Nov 29 00:38:44 Spy kernel: [   18.252213] NET: Registered protocol family 1
Nov 29 00:38:44 Spy kernel: [   18.252394] pci 0000:01:00.0: Boot video device
Nov 29 00:38:44 Spy kernel: [   18.252413] PCI: CLS 64 bytes, default 64
Nov 29 00:38:44 Spy kernel: [   18.252442] Simple Boot Flag at 0x36 set to 0x1
Nov 29 00:38:44 Spy kernel: [   18.252682] cpufreq-nforce2: No nForce2 chipset.
Nov 29 00:38:44 Spy kernel: [   18.252758] Scanning for low memory corruption every 60 seconds
Nov 29 00:38:44 Spy kernel: [   18.252971] audit: initializing netlink socket (disabled)
Nov 29 00:38:44 Spy kernel: [   18.253029] type=2000 audit(1290991108.252:1): initialized
Nov 29 00:38:44 Spy kernel: [   18.263830] highmem bounce pool size: 64 pages
Nov 29 00:38:44 Spy kernel: [   18.263880] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov 29 00:38:44 Spy kernel: [   18.265496] VFS: Disk quotas dquot_6.5.2
Nov 29 00:38:44 Spy kernel: [   18.265608] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 29 00:38:44 Spy kernel: [   18.266289] fuse init (API version 7.14)
Nov 29 00:38:44 Spy kernel: [   18.266429] msgmni has been set to 1703
Nov 29 00:38:44 Spy kernel: [   18.269124] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Nov 29 00:38:44 Spy kernel: [   18.269183] io scheduler noop registered
Nov 29 00:38:44 Spy kernel: [   18.269228] io scheduler deadline registered
Nov 29 00:38:44 Spy kernel: [   18.269288] io scheduler cfq registered (default)
Nov 29 00:38:44 Spy kernel: [   18.269447] pcieport 0000:00:01.0: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.269475]   alloc irq_desc for 40 on node -1
Nov 29 00:38:44 Spy kernel: [   18.269477]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   18.269487] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Nov 29 00:38:44 Spy kernel: [   18.269554] pcieport 0000:00:1c.0: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.269599]   alloc irq_desc for 41 on node -1
Nov 29 00:38:44 Spy kernel: [   18.269601]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   18.269610] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Nov 29 00:38:44 Spy kernel: [   18.269710] pcieport 0000:00:1c.2: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.269755]   alloc irq_desc for 42 on node -1
Nov 29 00:38:44 Spy kernel: [   18.269757]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   18.269766] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Nov 29 00:38:44 Spy kernel: [   18.269881] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 29 00:38:44 Spy kernel: [   18.270010] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 29 00:38:44 Spy kernel: [   18.270150] intel_idle: MWAIT substates: 0x22220
Nov 29 00:38:44 Spy kernel: [   18.270152] intel_idle: does not run on family 6 model 14
Nov 29 00:38:44 Spy kernel: [   18.271956] ACPI: AC Adapter [AC0] (on-line)
Nov 29 00:38:44 Spy kernel: [   18.272096] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Nov 29 00:38:44 Spy kernel: [   18.272188] ACPI: Lid Switch [LID0]
Nov 29 00:38:44 Spy kernel: [   18.272281] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Nov 29 00:38:44 Spy kernel: [   18.272340] ACPI: Power Button [PWRB]
Nov 29 00:38:44 Spy kernel: [   18.272428] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Nov 29 00:38:44 Spy kernel: [   18.272486] ACPI: Sleep Button [SLPB]
Nov 29 00:38:44 Spy kernel: [   18.272593] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Nov 29 00:38:44 Spy kernel: [   18.272649] ACPI: Power Button [PWRF]
Nov 29 00:38:44 Spy kernel: [   18.272949] ACPI: acpi_idle registered with cpuidle
Nov 29 00:38:44 Spy kernel: [   18.273074] Marking TSC unstable due to TSC halts in idle
Nov 29 00:38:44 Spy kernel: [   18.273226] Switching to clocksource hpet
Nov 29 00:38:44 Spy kernel: [   18.275813] thermal LNXTHERM:01: registered as thermal_zone0
Nov 29 00:38:44 Spy kernel: [   18.275868] ACPI: Thermal Zone [THRM] (66 C)
Nov 29 00:38:44 Spy kernel: [   18.276020] ERST: Table is not found!
Nov 29 00:38:44 Spy kernel: [   18.276110] isapnp: Scanning for PnP cards...
Nov 29 00:38:44 Spy kernel: [   18.281832] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov 29 00:38:44 Spy kernel: [   18.283384] brd: module loaded
Nov 29 00:38:44 Spy kernel: [   18.283988] loop: module loaded
Nov 29 00:38:44 Spy kernel: [   18.284221] ata_piix 0000:00:1f.1: version 2.13
Nov 29 00:38:44 Spy kernel: [   18.284235]   alloc irq_desc for 19 on node -1
Nov 29 00:38:44 Spy kernel: [   18.284237]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   18.284244] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 29 00:38:44 Spy kernel: [   18.284330] ata_piix 0000:00:1f.1: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.284410] scsi0 : ata_piix
Nov 29 00:38:44 Spy kernel: [   18.284533] scsi1 : ata_piix
Nov 29 00:38:44 Spy kernel: [   18.285186] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
Nov 29 00:38:44 Spy kernel: [   18.285237] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
Nov 29 00:38:44 Spy kernel: [   18.285616] Fixed MDIO Bus: probed
Nov 29 00:38:44 Spy kernel: [   18.285694] PPP generic driver version 2.4.2
Nov 29 00:38:44 Spy kernel: [   18.285776] tun: Universal TUN/TAP device driver, 1.6
Nov 29 00:38:44 Spy kernel: [   18.285823] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 29 00:38:44 Spy kernel: [   18.285952] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 29 00:38:44 Spy kernel: [   18.286018]   alloc irq_desc for 23 on node -1
Nov 29 00:38:44 Spy kernel: [   18.286020]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   18.286025] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 29 00:38:44 Spy kernel: [   18.286084] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.286088] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 29 00:38:44 Spy kernel: [   18.286169] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Nov 29 00:38:44 Spy kernel: [   18.286243] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Nov 29 00:38:44 Spy kernel: [   18.286302] ehci_hcd 0000:00:1d.7: debug port 1
Nov 29 00:38:44 Spy kernel: [   18.290223] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Nov 29 00:38:44 Spy kernel: [   18.290243] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0004000
Nov 29 00:38:44 Spy kernel: [   18.294441] ata2: port disabled. ignoring.
Nov 29 00:38:44 Spy kernel: [   18.301237] ACPI: Battery Slot [BAT0] (battery present)
Nov 29 00:38:44 Spy kernel: [   18.304017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Nov 29 00:38:44 Spy kernel: [   18.304202] hub 1-0:1.0: USB hub found
Nov 29 00:38:44 Spy kernel: [   18.304252] hub 1-0:1.0: 8 ports detected
Nov 29 00:38:44 Spy kernel: [   18.304384] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 29 00:38:44 Spy kernel: [   18.304444] uhci_hcd: USB Universal Host Controller Interface driver
Nov 29 00:38:44 Spy kernel: [   18.304512] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 29 00:38:44 Spy kernel: [   18.304566] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.304570] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 29 00:38:44 Spy kernel: [   18.304654] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Nov 29 00:38:44 Spy kernel: [   18.304734] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
Nov 29 00:38:44 Spy kernel: [   18.304902] hub 2-0:1.0: USB hub found
Nov 29 00:38:44 Spy kernel: [   18.304951] hub 2-0:1.0: 2 ports detected
Nov 29 00:38:44 Spy kernel: [   18.305056] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 29 00:38:44 Spy kernel: [   18.305111] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.305115] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 29 00:38:44 Spy kernel: [   18.305198] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Nov 29 00:38:44 Spy kernel: [   18.305288] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
Nov 29 00:38:44 Spy kernel: [   18.305450] hub 3-0:1.0: USB hub found
Nov 29 00:38:44 Spy kernel: [   18.305498] hub 3-0:1.0: 2 ports detected
Nov 29 00:38:44 Spy kernel: [   18.305601] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 29 00:38:44 Spy kernel: [   18.305655] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.305658] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 29 00:38:44 Spy kernel: [   18.305739] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Nov 29 00:38:44 Spy kernel: [   18.305830] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Nov 29 00:38:44 Spy kernel: [   18.305994] hub 4-0:1.0: USB hub found
Nov 29 00:38:44 Spy kernel: [   18.306042] hub 4-0:1.0: 2 ports detected
Nov 29 00:38:44 Spy kernel: [   18.306148] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Nov 29 00:38:44 Spy kernel: [   18.306202] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.306206] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov 29 00:38:44 Spy kernel: [   18.306287] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Nov 29 00:38:44 Spy kernel: [   18.306378] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
Nov 29 00:38:44 Spy kernel: [   18.306542] hub 5-0:1.0: USB hub found
Nov 29 00:38:44 Spy kernel: [   18.306592] hub 5-0:1.0: 2 ports detected
Nov 29 00:38:44 Spy kernel: [   18.306756] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov 29 00:38:44 Spy kernel: [   18.313056] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov 29 00:38:44 Spy kernel: [   18.314012] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 29 00:38:44 Spy kernel: [   18.314064] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 29 00:38:44 Spy kernel: [   18.314113] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 29 00:38:44 Spy kernel: [   18.314161] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 29 00:38:44 Spy kernel: [   18.314209] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 29 00:38:44 Spy kernel: [   18.314310] mice: PS/2 mouse device common for all mice
Nov 29 00:38:44 Spy kernel: [   18.314540] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Nov 29 00:38:44 Spy kernel: [   18.314621] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Nov 29 00:38:44 Spy kernel: [   18.314774] device-mapper: uevent: version 1.0.3
Nov 29 00:38:44 Spy kernel: [   18.314917] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Nov 29 00:38:44 Spy kernel: [   18.315042] device-mapper: multipath: version 1.1.1 loaded
Nov 29 00:38:44 Spy kernel: [   18.315092] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 29 00:38:44 Spy kernel: [   18.315253] EISA: Probing bus 0 at eisa.0
Nov 29 00:38:44 Spy kernel: [   18.315304] Cannot allocate resource for EISA slot 1
Nov 29 00:38:44 Spy kernel: [   18.315353] Cannot allocate resource for EISA slot 2
Nov 29 00:38:44 Spy kernel: [   18.315401] Cannot allocate resource for EISA slot 3
Nov 29 00:38:44 Spy kernel: [   18.315448] Cannot allocate resource for EISA slot 4
Nov 29 00:38:44 Spy kernel: [   18.315495] Cannot allocate resource for EISA slot 5
Nov 29 00:38:44 Spy kernel: [   18.315554] EISA: Detected 0 cards.
Nov 29 00:38:44 Spy kernel: [   18.315739] cpuidle: using governor ladder
Nov 29 00:38:44 Spy kernel: [   18.315891] cpuidle: using governor menu
Nov 29 00:38:44 Spy kernel: [   18.316266] TCP cubic registered
Nov 29 00:38:44 Spy kernel: [   18.316451] NET: Registered protocol family 10
Nov 29 00:38:44 Spy kernel: [   18.316872] lo: Disabled Privacy Extensions
Nov 29 00:38:44 Spy kernel: [   18.317157] NET: Registered protocol family 17
Nov 29 00:38:44 Spy kernel: [   18.317562] Using IPI No-Shortcut mode
Nov 29 00:38:44 Spy kernel: [   18.317683] PM: Resume from disk failed.
Nov 29 00:38:44 Spy kernel: [   18.317694] registered taskstats version 1
Nov 29 00:38:44 Spy kernel: [   18.318057]   Magic number: 2:787:608
Nov 29 00:38:44 Spy kernel: [   18.318196] rtc_cmos 00:08: setting system clock to 2010-11-29 00:38:29 UTC (1290991109)
Nov 29 00:38:44 Spy kernel: [   18.318254] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 29 00:38:44 Spy kernel: [   18.318301] EDD information not available.
Nov 29 00:38:44 Spy kernel: [   18.351059] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Nov 29 00:38:44 Spy kernel: [   18.457742] ata1.00: ATAPI: _NEC DVD_RW ND-6750A, 2.42, max UDMA/33
Nov 29 00:38:44 Spy kernel: [   18.473332] ata1.00: configured for UDMA/33
Nov 29 00:38:44 Spy kernel: [   18.630297] isapnp: No Plug & Play device found
Nov 29 00:38:44 Spy kernel: [   18.637674] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-6750A  2.42 PQ: 0 ANSI: 5
Nov 29 00:38:44 Spy kernel: [   18.663377] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Nov 29 00:38:44 Spy kernel: [   18.663428] Uniform CD-ROM driver Revision: 3.20
Nov 29 00:38:44 Spy kernel: [   18.663568] sr 0:0:0:0: Attached scsi CD-ROM sr0
Nov 29 00:38:44 Spy kernel: [   18.663619] sr 0:0:0:0: Attached scsi generic sg0 type 5
Nov 29 00:38:44 Spy kernel: [   18.663760] Freeing unused kernel memory: 684k freed
Nov 29 00:38:44 Spy kernel: [   18.664214] Write protecting the kernel text: 4932k
Nov 29 00:38:44 Spy kernel: [   18.664319] Write protecting the kernel read-only data: 1976k
Nov 29 00:38:44 Spy kernel: [   18.680596] udev[81]: starting version 163
Nov 29 00:38:44 Spy kernel: [   18.811287] ahci 0000:00:1f.2: version 3.0
Nov 29 00:38:44 Spy kernel: [   18.811309] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 29 00:38:44 Spy kernel: [   18.811404]   alloc irq_desc for 43 on node -1
Nov 29 00:38:44 Spy kernel: [   18.811407]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   18.811420] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
Nov 29 00:38:44 Spy kernel: [   18.811503] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
Nov 29 00:38:44 Spy kernel: [   18.811563] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
Nov 29 00:38:44 Spy kernel: [   18.811621] ahci 0000:00:1f.2: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   18.822443] sata_via 0000:05:07.0: version 2.6
Nov 29 00:38:44 Spy kernel: [   18.822470] sata_via 0000:05:07.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 29 00:38:44 Spy kernel: [   18.822573] sata_via 0000:05:07.0: routed to hard irq line 7
Nov 29 00:38:44 Spy kernel: [   18.838270] scsi3 : sata_via
Nov 29 00:38:44 Spy kernel: [   18.838453] scsi2 : ahci
Nov 29 00:38:44 Spy kernel: [   18.838637] scsi5 : ahci
Nov 29 00:38:44 Spy kernel: [   18.838801] scsi4 : sata_via
Nov 29 00:38:44 Spy kernel: [   18.838943] scsi7 : sata_via
Nov 29 00:38:44 Spy kernel: [   18.839039] ata7: SATA max UDMA/133 port i16@0x3850 bmdma 0x3800 irq 17
Nov 29 00:38:44 Spy kernel: [   18.839090] ata8: SATA max UDMA/133 port i16@0x3840 bmdma 0x3808 irq 17
Nov 29 00:38:44 Spy kernel: [   18.839140] ata9: PATA max UDMA/133 port i16@0x3830 bmdma 0x3810 irq 17
Nov 29 00:38:44 Spy kernel: [   18.839457] scsi6 : ahci
Nov 29 00:38:44 Spy kernel: [   18.839610] scsi8 : ahci
Nov 29 00:38:44 Spy kernel: [   18.839805] ata3: SATA max UDMA/133 abar m1024@0xb0004400 port 0xb0004500 irq 43
Nov 29 00:38:44 Spy kernel: [   18.840585] ata4: DUMMY
Nov 29 00:38:44 Spy kernel: [   18.840631] ata5: SATA max UDMA/133 abar m1024@0xb0004400 port 0xb0004600 irq 43
Nov 29 00:38:44 Spy kernel: [   18.840687] ata6: DUMMY
Nov 29 00:38:44 Spy kernel: [   18.842830] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 29 00:38:44 Spy kernel: [   18.842902] r8169 0000:05:05.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 29 00:38:44 Spy kernel: [   18.842980] r8169 0000:05:05.0: (unregistered net_device): no PCI Express capability
Nov 29 00:38:44 Spy kernel: [   18.843588] r8169 0000:05:05.0: eth0: RTL8169sb/8110sb at 0xf80d2800, 00:03:0d:4b:7f:85, XID 10000000 IRQ 19
Nov 29 00:38:44 Spy kernel: [   18.992078] usb 2-1: new low speed USB device using uhci_hcd and address 2
Nov 29 00:38:44 Spy kernel: [   19.156130] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov 29 00:38:44 Spy kernel: [   19.161086] ata3: SATA link down (SStatus 0 SControl 300)
Nov 29 00:38:44 Spy kernel: [   19.161155] ata5: SATA link down (SStatus 0 SControl 300)
Nov 29 00:38:44 Spy kernel: [   19.199606] ata7.00: ATA-7: WDC WD1200BEVS-07LAT0, 01.06M01, max UDMA/133
Nov 29 00:38:44 Spy kernel: [   19.199661] ata7.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/1)
Nov 29 00:38:44 Spy kernel: [   19.228763] ata7.00: configured for UDMA/133
Nov 29 00:38:44 Spy kernel: [   19.228984] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-0 01.0 PQ: 0 ANSI: 5
Nov 29 00:38:44 Spy kernel: [   19.229222] sd 3:0:0:0: Attached scsi generic sg1 type 0
Nov 29 00:38:44 Spy kernel: [   19.229290] sd 3:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Nov 29 00:38:44 Spy kernel: [   19.229449] sd 3:0:0:0: [sda] Write Protect is off
Nov 29 00:38:44 Spy kernel: [   19.229498] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 29 00:38:44 Spy kernel: [   19.229523] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 29 00:38:44 Spy kernel: [   19.229733]  sda: sda1 sda2 sda3 < sda5 sda6 >
Nov 29 00:38:44 Spy kernel: [   19.272898] sd 3:0:0:0: [sda] Attached SCSI disk
Nov 29 00:38:44 Spy kernel: [   19.404078] usb 3-2: new full speed USB device using uhci_hcd and address 2
Nov 29 00:38:44 Spy kernel: [   19.605125] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov 29 00:38:44 Spy kernel: [   19.647971] ata8.00: ATA-7: WDC WD1200BEVS-07LAT0, 01.06M01, max UDMA/133
Nov 29 00:38:44 Spy kernel: [   19.648033] ata8.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/1)
Nov 29 00:38:44 Spy kernel: [   19.664749] ata8.00: configured for UDMA/133
Nov 29 00:38:44 Spy kernel: [   19.664954] scsi 4:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-0 01.0 PQ: 0 ANSI: 5
Nov 29 00:38:44 Spy kernel: [   19.665188] sd 4:0:0:0: Attached scsi generic sg2 type 0
Nov 29 00:38:44 Spy kernel: [   19.665203] sd 4:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Nov 29 00:38:44 Spy kernel: [   19.665263] sd 4:0:0:0: [sdb] Write Protect is off
Nov 29 00:38:44 Spy kernel: [   19.665266] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov 29 00:38:44 Spy kernel: [   19.665322] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 29 00:38:44 Spy kernel: [   19.665529]  sdb: sdb1
Nov 29 00:38:44 Spy kernel: [   19.673911] sd 4:0:0:0: [sdb] Attached SCSI disk
Nov 29 00:38:44 Spy kernel: [   19.837309] firewire_ohci 0000:05:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 29 00:38:44 Spy kernel: [   19.841973] usbcore: registered new interface driver hiddev
Nov 29 00:38:44 Spy kernel: [   19.855561] input: Darfon USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5
Nov 29 00:38:44 Spy kernel: [   19.855738] generic-usb 0003:0D62:A100.0001: input,hidraw0: USB HID v1.10 Mouse [Darfon USB Optical Mouse] on usb-0000:00:1d.0-1/input0
Nov 29 00:38:44 Spy kernel: [   19.855826] usbcore: registered new interface driver usbhid
Nov 29 00:38:44 Spy kernel: [   19.855884] usbhid: USB HID core driver
Nov 29 00:38:44 Spy kernel: [   19.893086] firewire_ohci: Added fw-ohci device 0000:05:04.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Nov 29 00:38:44 Spy kernel: [   20.392169] firewire_core: created device fw0: GUID 00030d4972007480, S400
Nov 29 00:38:44 Spy kernel: [   20.635682] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Nov 29 00:38:44 Spy kernel: [   32.279252] udev[399]: starting version 163
Nov 29 00:38:44 Spy kernel: [   32.359545] lp: driver loaded but no devices found
Nov 29 00:38:44 Spy kernel: [   32.374189] Adding 1998844k swap on /dev/sda5.  Priority:-1 extents:1 across:1998844k 
Nov 29 00:38:44 Spy kernel: [   32.408397] intel_rng: FWH not detected
Nov 29 00:38:44 Spy kernel: [   32.454625] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6
Nov 29 00:38:44 Spy kernel: [   32.454724] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov 29 00:38:44 Spy kernel: [   32.514897] leds_ss4200: no LED devices found
Nov 29 00:38:44 Spy kernel: [   32.545733] Linux agpgart interface v0.103
Nov 29 00:38:44 Spy kernel: [   32.654035] Bluetooth: Core ver 2.15
Nov 29 00:38:44 Spy kernel: [   32.654087] NET: Registered protocol family 31
Nov 29 00:38:44 Spy kernel: [   32.654089] Bluetooth: HCI device and connection manager initialized
Nov 29 00:38:44 Spy kernel: [   32.654092] Bluetooth: HCI socket layer initialized
Nov 29 00:38:44 Spy kernel: [   32.663504] Bluetooth: Generic Bluetooth USB driver ver 0.6
Nov 29 00:38:44 Spy kernel: [   32.691421] usbcore: registered new interface driver btusb
Nov 29 00:38:44 Spy kernel: [   32.701612] cfg80211: Calling CRDA to update world regulatory domain
Nov 29 00:38:44 Spy kernel: [   32.742140] cfg80211: World regulatory domain updated:
Nov 29 00:38:44 Spy kernel: [   32.742144]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 29 00:38:44 Spy kernel: [   32.742147]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:38:44 Spy kernel: [   32.742150]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:38:44 Spy kernel: [   32.742153]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:38:44 Spy kernel: [   32.742156]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:38:44 Spy kernel: [   32.742159]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 29 00:38:44 Spy kernel: [   32.743074] [drm] Initialized drm 1.1.0 20060810
Nov 29 00:38:44 Spy kernel: [   32.746724] type=1400 audit(1290991123.926:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=757 comm="apparmor_parser"
Nov 29 00:38:44 Spy kernel: [   32.747335] type=1400 audit(1290991123.926:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=757 comm="apparmor_parser"
Nov 29 00:38:44 Spy kernel: [   32.747672] type=1400 audit(1290991123.926:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=757 comm="apparmor_parser"
Nov 29 00:38:44 Spy kernel: [   32.824293] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Nov 29 00:38:44 Spy kernel: [   32.855538] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Nov 29 00:38:44 Spy kernel: [   32.855542] iwl3945: Copyright(c) 2003-2010 Intel Corporation
Nov 29 00:38:44 Spy kernel: [   32.855622] iwl3945 0000:04:00.0: enabling device (0000 -> 0002)
Nov 29 00:38:44 Spy kernel: [   32.855634] iwl3945 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 29 00:38:44 Spy kernel: [   32.855654] iwl3945 0000:04:00.0: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   32.910516] [drm] radeon kernel modesetting enabled.
Nov 29 00:38:44 Spy kernel: [   32.910593] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 29 00:38:44 Spy kernel: [   32.910599] radeon 0000:01:00.0: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   32.912597] [drm] initializing kernel modesetting (R520 0x1002:0x7102).
Nov 29 00:38:44 Spy kernel: [   32.912688] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Nov 29 00:38:44 Spy kernel: [   32.912692] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
Nov 29 00:38:44 Spy kernel: [   32.912810]   alloc irq_desc for 44 on node -1
Nov 29 00:38:44 Spy kernel: [   32.912813]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   32.912848] iwl3945 0000:04:00.0: irq 44 for MSI/MSI-X
Nov 29 00:38:44 Spy kernel: [   32.929227] [drm] register mmio base: 0xB0100000
Nov 29 00:38:44 Spy kernel: [   32.929230] [drm] register mmio size: 65536
Nov 29 00:38:44 Spy kernel: [   32.929380] ATOM BIOS: Uniwill
Nov 29 00:38:44 Spy kernel: [   32.929411] [drm] Generation 2 PCI interface, using max accessible memory
Nov 29 00:38:44 Spy kernel: [   32.929418] radeon 0000:01:00.0: VRAM: 256M 0x00000000 - 0x0FFFFFFF (256M used)
Nov 29 00:38:44 Spy kernel: [   32.929422] radeon 0000:01:00.0: GTT: 512M 0x10000000 - 0x2FFFFFFF
Nov 29 00:38:44 Spy kernel: [   32.929500] [drm] radeon: irq initialized.
Nov 29 00:38:44 Spy kernel: [   32.930055] [drm] Detected VRAM RAM=256M, BAR=256M
Nov 29 00:38:44 Spy kernel: [   32.930059] [drm] RAM width 256bits DDR
Nov 29 00:38:44 Spy kernel: [   32.930246] [TTM] Zone  kernel: Available graphics memory: 436548 kiB.
Nov 29 00:38:44 Spy kernel: [   32.930248] [TTM] Zone highmem: Available graphics memory: 1029736 kiB.
Nov 29 00:38:44 Spy kernel: [   32.930251] [TTM] Initializing pool allocator.
Nov 29 00:38:44 Spy kernel: [   32.930274] [drm] radeon: 256M of VRAM memory ready
Nov 29 00:38:44 Spy kernel: [   32.930276] [drm] radeon: 512M of GTT memory ready.
Nov 29 00:38:44 Spy kernel: [   32.930301] [drm] GART: num cpu pages 131072, num gpu pages 131072
Nov 29 00:38:44 Spy kernel: [   32.932022] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
Nov 29 00:38:44 Spy kernel: [   32.933352] [drm] PCIE GART of 512M enabled (table at 0x00040000).
Nov 29 00:38:44 Spy kernel: [   32.933478] [drm] Loading R500 Microcode
Nov 29 00:38:44 Spy kernel: [   32.937256] phy0: Selected rate control algorithm 'iwl-3945-rs'
Nov 29 00:38:44 Spy kernel: [   32.955372] [drm] radeon: ring at 0x0000000010000000
Nov 29 00:38:44 Spy kernel: [   32.955399] [drm] ring test succeeded in 3 usecs
Nov 29 00:38:44 Spy kernel: [   32.955579] [drm] radeon: ib pool ready.
Nov 29 00:38:44 Spy kernel: [   32.955658] [drm] ib test succeeded in 0 usecs
Nov 29 00:38:44 Spy kernel: [   32.955703] [drm] Default TV standard: NTSC
Nov 29 00:38:44 Spy kernel: [   32.955708] [drm] Default TV standard: NTSC
Nov 29 00:38:44 Spy kernel: [   32.955837] [drm] Default TV standard: NTSC
Nov 29 00:38:44 Spy kernel: [   32.955867] [drm] Radeon Display Connectors
Nov 29 00:38:44 Spy kernel: [   32.955869] [drm] Connector 0:
Nov 29 00:38:44 Spy kernel: [   32.955871] [drm]   DVI-I
Nov 29 00:38:44 Spy kernel: [   32.955872] [drm]   HPD1
Nov 29 00:38:44 Spy kernel: [   32.955875] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
Nov 29 00:38:44 Spy kernel: [   32.955877] [drm]   Encoders:
Nov 29 00:38:44 Spy kernel: [   32.955879] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Nov 29 00:38:44 Spy kernel: [   32.955881] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
Nov 29 00:38:44 Spy kernel: [   32.955883] [drm] Connector 1:
Nov 29 00:38:44 Spy kernel: [   32.955884] [drm]   LVDS
Nov 29 00:38:44 Spy kernel: [   32.955887] [drm]   DDC: 0x7e30 0x7e30 0x7e34 0x7e34 0x7e38 0x7e38 0x7e3c 0x7e3c
Nov 29 00:38:44 Spy kernel: [   32.955889] [drm]   Encoders:
Nov 29 00:38:44 Spy kernel: [   32.955891] [drm]     LCD1: INTERNAL_LVTM1
Nov 29 00:38:44 Spy kernel: [   32.955893] [drm] Connector 2:
Nov 29 00:38:44 Spy kernel: [   32.955894] [drm]   S-video
Nov 29 00:38:44 Spy kernel: [   32.955896] [drm]   Encoders:
Nov 29 00:38:44 Spy kernel: [   32.955897] [drm]     TV1: INTERNAL_KLDSCP_DAC2
Nov 29 00:38:44 Spy kernel: [   32.964458]   alloc irq_desc for 22 on node -1
Nov 29 00:38:44 Spy kernel: [   32.964462]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   32.964470] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 29 00:38:44 Spy kernel: [   32.964521]   alloc irq_desc for 45 on node -1
Nov 29 00:38:44 Spy kernel: [   32.964523]   alloc kstat_irqs on node -1
Nov 29 00:38:44 Spy kernel: [   32.964536] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Nov 29 00:38:44 Spy kernel: [   32.964573] HDA Intel 0000:00:1b.0: setting latency timer to 64
Nov 29 00:38:44 Spy kernel: [   33.014615] [drm] radeon: power management initialized
Nov 29 00:38:44 Spy kernel: [   33.288002] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa0b1, caps: 0xa04713/0x20040a/0x0
Nov 29 00:38:44 Spy NetworkManager[964]: <info> NetworkManager (version 0.8.1) is starting...
Nov 29 00:38:44 Spy NetworkManager[964]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Nov 29 00:38:44 Spy avahi-daemon[966]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Nov 29 00:38:44 Spy avahi-daemon[966]: Successfully dropped root privileges.
Nov 29 00:38:44 Spy avahi-daemon[966]: avahi-daemon 0.6.27 starting up.
Nov 29 00:38:44 Spy NetworkManager[964]: <info> trying to start the modem manager...
Nov 29 00:38:44 Spy avahi-daemon[966]: Successfully called chroot().
Nov 29 00:38:44 Spy avahi-daemon[966]: Successfully dropped remaining capabilities.
Nov 29 00:38:44 Spy NetworkManager[964]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: init!
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: update_system_hostname
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPluginIfupdown: management mode: unmanaged
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/wlan0, iface: wlan0)
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:05.0/net/eth0, iface: eth0)
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:05.0/net/eth0, iface: eth0): no ifupdown configuration found.
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: end _init.
Nov 29 00:38:44 Spy NetworkManager[964]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 29 00:38:44 Spy modem-manager: ModemManager (version 0.4) starting...
Nov 29 00:38:44 Spy NetworkManager[964]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 29 00:38:44 Spy NetworkManager[964]:    Ifupdown: get unmanaged devices count: 0
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: (143572816) ... get_connections.
Nov 29 00:38:44 Spy NetworkManager[964]:    SCPlugin-Ifupdown: (143572816) ... get_connections (managed=false): return empty list.
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Longcheer
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Nokia
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Option
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Generic
Nov 29 00:38:44 Spy modem-manager: Loaded plugin SimTech
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Ericsson MBM
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Huawei
Nov 29 00:38:44 Spy modem-manager: Loaded plugin AnyData
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Sierra
Nov 29 00:38:44 Spy modem-manager: Loaded plugin MotoC
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Gobi
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Option High-Speed
Nov 29 00:38:44 Spy modem-manager: Loaded plugin ZTE
Nov 29 00:38:44 Spy modem-manager: Loaded plugin Novatel
Nov 29 00:38:44 Spy modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Nov 29 00:38:44 Spy modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Nov 29 00:38:44 Spy modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Nov 29 00:38:44 Spy modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Nov 29 00:38:44 Spy NetworkManager[964]:    Ifupdown: get unmanaged devices count: 0
Nov 29 00:38:44 Spy avahi-daemon[966]: No service file found in /etc/avahi/services.
Nov 29 00:38:44 Spy NetworkManager[964]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
Nov 29 00:38:44 Spy kernel: [   33.319355] type=1400 audit(1290991124.498:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=983 comm="apparmor_parser"
Nov 29 00:38:44 Spy kernel: [   33.319975] type=1400 audit(1290991124.498:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=983 comm="apparmor_parser"
Nov 29 00:38:44 Spy NetworkManager[964]: <info> WiFi enabled by radio killswitch; enabled by state file
Nov 29 00:38:44 Spy NetworkManager[964]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 29 00:38:44 Spy NetworkManager[964]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 29 00:38:44 Spy NetworkManager[964]: <info> Networking is enabled by state file
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): now managed
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): bringing up device.
Nov 29 00:38:44 Spy kernel: [   33.320418] type=1400 audit(1290991124.498:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=983 comm="apparmor_parser"
Nov 29 00:38:44 Spy kernel: [   33.324465] type=1400 audit(1290991124.502:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=984 comm="apparmor_parser"
Nov 29 00:38:44 Spy kernel: [   33.325362] type=1400 audit(1290991124.506:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=982 comm="apparmor_parser"
Nov 29 00:38:44 Spy kernel: [   33.327277] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
Nov 29 00:38:44 Spy kernel: [   33.332819] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Nov 29 00:38:44 Spy kernel: [   33.340570] type=1400 audit(1290991124.518:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=988 comm="apparmor_parser"
Nov 29 00:38:44 Spy kernel: [   33.341444] type=1400 audit(1290991124.522:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=984 comm="apparmor_parser"
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): preparing device.
Nov 29 00:38:44 Spy avahi-daemon[966]: Network interface enumeration completed.
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): deactivating device (reason: 2).
Nov 29 00:38:44 Spy avahi-daemon[966]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 29 00:38:44 Spy avahi-daemon[966]: Server startup complete. Host name is Spy.local. Local service cookie is 723612886.
Nov 29 00:38:44 Spy NetworkManager[964]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (eth0): carrier is OFF
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (eth0): now managed
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (eth0): bringing up device.
Nov 29 00:38:44 Spy kernel: [   33.426446] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (eth0): preparing device.
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (eth0): deactivating device (reason: 2).
Nov 29 00:38:44 Spy NetworkManager[964]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:05.0/net/eth0
Nov 29 00:38:44 Spy kernel: [   33.433602] r8169 0000:05:05.0: eth0: link down
Nov 29 00:38:44 Spy kernel: [   33.433786] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 29 00:38:44 Spy NetworkManager[964]: <info> modem-manager is now available
Nov 29 00:38:44 Spy NetworkManager[964]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov 29 00:38:44 Spy NetworkManager[964]: <info> Trying to start the supplicant...
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): supplicant manager state:  down -> idle
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Nov 29 00:38:44 Spy NetworkManager[964]: <info> (wlan0): supplicant interface state:  starting -> ready
Nov 29 00:38:44 Spy kernel: [   33.481269] [drm] fb mappable at 0xC00C0000
Nov 29 00:38:44 Spy kernel: [   33.481273] [drm] vram apper at 0xC0000000
Nov 29 00:38:44 Spy kernel: [   33.481275] [drm] size 5300224
Nov 29 00:38:44 Spy kernel: [   33.481277] [drm] fb depth is 24
Nov 29 00:38:44 Spy kernel: [   33.481278] [drm]    pitch is 5888
Nov 29 00:38:45 Spy init: Failed to open system console: Input/output error
Nov 29 00:38:45 Spy kernel: [   33.817678] Console: switching to colour frame buffer device 180x56
Nov 29 00:38:45 Spy kernel: [   33.823065] fb0: radeondrmfb frame buffer device
Nov 29 00:38:45 Spy kernel: [   33.823067] drm: registered panic notifier
Nov 29 00:38:45 Spy kernel: [   33.823071] Slow work thread pool: Starting up
Nov 29 00:38:45 Spy kernel: [   33.823140] Slow work thread pool: Ready
Nov 29 00:38:45 Spy kernel: [   33.823147] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
Nov 29 00:38:45 Spy init: apport pre-start process (1060) terminated with status 1
Nov 29 00:38:45 Spy cron[1067]: (CRON) INFO (pidfile fd = 3)
Nov 29 00:38:45 Spy init: apport post-stop process (1082) terminated with status 1
Nov 29 00:38:45 Spy acpid: starting up with proc fs
Nov 29 00:38:45 Spy acpid: 36 rules loaded
Nov 29 00:38:45 Spy acpid: waiting for events: event logging is off
Nov 29 00:38:45 Spy gdm-binary[1094]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 29 00:38:45 Spy anacron[1109]: Anacron 2.3 started on 2010-11-29
Nov 29 00:38:45 Spy cron[1175]: (CRON) STARTUP (fork ok)
Nov 29 00:38:45 Spy cron[1175]: (CRON) INFO (Running @reboot jobs)
Nov 29 00:38:45 Spy kernel: [   33.930845] ppdev: user-space parallel port driver
Nov 29 00:38:45 Spy gdm-binary[1094]: WARNING: Unable to find users: no seat-id found
Nov 29 00:38:45 Spy gdm-simple-slave[1196]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 29 00:38:45 Spy bluetoothd[1212]: Bluetooth deamon 4.69
Nov 29 00:38:45 Spy bluetoothd[1214]: Starting SDP server
Nov 29 00:38:45 Spy bluetoothd[1214]: Starting experimental netlink support
Nov 29 00:38:45 Spy bluetoothd[1214]: Failed to find Bluetooth netlink family
Nov 29 00:38:45 Spy bluetoothd[1214]: Failed to init netlink plugin
Nov 29 00:38:45 Spy kernel: [   34.081322] Bluetooth: L2CAP ver 2.14
Nov 29 00:38:45 Spy kernel: [   34.081325] Bluetooth: L2CAP socket layer initialized
Nov 29 00:38:45 Spy kernel: [   34.088071] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 29 00:38:45 Spy kernel: [   34.088075] Bluetooth: BNEP filters: protocol multicast
Nov 29 00:38:45 Spy bluetoothd[1214]: HCI dev 0 registered
Nov 29 00:38:45 Spy kernel: [   34.093986] Bluetooth: SCO (Voice Link) ver 0.6
Nov 29 00:38:45 Spy kernel: [   34.093988] Bluetooth: SCO socket layer initialized
Nov 29 00:38:45 Spy anacron[1109]: Will run job `cron.daily' in 5 min.
Nov 29 00:38:45 Spy anacron[1109]: Jobs will be executed sequentially
Nov 29 00:38:45 Spy bluetoothd[1214]: HCI dev 0 up
Nov 29 00:38:45 Spy bluetoothd[1214]: Starting security manager 0
Nov 29 00:38:45 Spy acpid: client connected from 1273[0:0]
Nov 29 00:38:45 Spy acpid: 1 client rule loaded
Nov 29 00:38:45 Spy bluetoothd[1214]: ioctl(HCIUNBLOCKADDR): Invalid argument (22)
Nov 29 00:38:45 Spy bluetoothd[1214]: Adapter /org/bluez/1212/hci0 has been enabled
Nov 29 00:38:45 Spy kernel: [   34.350092] Bluetooth: RFCOMM TTY layer initialized
Nov 29 00:38:45 Spy kernel: [   34.350098] Bluetooth: RFCOMM socket layer initialized
Nov 29 00:38:45 Spy kernel: [   34.350101] Bluetooth: RFCOMM ver 1.11
Nov 29 00:38:46 Spy kernel: [   35.266650] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Nov 29 00:38:46 Spy init: plymouth-stop pre-start process (1380) terminated with status 1
Nov 29 00:38:47 Spy gdm-session-worker[1393]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 29 00:38:47 Spy rtkit-daemon[1403]: Successfully called chroot.
Nov 29 00:38:47 Spy rtkit-daemon[1403]: Successfully dropped privileges.
Nov 29 00:38:47 Spy rtkit-daemon[1403]: Successfully limited resources.
Nov 29 00:38:47 Spy rtkit-daemon[1403]: Running.
Nov 29 00:38:47 Spy rtkit-daemon[1403]: Watchdog thread running.
Nov 29 00:38:47 Spy rtkit-daemon[1403]: Canary thread running.
Nov 29 00:38:47 Spy polkitd[1408]: started daemon version 0.96 using authority implementation `local' version `0.96'
Nov 29 00:38:47 Spy rtkit-daemon[1403]: Successfully made thread 1398 of process 1398 (n/a) owned by '113' high priority at nice level -11.
Nov 29 00:38:47 Spy rtkit-daemon[1403]: Supervising 1 threads of 1 processes of 1 users.
Nov 29 00:38:48 Spy gdm-simple-greeter[1391]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Nov 29 00:38:48 Spy rtkit-daemon[1403]: Successfully made thread 1482 of process 1398 (n/a) owned by '113' RT at priority 5.
Nov 29 00:38:48 Spy rtkit-daemon[1403]: Supervising 2 threads of 1 processes of 1 users.
Nov 29 00:38:48 Spy rtkit-daemon[1403]: Successfully made thread 1483 of process 1398 (n/a) owned by '113' RT at priority 5.
Nov 29 00:38:48 Spy rtkit-daemon[1403]: Supervising 3 threads of 1 processes of 1 users.
Nov 29 00:38:48 Spy kernel: [   37.547265] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 152.
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c: snd_pcm_dump():
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c: Soft volume PCM
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c: Control: PCM Playback Volume
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c: min_dB: -51
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c: max_dB: 0
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c: resolution: 256
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c: Its setup is:
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   stream       : CAPTURE
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   access       : MMAP_INTERLEAVED
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   format       : S16_LE
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   subformat    : STD
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   channels     : 2
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   rate         : 44100
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   exact rate   : 44100 (44100/1)
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   msbits       : 16
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   buffer_size  : 88192
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   period_size  : 44096
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   period_time  : 999909
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   tstamp_mode  : ENABLE
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   period_step  : 1
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   avail_min    : 87310
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-util.c:   period_event : 0
Nov 29 00:38:50 Spy pulseaudio[1398]: alsa-utNov 29 00:40:12 Spy kernel: imklog 4.2.0, log source = /proc/kmsg started.

```

---

