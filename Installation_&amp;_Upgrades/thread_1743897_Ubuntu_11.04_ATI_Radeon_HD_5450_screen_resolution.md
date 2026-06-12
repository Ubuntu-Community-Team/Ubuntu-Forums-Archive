---
title: "Ubuntu 11.04 ATI Radeon HD 5450 screen resolution"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by johnwate on 2011-04-29
Hello, I'm new to the forum.

After upgrading to 11.04 from 10.10, the native resolution of my 24-inch screen (1920x1080) was no longer available. The highest resolution I'm able to get is 1600x1200.

I'm running Natty 11.04 on my desktop.

My graphics card is ATI Radeon HD 5450. I've enabled the "ATI/AMD proprietary FGLRX graphics driver" in "Additional Drivers". But I still cannot get the native 1920x1080 resolution on my screen.

Any help is appreciated.

---

### Post by Devi 710 on 2011-04-29
Can you change the resolution in ATI settings manager? I believe it is called the "Catalyst Centre" or something like that. You should be able to make the change there, no?

---

### Post by johnwate on 2011-04-29
No. In "Catalyst Control Center" the resolution drop box does not show 1920x1080 as an option. The biggest resolution in the drop box is 1600x1200.

---

### Post by johnwate on 2011-04-29
I'm posting some more information for diagnosis.

This is the output of **xrandr**
```

Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+   60.0* 
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0  
   640x480        59.9  

```
If I'm interpreting the output correctly, my Samsung LCD screen is being detected as CRT. Why is that?

---

### Post by jkgodzvision on 2011-05-03
I'm also having the same problem, except my video card is low-end nvidia & max res is 1300x768. Strange. Hope there is a solution very soon! :(

---

### Post by johnwate on 2011-05-07
Today I had the motherboard replaced as part of [Intel's Cougar Point chip recall]("http://www.huffingtonpost.com/2011/01/31/intel-chip-design-flaw_n_816408.html"). And when I restarted my computer the native 1920x1080 resolution suddenly became available. This is a bit strange, as I don't know what could have fixed the resolution problem.

---

### Post by MAFoElffen on 2011-05-07
> **johnwate said:**
> I'm posting some more information for diagnosis.

This is the output of **xrandr**
```

Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+   60.0* 
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0  
   640x480        59.9  

```If I'm interpreting the output correctly, my Samsung LCD screen is being detected as CRT. Why is that?
What does 
```

sudo hwinfo --framebuffer

``` report back?
Try installing startup-manager
```

sudo apt-get install startup-manager

```and see if the resolution shows in there.  Is so, set it with that.  It will set the res through the grub files, where it will use KMS to pass it to Xorg...  

If it doesn't show there, Ill tell you which 2 files to change.

Have had about a dozen people with this problem in the last week, where that fixed them up.

---

### Post by ccompagnon on 2011-05-08
Hello, I've exactly the same problem, monitor is detected as CRT and no 1680x1080 mode available in catalyst.


this is the "hwinfo --framebuffer" output :

> hal.1: read hal dataprocess 5858: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.MjHvaYDEPm4
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  REDWOOD"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "REDWOOD"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0319: 1280x1024 (+2560), 15 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x960 (+1280), 8 bits
  Mode 0x0365: 1280x960 (+2560), 16 bits
  Mode 0x0366: 1280x960 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Mode 0x0373: 1600x1200 (+1600), 8 bits
  Mode 0x0375: 1600x1200 (+3200), 16 bits
  Mode 0x0376: 1600x1200 (+6400), 24 bits
  Mode 0x0383: 1792x1344 (+1792), 8 bits
  Mode 0x0385: 1792x1344 (+3584), 16 bits
  Mode 0x0386: 1792x1344 (+7168), 24 bits
  Mode 0x03d3: 1856x1392 (+1856), 8 bits
  Mode 0x03d5: 1856x1392 (+3712), 16 bits
  Mode 0x03d6: 1856x1392 (+7424), 24 bits
  Mode 0x03e3: 1920x1440 (+1920), 8 bits
  Mode 0x03e5: 1920x1440 (+3840), 16 bits
  Mode 0x03e6: 1920x1440 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
root@PaliAike:/var/log#

---

### Post by EricUtah on 2011-05-08
I also have this same problem with my Radeon.  Going to "monitors" shows unknown monitor, max resolution 1024x768.  Hitting "detect monitor" doesn't seem to trigger any response.  Xrandr shows max 1024x768 while hwinfo --framebuffer shows max resolution of 1280x1024.  I believe the mode it *should* be running at is 1376 x 768.

xrandr:
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  

hwinfo --framebuffer
> hal.1: read hal dataprocess 13286: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.TIM8629z9tC
  Hardware Class: framebuffer
  Model: "ATI V380"
<snip>
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+3072), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0319: 1280x1024 (+2560), 15 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+3840), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown


