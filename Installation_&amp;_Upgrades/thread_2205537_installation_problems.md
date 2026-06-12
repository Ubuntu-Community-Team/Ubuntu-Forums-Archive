---
title: "installation problems"
date: 2014-02-14
forum: Installation &amp; Upgrades
---

### Post by tom53 on 2014-02-14
Dear reader,

I'm trying to install linux for a while, without succes.
I've tried different versions like mint (32 and 64 bit), ubuntu, and xubuntu.
Xubuntu is the latest wich I want to continue with. 

When installing I have to choose the f6 option no acpi=off, otherwise the only thing I get is a black screen..
After that there are no problems within the installing proces, but when I try to restart after the installation I get the following screen:

[http://www.fotosop.nl/afbeelding/?f=59607142817022014-02-14%2016.55.26.jpg](http://www.fotosop.nl/afbeelding/?f=59607142817022014-02-14%2016.55.26.jpg)

Some hardware specs:
[COLOR=#333333][FONT=Verdana]AMD athlon 64 x2 dual core processor 4200+, 3 gb RAM, ATI Radeon HD Pro.[/FONT][/COLOR]

Who can help me with this?

---

### Post by grahammechanical on 2014-02-14
As an experiment, try installing without ticking the box "Install Third Party Software." That will install Ubuntu and its flavours without installing a proprietary video driver. That may get you to a working installation. We can always install a proprietary video driver after installation using the Additional Drivers utility or its equivalent in Xubuntu.

Or you can find Recovery mode in the Grub Advanced Option sub menu. And select Resume. That will load to a desktop without using the proprietary video driver. From there you can experiment with different video drivers using Additional Drivers.

Regards.

---

### Post by tom53 on 2014-02-14
Tried boot things.
Without ticking the box[COLOR=#000000] third party software, xubuntu installed without problems. 
But by trying to boot I get a black screen.

In recovery mode it's not booting also. I get the following screen:
[http://www.fotosop.nl/afbeelding?f=722714281902boot.jpg](http://www.fotosop.nl/afbeelding?f=722714281902boot.jpg)

[/COLOR]

---

### Post by Bashing-om on 2014-02-14
tom53; Hi !

Following grahammechanical's lead and the screen shot; let's say that a graphics driver is not available at this time. So, let's see what we can do to get you to a desktop and at a later time install a graphics driver.
Try this and advise results:
Boot the install, and as soon as the bios screen clears depress and hold the right shiftkey -> grub boot menu ;
The top most entry shoud be highlighted at this time and should be a "non recovery" kernel, hit the 'e' key for edit mode;
Arrow down and across to the terms "quiet splash" and add the term "nomodeset".
Key combo ctl+x to continue the boot process.

Do you now boot to a GUI login ?
Enter you pass word -> Desk top (??) - degraded graphics at this point is OK.

If you can reach this point, we will advise you on steps to take to get you an appropriate graphics driver installed.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by tom53 on 2014-02-14
I added nomodeset as described.
But it's still not booting to a GUI login like before [http://www.fotosop.nl/afbeelding/?f=722714281902boot.jpg](http://www.fotosop.nl/afbeelding/?f=722714281902boot.jpg)

---

### Post by tom53 on 2014-02-14
when I replace the "nomodeset" with "pci=noacpi" it boots succesfully :D
I've searched some on the internet, for permanent solutions.
I'm gonna try to debug as described over here later this weekend: 
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

Will let you know if I succeeded.
Thank you for your replies so far.

---

### Post by Bashing-om on 2014-02-15
tom53; Hello.

It is regretful that I do not have a "better" solution. I am not at all comfortable that you must use "pci=noacpi" in order to boot.
As you now know that option disables several things, and we have to do work-a-rounds. Presently I can not add to what the tutorial encompasses. You will just have to try and see what works.

I do not understand where the problem might lie, as I too run AMD dual core Athlon chips with a ATI graphics card; and I have no problems.

 I will be here to assist in any way that I can.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by tom53 on 2014-02-17
Still got boot problems. If I add pci=noacpi it will boot normally, without I don get a GUI but a grey screen.
I made a logfile:
[http://paste.ubuntu.com/6948743/](http://paste.ubuntu.com/6948743/)

Does anyone have a idea what the problem is?

---

### Post by Bashing-om on 2014-02-17
tom53; My Morning to ya ;

I see no issue with the boot process, all appears good to me.
I have no idea why - with that graphics card, you must use "pci=noacpi" in order to boot. Will require to research the effects of the boot parameter, and what else we "might" have to do to alleviate the situation.
As graphics related: Show us what precisely we are working with; Post the output of terminal codes:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

I will attend to that little mater this afternoon, after I get my outside chores done, and get back to the keyboard.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by tom53 on 2014-02-17
> **Bashing-om said:**
> tom53; My Morning to ya ;

I see no issue with the boot process, all appears good to me.
I have no idea why - with that graphics card, you must use "pci=noacpi" in order to boot. Will require to research the effects of the boot parameter, and what else we "might" have to do to alleviate the situation.
As graphics related: Show us what precisely we are working with; Post the output of terminal codes:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

I will attend to that little mater this afternoon, after I get my outside chores done, and get back to the keyboard.
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


Good morning ;)

I tested without my videocard today(I used the one on the mobo), but there was no difference.

The output of the terminal codes are:
```
 GA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV630 PRO [Radeon HD 2600 PRO] [1002:9589]        Subsystem: Micro-Star International Co., Ltd. Device [1462:0930]
        Kernel driver in use: radeon
        Kernel modules: radeon
 
```
```
  *-display                      description: VGA compatible controller
       product: RV630 PRO [Radeon HD 2600 PRO]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:40 memory:d0000000-dfffffff memory:fdfe0000-fdfeffff ioport:ee00(size=256) memory:fdf00000-fdf1ffff
 
```

Regards.

---

### Post by Bashing-om on 2014-02-17
tom53; Uummm;

Using the ATI graphics card ->[AMD/ATI] RV630 PRO [Radeon HD 2600 PRO] should not be a problem so long as the open source driver "radeon" is used, as ATI no longer supports that card with a proprietary driver. The required driver is loaded.
But just to cover that base, what does the system report ?
Show us the output of:
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]If it ain't one thing
[INDENT][INDENT][/INDENT]it must be another
[/INDENT][/INDENT][/INDENT]

---

### Post by justtryit on 2014-02-17
> **grahammechanical said:**
> Or you can find Recovery mode in the Grub Advanced Option sub menu. And select Resume. That will load to a desktop without using the proprietary video driver. From there you can experiment with different video drivers using Additional Drivers.

Regards.

nOOb just 'driving by', seeking enlightenment:  (Scary - Some of this is actually starting to make a little sense.)  Thanks for the tip, GM!  I had some nVidia proprietary driver issues on installation (black screen).  Seems to be a non-issue now, but if I have to go back there again, the above will doubtless be of help.  Thank you!


[Dual booting Ubuntu 12.04.3 64bit LTS/WinXP-MCE 32bit SP3, on NODUSM3, Athlon64x2 Windsor4200+,  8GB (4 X CM2X2048-6400C5), WD1001FALS]

---

### Post by Bashing-om on 2014-02-17
tom53; Hey ;

Playing catch up with you. Take a look here and try the suggested boot parameters:
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

And let's see where this leads us to.

[INDENT][INDENT]Things are not so bad
[/INDENT][/INDENT]

---

### Post by tom53 on 2014-02-18
> **Bashing-om said:**
> tom53; Uummm;

Using the ATI graphics card ->[AMD/ATI] RV630 PRO [Radeon HD 2600 PRO] should not be a problem so long as the open source driver "radeon" is used, as ATI no longer supports that card with a proprietary driver. The required driver is loaded.
But just to cover that base, what does the system report ?
Show us the output of:
```

cat /var/log/Xorg.0.log


```[INDENT][INDENT]If it ain't one thing[INDENT]it must be another
[/INDENT]
[/INDENT]
[/INDENT]


Here's the log:
```

[    18.067] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    18.067] X Protocol Version 11, Revision 0
[    18.067] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    18.067] Current Operating System: Linux tom-GA-MA69VM-S2 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64
[    18.067] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic root=UUID=8a328ccc-7e29-439e-a9d2-b19af1d9ed52 ro pci=noacpi
[    18.067] Build Date: 16 October 2013  04:41:23PM
[    18.067] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    18.067] Current version of pixman: 0.30.2
[    18.067]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    18.067] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.067] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 18 08:31:11 2014
[    18.083] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.083] (==) No Layout section.  Using the first Screen section.
[    18.083] (==) No screen section available. Using defaults.
[    18.083] (**) |-->Screen "Default Screen Section" (0)
[    18.083] (**) |   |-->Monitor "<default monitor>"
[    18.083] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    18.083] (==) Automatically adding devices
[    18.083] (==) Automatically enabling devices
[    18.083] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.083]    Entry deleted from font path.
[    18.083] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.083]    Entry deleted from font path.
[    18.083] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.083]    Entry deleted from font path.
[    18.083] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.083]    Entry deleted from font path.
[    18.083] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.083]    Entry deleted from font path.
[    18.083] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    18.083]    Entry deleted from font path.
[    18.083] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,                                                                                                                                                                        
        built-ins                                                                                                                                                                                          
[    18.083] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"                                                                       
[    18.083] (II) The server relies on udev to provide the list of input devices.                                                                                                                          
        If no devices become available, reconfigure udev or disable AutoAddDevices.                                                                                                                        
[    18.083] (II) Loader magic: 0x7fb989bacb00                                                                                                                                                             
[    18.083] (II) Module ABI versions:                                                                                                                                                                     
[    18.083]    X.Org ANSI C Emulation: 0.4                                                                                                                                                                
[    18.083]    X.Org Video Driver: 11.0                                                                                                                                                                   
[    18.083]    X.Org XInput driver : 16.0                                                                                                                                                                 
[    18.083]    X.Org Server Extension : 6.0                                                                                                                                                               
[    18.084] (--) PCI:*(0:1:0:0) 1002:9589:1462:0930 rev 0, Mem @ 0xd0000000/268435456, 0xfdfe0000/65536, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072                                                   
[    18.085] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.085] (II) LoadModule: "extmod"
[    18.086] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.087] (II) Module extmod: vendor="X.Org Foundation"
[    18.087]    compiled for 1.11.3, module version = 1.0.0
[    18.087]    Module class: X.Org Server Extension
[    18.087]    ABI class: X.Org Server Extension, version 6.0
[    18.087] (II) Loading extension MIT-SCREEN-SAVER
[    18.087] (II) Loading extension XFree86-VidModeExtension
[    18.087] (II) Loading extension XFree86-DGA
[    18.087] (II) Loading extension DPMS
[    18.087] (II) Loading extension XVideo
[    18.087] (II) Loading extension XVideo-MotionCompensation
[    18.087] (II) Loading extension X-Resource
[    18.087] (II) LoadModule: "dbe"
[    18.087] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.087] (II) Module dbe: vendor="X.Org Foundation"
[    18.087]    compiled for 1.11.3, module version = 1.0.0
[    18.087]    Module class: X.Org Server Extension
[    18.087]    ABI class: X.Org Server Extension, version 6.0
[    18.087] (II) Loading extension DOUBLE-BUFFER
[    18.087] (II) LoadModule: "glx"
[    18.088] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.088] (II) Module glx: vendor="X.Org Foundation"
[    18.088]    compiled for 1.11.3, module version = 1.0.0
[    18.088]    ABI class: X.Org Server Extension, version 6.0
[    18.088] (==) AIGLX enabled
[    18.088] (II) Loading extension GLX
[    18.088] (II) LoadModule: "record"
[    18.088] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.088] (II) Module record: vendor="X.Org Foundation"
[    18.088]    compiled for 1.11.3, module version = 1.13.0
[    18.088]    Module class: X.Org Server Extension
[    18.088]    ABI class: X.Org Server Extension, version 6.0
[    18.088] (II) Loading extension RECORD
[    18.088] (II) LoadModule: "dri"
[    18.089] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.089] (II) Module dri: vendor="X.Org Foundation"
[    18.089]    compiled for 1.11.3, module version = 1.0.0
[    18.089]    ABI class: X.Org Server Extension, version 6.0
[    18.089] (II) Loading extension XFree86-DRI
[    18.089] (II) LoadModule: "dri2"
[    18.089] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.089] (II) Module dri2: vendor="X.Org Foundation"
[    18.089]    compiled for 1.11.3, module version = 1.2.0
[    18.089]    ABI class: X.Org Server Extension, version 6.0
[    18.089] (II) Loading extension DRI2
[    18.090] (==) Matched fglrx as autoconfigured driver 0
[    18.090] (==) Matched ati as autoconfigured driver 1
[    18.090] (==) Matched vesa as autoconfigured driver 2
[    18.090] (==) Matched fbdev as autoconfigured driver 3
[    18.090] (==) Assigned the driver to the xf86ConfigLayout
[    18.090] (II) LoadModule: "fglrx"
[    18.090] (WW) Warning, couldn't open module fglrx
[    18.090] (II) UnloadModule: "fglrx"
[    18.090] (II) Unloading fglrx
[    18.090] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    18.090] (II) LoadModule: "ati"
[    18.090] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.091] (II) Module ati: vendor="X.Org Foundation"
[    18.091]    compiled for 1.11.3, module version = 6.14.99
[    18.091]    Module class: X.Org Video Driver
[    18.091]    ABI class: X.Org Video Driver, version 11.0
[    18.091] (II) LoadModule: "radeon"
[    18.091] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.091] (II) Module radeon: vendor="X.Org Foundation"
[    18.091]    compiled for 1.11.3, module version = 6.14.99
[    18.091]    Module class: X.Org Video Driver
[    18.091]    ABI class: X.Org Video Driver, version 11.0
[    18.091] (II) LoadModule: "vesa"
[    18.092] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.092] (II) Module vesa: vendor="X.Org Foundation"
[    18.092]    compiled for 1.11.3, module version = 2.3.0
[    18.092]    Module class: X.Org Video Driver
[    18.092]    ABI class: X.Org Video Driver, version 11.0
[    18.092] (II) LoadModule: "fbdev"
[    18.092] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.093] (II) Module fbdev: vendor="X.Org Foundation"
[    18.093]    compiled for 1.11.3, module version = 0.4.2
[    18.093]    ABI class: X.Org Video Driver, version 11.0
[    18.093] (==) Matched fglrx as autoconfigured driver 0
[    18.093] (==) Matched ati as autoconfigured driver 1
[    18.093] (==) Matched vesa as autoconfigured driver 2
[    18.093] (==) Matched fbdev as autoconfigured driver 3
[    18.093] (==) Assigned the driver to the xf86ConfigLayout
[    18.093] (II) LoadModule: "fglrx"
[    18.093] (WW) Warning, couldn't open module fglrx
[    18.093] (II) UnloadModule: "fglrx"
[    18.093] (II) Unloading fglrx
[    18.093] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    18.093] (II) LoadModule: "ati"
[    18.094] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.094] (II) Module ati: vendor="X.Org Foundation"
[    18.094]    compiled for 1.11.3, module version = 6.14.99
[    18.094]    Module class: X.Org Video Driver
[    18.094]    ABI class: X.Org Video Driver, version 11.0
[    18.094] (II) LoadModule: "vesa"
[    18.094] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.094] (II) Module vesa: vendor="X.Org Foundation"
[    18.094]    compiled for 1.11.3, module version = 2.3.0
[    18.094]    Module class: X.Org Video Driver
[    18.094]    ABI class: X.Org Video Driver, version 11.0
[    18.094] (II) UnloadModule: "vesa"
[    18.094] (II) Unloading vesa
[    18.094] (II) Failed to load module "vesa" (already loaded, 0)
[    18.094] (II) LoadModule: "fbdev"
[    18.094] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.094] (II) Module fbdev: vendor="X.Org Foundation"
[    18.094]    compiled for 1.11.3, module version = 0.4.2
[    18.094]    ABI class: X.Org Video Driver, version 11.0
[    18.094] (II) UnloadModule: "fbdev"
[    18.094] (II) Unloading fbdev
[    18.094] (II) Failed to load module "fbdev" (already loaded, 0)
[    18.094] (II) RADEON: Driver for ATI Radeon chipsets:
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
        ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
        ATI Radeon IGP330M/340M/350M (U2) 4337,
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
        ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
        ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
        ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
        ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
        ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
        ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
        SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
        ATI Radeon 4100, ATI Mobility Radeon HD 4200,
        ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
        AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
        AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
        AMD Radeon HD 6300 Series Graphics,
        AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
        AMD Firestream 9350, ATI Radeon HD 5800 Series,
        ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
        ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
        ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
        ATI Mobility Radeon HD 5800 Series,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
        ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
        ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
        ATI Mobility Radeon HD 5000 Series,
        ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
        ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
        ATI Mobility Radeon HD 5000 Series,
        ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
        ATI Mobility Radeon Graphics, CEDAR,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
        ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
        CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
        AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
        CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
        BARTS, BARTS, Mobility Radeon HD 6000 Series,
        Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
        AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
        AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
        CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[    18.100] (II) VESA: driver for VESA chipsets: vesa
[    18.100] (II) FBDEV: driver for framebuffer: fbdev
[    18.100] (++) using VT number 7


[    18.100] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.100] (II) [KMS] Kernel modesetting enabled.
[    18.100] (WW) Falling back to old probe method for vesa
[    18.100] (WW) Falling back to old probe method for fbdev
[    18.100] (II) Loading sub module "fbdevhw"
[    18.100] (II) LoadModule: "fbdevhw"
[    18.100] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.101] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.101]    compiled for 1.11.3, module version = 0.0.2
[    18.101]    ABI class: X.Org Video Driver, version 11.0
[    18.101] (II) RADEON(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    18.101] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    18.101] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    18.101] (==) RADEON(0): Default visual is TrueColor
[    18.101] (==) RADEON(0): RGB weight 888
[    18.101] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    18.101] (--) RADEON(0): Chipset: "ATI Radeon HD 2600 Pro" (ChipID = 0x9589)
[    18.101] (II) RADEON(0): PCIE card detected
[    18.101] drmOpenDevice: node name is /dev/dri/card0
[    18.101] drmOpenDevice: open result is 9, (OK)
[    18.101] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    18.101] drmOpenDevice: node name is /dev/dri/card0
[    18.101] drmOpenDevice: open result is 9, (OK)
[    18.101] drmOpenByBusid: drmOpenMinor returns 9
[    18.101] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    18.101] (II) Loading sub module "exa"
[    18.101] (II) LoadModule: "exa"
[    18.101] (II) Loading /usr/lib/xorg/modules/libexa.so
[    18.102] (II) Module exa: vendor="X.Org Foundation"
[    18.102]    compiled for 1.11.3, module version = 2.5.0
[    18.102]    ABI class: X.Org Video Driver, version 11.0
[    18.102] (II) RADEON(0): KMS Color Tiling: enabled
[    18.102] (II) RADEON(0): KMS Pageflipping: enabled
[    18.102] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    18.128] (II) RADEON(0): Output DVI-0 has no monitor section
[    18.152] (II) RADEON(0): Output DIN has no monitor section
[    18.211] (II) RADEON(0): Output DVI-1 has no monitor section
[    18.236] (II) RADEON(0): EDID for output DVI-0
[    18.260] (II) RADEON(0): EDID for output DIN
[    18.318] (II) RADEON(0): EDID for output DVI-1
[    18.318] (II) RADEON(0): Manufacturer: ACR  Model: ad80  Serial#: 1902131713
[    18.318] (II) RADEON(0): Year: 2007  Week: 16
[    18.318] (II) RADEON(0): EDID Version: 1.3
[    18.318] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    18.318] (II) RADEON(0): Sync:  Separate
[    18.318] (II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[    18.318] (II) RADEON(0): Gamma: 2.20
[    18.318] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    18.318] (II) RADEON(0): First detailed timing not preferred mode in violation of standard!
[    18.318] (II) RADEON(0): redX: 0.650 redY: 0.345   greenX: 0.287 greenY: 0.600
[    18.318] (II) RADEON(0): blueX: 0.140 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
[    18.318] (II) RADEON(0): Supported established timings:
[    18.318] (II) RADEON(0): 720x400@70Hz
[    18.318] (II) RADEON(0): 640x480@60Hz
[    18.318] (II) RADEON(0): 640x480@67Hz
[    18.318] (II) RADEON(0): 640x480@72Hz
[    18.318] (II) RADEON(0): 640x480@75Hz
[    18.318] (II) RADEON(0): 800x600@56Hz
[    18.318] (II) RADEON(0): 800x600@60Hz
[    18.318] (II) RADEON(0): 800x600@72Hz
[    18.318] (II) RADEON(0): 800x600@75Hz
[    18.318] (II) RADEON(0): 832x624@75Hz
[    18.318] (II) RADEON(0): 1024x768@60Hz
[    18.318] (II) RADEON(0): 1024x768@70Hz
[    18.318] (II) RADEON(0): 1024x768@75Hz
[    18.318] (II) RADEON(0): 1280x1024@75Hz
[    18.318] (II) RADEON(0): 1152x864@75Hz
[    18.318] (II) RADEON(0): Manufacturer's mask: 0
[    18.318] (II) RADEON(0): Supported standard timings:
[    18.318] (II) RADEON(0): #0: hsize: 1400  vsize 1050  refresh: 75  vid: 20368
[    18.318] (II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    18.318] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    18.318] (II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    18.318] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 75  vid: 3969
[    18.318] (II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    18.318] (II) RADEON(0): #6: hsize: 1152  vsize 921  refresh: 76  vid: 36977
[    18.318] (II) RADEON(0): #7: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    18.318] (II) RADEON(0): Supported detailed timing:
[    18.318] (II) RADEON(0): clock: 89.0 MHz   Image Size:  410 x 257 mm
[    18.318] (II) RADEON(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
[    18.318] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    18.318] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 84 kHz, PixClock max 145 MHz
[    18.318] (II) RADEON(0): Serial No: L800C0014020
[    18.318] (II) RADEON(0): Monitor name: AL1916W
[    18.318] (II) RADEON(0): EDID (in hex):
[    18.318] (II) RADEON(0):    00ffffffffffff00047280ad013a6071
[    18.318] (II) RADEON(0):    1011010308291a78e89ae5a658499923
[    18.318] (II) RADEON(0):    115054bfef80904f950f81808140810f
[    18.318] (II) RADEON(0):    81007190714fc422a0a050841a303020
[    18.318] (II) RADEON(0):    36009a011100001e000000fd00384c1f
[    18.318] (II) RADEON(0):    540e000a202020202020000000ff004c
[    18.318] (II) RADEON(0):    38303043303031343032300a000000fc
[    18.318] (II) RADEON(0):    00414c31393136570a202020202000c9
[    18.318] (II) RADEON(0): Not using mode "1400x1050" (bad mode clock/interlace/doublescan)
[    18.318] (II) RADEON(0): Printing probed modes for output DVI-1
[    18.318] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.318] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.318] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    18.318] (II) RADEON(0): Modeline "1440x900"x60.1   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz)
[    18.318] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.318] (II) RADEON(0): Modeline "1152x921"x76.0  113.52  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz)
[    18.318] (II) RADEON(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
[    18.318] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[    18.318] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.318] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    18.318] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.318] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.318] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.318] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.318] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.319] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.319] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.319] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    18.319] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.319] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    18.319] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.319] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.319] (II) RADEON(0): Output DVI-0 disconnected
[    18.319] (II) RADEON(0): Output DIN disconnected
[    18.319] (II) RADEON(0): Output DVI-1 connected
[    18.319] (II) RADEON(0): Using exact sizes for initial modes
[    18.319] (II) RADEON(0): Output DVI-1 using initial mode 1440x900
[    18.319] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.319] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fa14000
[    18.319] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    18.319] (==) RADEON(0): DPI set to (96, 96)
[    18.319] (II) Loading sub module "fb"
[    18.319] (II) LoadModule: "fb"
[    18.319] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.319] (II) Module fb: vendor="X.Org Foundation"
[    18.319]    compiled for 1.11.3, module version = 1.0.0
[    18.319]    ABI class: X.Org ANSI C Emulation, version 0.4
[    18.319] (II) Loading sub module "ramdac"
[    18.319] (II) LoadModule: "ramdac"
[    18.319] (II) Module "ramdac" already built-in
[    18.319] (II) UnloadModule: "vesa"
[    18.319] (II) Unloading vesa
[    18.319] (II) UnloadModule: "fbdev"
[    18.319] (II) Unloading fbdev
[    18.319] (II) UnloadModule: "fbdevhw"
[    18.319] (II) Unloading fbdevhw
[    18.319] (--) Depth 24 pixmap format is 32 bpp
[    18.319] (II) RADEON(0): [DRI2] Setup complete
[    18.319] (II) RADEON(0): [DRI2]   DRI driver: r600
[    18.319] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    18.320] (II) RADEON(0): Front buffer size: 5200K
[    18.320] (II) RADEON(0): VRAM usage limit set to 225792K
[    18.320] (==) RADEON(0): Backing store disabled
[    18.320] (II) RADEON(0): Direct rendering enabled
[    18.320] (II) RADEON(0): Setting EXA maxPitchBytes
[    18.320] (II) EXA(0): Driver allocated offscreen pixmaps
[    18.320] (II) EXA(0): Driver registered support for the following operations:
[    18.320] (II)         Solid
[    18.320] (II)         Copy
[    18.320] (II)         Composite (RENDER acceleration)
[    18.320] (II)         UploadToScreen
[    18.320] (II)         DownloadFromScreen
[    18.320] (II) RADEON(0): Acceleration enabled
[    18.320] (==) RADEON(0): DPMS enabled
[    18.320] (==) RADEON(0): Silken mouse enabled
[    18.320] (II) RADEON(0): Set up textured video
[    18.320] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    18.320] (II) RADEON(0): [XvMC] Extension initialized.
[    18.320] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.320] (--) RandR disabled
[    18.320] (II) Initializing built-in extension Generic Event Extension
[    18.320] (II) Initializing built-in extension SHAPE
[    18.320] (II) Initializing built-in extension MIT-SHM
[    18.320] (II) Initializing built-in extension XInputExtension
[    18.320] (II) Initializing built-in extension XTEST
[    18.320] (II) Initializing built-in extension BIG-REQUESTS
[    18.320] (II) Initializing built-in extension SYNC
[    18.320] (II) Initializing built-in extension XKEYBOARD
[    18.320] (II) Initializing built-in extension XC-MISC
[    18.320] (II) Initializing built-in extension SECURITY
[    18.320] (II) Initializing built-in extension XINERAMA
[    18.320] (II) Initializing built-in extension XFIXES
[    18.320] (II) Initializing built-in extension RENDER
[    18.320] (II) Initializing built-in extension RANDR
[    18.320] (II) Initializing built-in extension COMPOSITE
[    18.320] (II) Initializing built-in extension DAMAGE
[    18.679] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.679] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.679] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.679] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.679] (II) AIGLX: Loaded and initialized r600
[    18.679] (II) GLX: Initialized DRI2 GL provider for screen 0
[    19.100] (II) RADEON(0): Setting screen physical size to 381 x 238
[    19.110] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.114] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.114] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.114] (II) LoadModule: "evdev"
[    19.115] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.115] (II) Module evdev: vendor="X.Org Foundation"
[    19.115]    compiled for 1.11.3, module version = 2.7.0
[    19.115]    Module class: X.Org XInput Driver
[    19.115]    ABI class: X.Org XInput driver, version 16.0
[    19.115] (II) Using input driver 'evdev' for 'Power Button'
[    19.115] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.115] (**) Power Button: always reports core events
[    19.115] (**) evdev: Power Button: Device: "/dev/input/event1"
[    19.115] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.115] (--) evdev: Power Button: Found keys
[    19.115] (II) evdev: Power Button: Configuring as keyboard
[    19.115] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.115] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.115] (**) Option "xkb_rules" "evdev"
[    19.115] (**) Option "xkb_model" "pc105"
[    19.115] (**) Option "xkb_layout" "us"
[    19.115] (**) Option "xkb_variant" "intl"
[    19.118] (II) XKB: reuse xkmfile /var/lib/xkb/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[    19.119] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.119] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.119] (II) Using input driver 'evdev' for 'Power Button'
[    19.119] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.119] (**) Power Button: always reports core events
[    19.119] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.119] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.119] (--) evdev: Power Button: Found keys
[    19.119] (II) evdev: Power Button: Configuring as keyboard
[    19.119] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    19.119] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    19.119] (**) Option "xkb_rules" "evdev"
[    19.119] (**) Option "xkb_model" "pc105"
[    19.119] (**) Option "xkb_layout" "us"
[    19.119] (**) Option "xkb_variant" "intl"
[    19.120] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event12)
[    19.120] (II) No input driver specified, ignoring this device.
[    19.120] (II) This device may have been added with another device file.
[    19.120] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event3)
[    19.120] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    19.120] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    19.120] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.120] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    19.120] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
[    19.120] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc03e
[    19.120] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[    19.120] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    19.120] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[    19.120] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    19.120] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    19.120] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    19.120] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    19.120] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.120] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input3/event3"
[    19.121] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 8)
[    19.121] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    19.121] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    19.121] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    19.121] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    19.121] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    19.121] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    19.121] (II) No input driver specified, ignoring this device.
[    19.121] (II) This device may have been added with another device file.
[    19.122] (II) config/udev: Adding input device HDA ATI SB Line-Out Surround (/dev/input/event10)
[    19.122] (II) No input driver specified, ignoring this device.
[    19.122] (II) This device may have been added with another device file.
[    19.122] (II) config/udev: Adding input device HDA ATI SB Line-Out Front (/dev/input/event11)
[    19.122] (II) No input driver specified, ignoring this device.
[    19.122] (II) This device may have been added with another device file.
[    19.122] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event4)
[    19.122] (II) No input driver specified, ignoring this device.
[    19.122] (II) This device may have been added with another device file.
[    19.123] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event5)
[    19.123] (II) No input driver specified, ignoring this device.
[    19.123] (II) This device may have been added with another device file.
[    19.123] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event6)
[    19.123] (II) No input driver specified, ignoring this device.
[    19.123] (II) This device may have been added with another device file.
[    19.123] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event7)
[    19.123] (II) No input driver specified, ignoring this device.
[    19.123] (II) This device may have been added with another device file.
[    19.123] (II) config/udev: Adding input device HDA ATI SB Line-Out Side (/dev/input/event8)
[    19.124] (II) No input driver specified, ignoring this device.
[    19.124] (II) This device may have been added with another device file.
[    19.124] (II) config/udev: Adding input device HDA ATI SB Line-Out CLFE (/dev/input/event9)
[    19.124] (II) No input driver specified, ignoring this device.
[    19.124] (II) This device may have been added with another device file.
[    19.124] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    19.124] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.124] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.124] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.124] (**) AT Translated Set 2 keyboard: always reports core events
[    19.124] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    19.124] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    19.124] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    19.124] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    19.124] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    19.124] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    19.125] (**) Option "xkb_rules" "evdev"
[    19.125] (**) Option "xkb_model" "pc105"
[    19.125] (**) Option "xkb_layout" "us"
[    19.125] (**) Option "xkb_variant" "intl"
[    23.818] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    23.818] (II) RADEON(0): Using EDID range info for horizontal sync
[    23.818] (II) RADEON(0): Using EDID range info for vertical refresh
[    23.818] (II) RADEON(0): Printing DDC gathered Modelines:
[    23.818] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz)
[    23.818] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.818] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.818] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.818] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    23.818] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    23.818] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.818] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.818] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    23.818] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.818] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    23.818] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.818] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.818] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.818] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    23.818] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.818] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz)
[    23.818] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    23.818] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.818] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    23.818] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
[    23.818] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    23.818] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz)
[    38.118] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    38.118] (II) RADEON(0): Using hsync ranges from config file
[    38.118] (II) RADEON(0): Using vrefresh ranges from config file
[    38.118] (II) RADEON(0): Printing DDC gathered Modelines:
[    38.118] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz)
[    38.118] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    38.118] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    38.118] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    38.118] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    38.118] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    38.118] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    38.118] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    38.118] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    38.118] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    38.118] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    38.118] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    38.118] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    38.118] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    38.118] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    38.118] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    38.118] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz)
[    38.118] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    38.118] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    38.118] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    38.118] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
[    38.118] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    38.118] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73. kHz)

```

---

### Post by tom53 on 2014-02-18
> **Bashing-om said:**
> tom53; Hey ;

Playing catch up with you. Take a look here and try the suggested boot parameters:
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

And let's see where this leads us to.[INDENT][INDENT]Things are not so bad
[/INDENT]
[/INDENT]


Bios-update didn't succeed, it doesn recognize the files on my usb, so it's still f8 instead of f9. Could that be a problem?

boot parameters:
acpi=ht > no boot
pci=noacpi >succesfull booth
acpi=noirq > no boot (ends with freeing initrd memory)
pnpacou=off > no boot(ends with freeing initrd memory
noapic > no boot(ends with freeing initrd memory
nolapic > no boot

What are the risks when i stay booting with pci=noacpi? is it dangerous?

Regards.

---

### Post by Bashing-om on 2014-02-18
tom53; Disappointed ;

Running with "pci=noacpi" is not directly a bad thing. Just that many "features" are not available. Maybe like temperature controls and fan speed (??).
Getting BIOS updated might be a good thing in this case - normally I advise if it ain't broke do not fix it, but I have resolved several situations by updating BIOS. - There are those times when updating BIOS causes more problems than it fixes !

This from the Xorg.0.log file:
> 
First detailed timing not preferred mode in violation of standard!
Not using mode "1400x1050" (bad mode clock/interlace/doublescan)
Printing probed modes for output DVI-1
Output DVI-1 connected

Unknown at this time if that violation is in respect to the boot parameter, Changing the output port for the monitor to DVI-0 might be of great benefit. To where the system is looking first.

In the meantime, I will keep searching for a better alternative.

[INDENT][INDENT]not happy ->
[INDENT][INDENT][INDENT]do something about it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tom53 on 2014-02-19
> **Bashing-om said:**
> tom53; Disappointed ;

Running with "pci=noacpi" is not directly a bad thing. Just that many "features" are not available. Maybe like temperature controls and fan speed (??).
Getting BIOS updated might be a good thing in this case - normally I advise if it ain't broke do not fix it, but I have resolved several situations by updating BIOS. - There are those times when updating BIOS causes more problems than it fixes !

This from the Xorg.0.log file:

Unknown at this time if that violation is in respect to the boot parameter, Changing the output port for the monitor to DVI-0 might be of great benefit. To where the system is looking first.

In the meantime, I will keep searching for a better alternative.
[INDENT][INDENT]not happy ->[INDENT][INDENT][INDENT]do something about it
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I'm new to linux. How do I change the output port for the monitor? Could't find it with google :P.

---

### Post by Bashing-om on 2014-02-19
tom53; Hey,

Hang'n with you.
In respect to DVI-1, I had expected there to be an alternate connection on the graphics card to swap the physical monitor cable to (DVI-0). I would think DVI-0 exist and is the primary output to be used for a single monitor.

Still looking for a better solution than the coverall "pci=noacpi" . But you can bet it will be BIOS related.


Edit:
> 
acpi=off
This disables ACPI completely. 
Note: this may not work with all computers and will disable a lot of useful (or even needed) features. In some cases it may even disable some crucial features, like.. fans. Be careful with this option, it might cause your machine to overheat if the fans no longer turn. Think of this as a last resort. Also note some machines require acpi=ht instead.



[INDENT]where there is a will there is a way[/INDENT]

---

### Post by tom53 on 2014-02-20
> **Bashing-om said:**
> tom53; Hey,

Hang'n with you.
In respect to DVI-1, I had expected there to be an alternate connection on the graphics card to swap the physical monitor cable to (DVI-0). I would think DVI-0 exist and is the primary output to be used for a single monitor.

Still looking for a better solution than the coverall "pci=noacpi" . But you can bet it will be BIOS related.


Edit:


[INDENT]where there is a will there is a way[/INDENT]



Thanks for staying hanging in ;)
I will try to fix a floppy disk to update my bios next week

.

---

### Post by Bashing-om on 2014-02-20
tom53; Hey:

I keep looking into this, and most of what I find is an advisement to update BIOS prior to doing anything else.

This does have my interest.
[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by tom53 on 2014-06-07
Hello all,

I updated my BIOS, but the screen still appears :(
So i'm still booting with the pci=noacpi mode.

---