I manually tried to edit monitors.xml and that unfortunately triggered Unity to declare an error that I did not have hardware support to run it; it dropped back to classic mode (which interestingly allowed all my resolutions to work again).  Even though I restored the file Unity wouldn't start again regardless of what was selected on the login page; I ended up reinstalling after several hours of frustration.  I'm back at 1024x768; do you have any ideas on what I might need to do?

Side note:  When I check "additional drivers" no proprietary ATI driver is shown; I'd try it if it was available.

---

### Post by Segofam on 2011-05-09
I am running off the CD, and have the same problem. I won't be installing until we find a cure!

Here's mine for the info.

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 720 x 576, maximum 960 x 600
default connected 720x576+0+0 0mm x 0mm
   960x600        60.0  
   960x540        60.0  
   800x600        60.0     56.0  
   768x576        60.0  
   720x576        60.0* 
   856x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        61.0  
ubuntu@ubuntu:~$ 

...any resolution that I try, does not give me a good screen size/resolution etc
...everything is huge :-/

Has anyone had success yet?

Sincerely,

Scott.

---

### Post by MatthewMetzger on 2011-05-09
I'm having the same problem with a ThinkPad T43 laptop. Screen resolution should be 1400x1050, but I can't get higher than 1024x768.

---

### Post by Segofam on 2011-05-11
> **MAFoElffen said:**
> Try installing startup-manager
```

sudo apt-get install startup-manager

```

scott@scott-laptop:~$ sudo apt-get install startup-manager
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startup-manager
scott@scott-laptop:~$ 

This is telling me it doesn't exist right?

Scott.

---

### Post by yousaf05 on 2011-05-18
try this 

```
 	sudo apt-get install startupmanager 
```

---

### Post by viraf87 on 2011-05-23
> **MAFoElffen said:**
> What does 
```

sudo hwinfo --framebuffer

``` report back?
Try installing startup-manager
```

sudo apt-get install startup-manager

```and see if the resolution shows in there.  Is so, set it with that.  It will set the res through the grub files, where it will use KMS to pass it to Xorg...  

If it doesn't show there, Ill tell you which 2 files to change.

Have had about a dozen people with this problem in the last week, where that fixed them up.

Here is what my hwinfo --framebuffer says:
```


02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.JDs7TUQtGiB
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  009"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "009"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0319: 1280x1024 (+2560), 15 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x960 (+1280), 8 bits
  Mode 0x0365: 1280x960 (+2560), 16 bits
  Mode 0x0366: 1280x960 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
I've installed startupmanager as instructed however 1920x1080 is not an option.  The problem only started when I plugged in a smaller monitor to use for work (text editing) as it became annoying on my HD TV.  My problem is I can't seem to change the settings in monitors (the max resolution is 1280x1024), and when I unplug the small monitor I can't seem to get the system to HD resolution again.  

Hope you can help

Thanks

---

### Post by MAFoElffen on 2011-05-24
> **johnwate said:**
> Today I had the motherboard replaced as part of [Intel's Cougar Point chip recall]("http://www.huffingtonpost.com/2011/01/31/intel-chip-design-flaw_n_816408.html"). And when I restarted my computer the native 1920x1080 resolution suddenly became available. This is a bit strange, as I don't know what could have fixed the resolution problem.
@johnwate / but the instructions are the same foor the others...

I didn't see a hwinfo --framebuffer on your hardware.  No matter.  If you did it AND it did say it supported the resolution that you want the monitor to display at (1920x1080)... (that is should say and would be your limit)... 

Then on your xrandr data it "did not say" that the monitor supported what the max resolution that is should be... You can use xrandr to "ADD" a mode, Test it to see that your graphics card and can display it, then add it to your xorg.conf...

The instructionns for adding a mode are from here:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")
(Theese are just examples, so yours would be to what resolution you are trying to add and the individual results you get.)

Which says:
> Adding undetected resolutions Due  to buggy hardware or drivers, your monitor's correct resolutions may  not always be detected.  For example, the EDID data block queried from  your monitor may be incorrect. 
If the mode already exists, but just isn't associated for the particular output, you can add it like this: 

  $ xrandr --addmode DVi-0 1280x1024

If the mode doesn't yet exist, you'll need to **create it first** by specifying a modeline: 

  $ xrandr --newmode <Mode``Line>

You may create a modeline using the gtf or cvt  utility. For example, if you want to add a mode with resolution  800x600, you can enter the following command: (The output is shown  following.) 

  $ cvt 1280 1024   # 1280x1024 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz   Modeline "[COLOR=Red]1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync [/COLOR]

Then copy the information after the word "Modeline" into the xrandr command: 

  $ xrandr --newmode "[COLOR=Red]1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync [/COLOR]

After the mode is entered, it needs to be added to the output using the --addmode command as explained above
After you add it, you would then test it using xrandr
```
[FONT=monospace]
[/FONT]xrandr --output DVi-0 --mode1280x1024 --rate 60
```Then to add the mode to your xorg.conf:
[/code]
And if it tests okay and xrandr can set it between the video chipset and hardware, you should then be able to add it to you xorg,conf to make it persistent.
```

Section "Monitor"     
        Identifier      "External DVi-0"     
          Modeline        [COLOR=Red]"1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync     [/COLOR]
          Option          "PreferredMode" [COLOR=Red]"1280x1024_60.00[/COLOR]" 
EndSection 

Section "Device"     
        Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"     
        Driver          "ati"     
        Option          "Monitor-DVI-0" "External DVI" 
EndSection 

Section "Screen"     
        Identifier      "Primary Screen"     
        Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"     
        DefaultDepth    24     
        SubSection "Display"         
             Depth           24         
     Modes [COLOR=Red]  "1280x1024[/COLOR]" "1024x768" "640x480"     
        EndSubSection 
EndSection  

Section "ServerLayout"         
        Identifier      "Default Layout"         
        Screen          "Primary Screen" 
EndSection

```

---

### Post by rmf730 on 2011-07-23
Thanx !!! i had the same probleme but with xrandr i have everything in place... thx again...

---

### Post by coffeecat on 2011-07-23
Just for the record and because so many people have posted "I'm having this problem too" (or words to that effect) and I suspect that like this poster....

> **MatthewMetzger said:**
> I'm having the same problem with a ThinkPad T43 laptop. Screen resolution should be 1400x1050, but I can't get higher than 1024x768.

... some may not have the ATI Radeon HD 5450 graphics card which is the subject of this thread (the ThinkPad T43 has a much older ATI chipset).
 
And...

> **johnwate said:**
> I've enabled the "ATI/AMD proprietary FGLRX graphics driver" in "Additional Drivers".

That was probably a mistake.

**The ATI Radeon HD 5450 works out of the box in 11.04 with the default open source driver**. This will give you Unity, 3d acceleration, compiz, and the screen resolutions people are having problems with without any fiddling about.

---

### Post by steve11911 on 2011-07-24
Near the bottom of this page are instructions for adding undetected resolutions,explained far better than I could.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Let us know...

---

### Post by TheOz on 2012-02-14
Same problem here Dell Optiplex 990 Radeon HD 5450, Dell 30' I cant get more that 1600x1200 even if the monitor supports up to 2560x1600
```

norsk
    description: Mini Tower Computer
    product: OptiPlex 990
    vendor: Dell Inc.
    version: 01
    serial: CNXP55J
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=mini-tower frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=44454C4C-4E00-1058-8050-C3C04F35354A
  *-core
       description: Motherboard
       product: 06D7TR
       vendor: Dell Inc.
       physical id: 0
       version: A00
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A06 (07/25/2011)
          size: 64KiB
          capacity: 10176KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot

        *-pci:0
             description: PCI bridge
             product: Sandy Bridge PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:e1400000-e14fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Cedar PRO [Radeon HD 5450]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:30 memory:d0000000-dfffffff(prefetchable) memory:e1420000-e143ffff ioport:3000(size=256) memory:e1400000-e141ffff(prefetchable)

```

Ubuntu 11.04/11.10 & Debian Squeeze

---

