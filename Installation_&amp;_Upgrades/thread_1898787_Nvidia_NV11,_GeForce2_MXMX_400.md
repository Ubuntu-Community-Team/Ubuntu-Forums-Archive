---
title: "Nvidia NV11, GeForce2 MX/MX 400"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by nhasan on 2011-12-22
Hi Guys,

I installed lubuntu to an old computer of mine (P3). It starts up fine. I saw that the resolution wasn't the best (probably around 1024x768) so I tried to switch to the nvidia drivers which dropped me down to 640x480. Note I can boot into lubuntu fine - in fact i am making this post from lubuntu.

Thanks for any help!!

Just went through the same type off issue on my other computer so here are some of the command output which might be of interest... Note: I think from looking at the xorg.0.log I am running into the same old EDID not detected... I am using a HDTV for a monitor (Sanyo lcd-26E3) and couldnt really find too much documentation online. Here are a couple of links

[http://www.bestcost.ca/article.asp?langue=e&noid=2897]("http://www.bestcost.ca/article.asp?langue=e&noid=2897"). [http://tv.manualsonline.com/manuals/mfg/sanyo/lcd26e3.html?idRes=14948413]("http://tv.manualsonline.com/manuals/mfg/sanyo/lcd26e3.html?idRes=14948413")

```
toast@Pluto:/var/log$ lspci -vnn | grep VGA
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 MX/MX 400] [10de:0110] (rev a1) (prog-if 00 [VGA controller])

```

Here is the second batch of info...
```
toast@Pluto:/var/log$ sudo hwinfo --framebuffer
[sudo] password for toast: 
> hal.1: read hal dataprocess 2730: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.HCiprRATnBF
  Hardware Class: framebuffer
  Model: "NVidia NV10 Reference Board"
  Vendor: "NVidia Corporation"
  Device: "NV10 Reference Board"
  SubVendor: "NVidia"
  SubDevice: 
  Revision: "Chip Rev A1"
  Memory Size: 32 MB
  Memory Range: 0xf0000000-0xf1ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
toast@Pluto:/var/log$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 2736: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
24: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 640x480@73Hz
  Driver Info #0:
    Max. Resolution: 640x480
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-38 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
toast@Pluto:/var/log$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
toast@Pluto:/var/log$ 

```

The xorg.0.log is attached

Thank you again.

~nhasan

---

### Post by GeorgeVita on 2011-12-22
Hi nhasan,
one idea is to test a possible "higher resolution" mode using terminal commands. When you succeed try to adjust your xorg.conf file.

Take a look at [http://ubuntuforums.org/showpost.php?p=10610565&postcount=2](http://ubuntuforums.org/showpost.php?p=10610565&postcount=2)
Note that all commands are documented using terminal command **man** (ex.: man xrandr)
G

---

### Post by MAFoElffen on 2011-12-22
> **nhasan said:**
> Hi Guys,

I installed lubuntu to an old computer of mine (P3). It starts up fine. I saw that the resolution wasn't the best (probably around 1024x768) so I tried to switch to the nvidia drivers which dropped me down to 640x480. Note I can boot into lubuntu fine - in fact i am making this post from lubuntu.

Thanks for any help!!

Just went through the same type off issue on my other computer so here are some of the command output which might be of interest... Note: I think from looking at the xorg.0.log I am running into the same old EDID not detected... I am using a HDTV for a monitor (Sanyo lcd-26E3) and couldnt really find too much documentation online. Here are a couple of links

[http://www.bestcost.ca/article.asp?langue=e&noid=2897](http://www.bestcost.ca/article.asp?langue=e&noid=2897). [http://tv.manualsonline.com/manuals/mfg/sanyo/lcd26e3.html?idRes=14948413](http://tv.manualsonline.com/manuals/mfg/sanyo/lcd26e3.html?idRes=14948413)

```
toast@Pluto:/var/log$ lspci -vnn | grep VGA
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 MX/MX 400] [10de:0110] (rev a1) (prog-if 00 [VGA controller])

```Here is the second batch of info...
```
toast@Pluto:/var/log$ sudo hwinfo --framebuffer
[sudo] password for toast: 
> hal.1: read hal dataprocess 2730: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.HCiprRATnBF
  Hardware Class: framebuffer
  Model: "NVidia NV10 Reference Board"
  Vendor: "NVidia Corporation"
  Device: "NV10 Reference Board"
  SubVendor: "NVidia"
  SubDevice: 
  Revision: "Chip Rev A1"
  Memory Size: 32 MB
  Memory Range: 0xf0000000-0xf1ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
toast@Pluto:/var/log$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 2736: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
24: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 640x480@73Hz
  Driver Info #0:
    Max. Resolution: 640x480
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-38 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
toast@Pluto:/var/log$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
toast@Pluto:/var/log$ 

```The xorg.0.log is attached

Thank you again.

~nhasan
This monitor does have edid data either?

What makes me "curious" about this one (and may need other investigation is the Xalloc warnings where it said it was "requesting a ridiculous amount of memory":
```

dmesg | grep alloc

```I'm out the door at moment. When I get back tonight, I'll look at modelines for this display and create an xorg,conf for Nouveau for you.

---

### Post by nhasan on 2011-12-22
Thanks MAFoElffen I was hoping you would come to the rescue!

Yes, this one is not providing the EDID data as well... I know how to pick em :P... I am at work right now will post the results when I get home

GeorgeVita: Thanks for the advise I will keep it in my backpocket to try out. I want to see how things work out with MAFoElffen first :)

~nhasan

PS: I started the computer and didn't the same excessive memory request this time around. I have attached the Xorg.0.log just in case. The output of the demsg is below... thanks again!

```
toast@Pluto:/var/log$ dmesg | grep alloc
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] allocated 4193728 bytes of page_cgroup
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.026541] ftrace: allocating 24878 entries in 49 pages
[    0.368890] HugeTLB registered 4 MB page size, pre-allocated 0 pages

```

---

### Post by MAFoElffen on 2011-12-23
> **nhasan said:**
> Thanks MAFoElffen I was hoping you would come to the rescue!

Yes, this one is not providing the EDID data as well... I know how to pick em :P... I am at work right now will post the results when I get home

GeorgeVita: Thanks for the advise I will keep it in my backpocket to try out. I want to see how things work out with MAFoElffen first :)

~nhasan

PS: I started the computer and didn't the same excessive memory request this time around. I have attached the Xorg.0.log just in case. The output of the demsg is below... thanks again!

```
toast@Pluto:/var/log$ dmesg | grep alloc
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] allocated 4193728 bytes of page_cgroup
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.026541] ftrace: allocating 24878 entries in 49 pages
[    0.368890] HugeTLB registered 4 MB page size, pre-allocated 0 pages

```
Are you using the vga or hdmi port on the TV? Never mind... see next post.

---

### Post by MAFoElffen on 2011-12-23
Here you go:
```

# X configuration file generated by MAFoElffen (custom)
# Revised As Of: 2011.12.22
# Not generated by $ sudo Xorg -configure
# 

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Sanyo LCD TV 26"
    ModelName      "LCD26E3"
    DisplaySize     575.759 323.712 
    HorizSync       31.47 - 41.78
    VertRefresh     59.94 - 60
    Option         "DPMS"
    ## Valid PC Modes = 1360x768, 1280x768, 1024x768, 800x600, 640x640 all @ 60 Hz
    Modeline "1360x768"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
    Modeline "1280x768"   93.75  1280 1360 1488 1696  768 771 781 802 -hsync +vsync
    Modeline "1024x768"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsyn
    Modeline "800x600"     38.25   800   832   912 1024  600 603 607 624 -hsync +vsync
    Option         "PreferredMode" "1360x768_60"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName    "NVIDIA GeForce 2 MX/MX 400 (NV10)"
  Option    "UseEDID"    "False"

EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection      "Display"
        Depth       24
        Modes       "1360x768"
    EndSubSection
EndSection

```

---

### Post by nhasan on 2011-12-23
Thanks MAFoElffen!

I am going to try this out tonight once I am back from work.

~nhasan

---

### Post by nhasan on 2011-12-24
Sorry, I got sidetracked and didnt get a chance to post back to the forums. I tried the new settings after a syntax thing ;) it worked. Well partially. 

The used space looks good (with small fonts though) and there is a lot of the screen which is left black all around it. There were different "pix shapes" options in the TV / Monitor. Switching from Dot By Dot to Normal expands the used area to the top and bottom in terms of the graphics (the fonts remain small though...) and if I choose the Full option then it stretches the graphic to fill the whole screen but they look pretty bad.

Anyway to use the whole screen / expand the graphics and get a good resolution?

Thanks!!
~nhasan

---

### Post by MAFoElffen on 2011-12-24
> **nhasan said:**
> Sorry, I got sidetracked and didnt get a chance to post back to the forums. I tried the new settings after a syntax thing ;) it worked. Well partially. 

The used space looks good (with small fonts though) and there is a lot of the screen which is left black all around it. There were different "pix shapes" options in the TV / Monitor. Switching from Dot By Dot to Normal expands the used area to the top and bottom in terms of the graphics (the fonts remain small though...) and if I choose the Full option then it stretches the graphic to fill the whole screen but they look pretty bad.

Anyway to use the whole screen / expand the graphics and get a good resolution?

Thanks!!
~nhasan
Have you tried to manually edit the prefeeref mode and the mode (should be same value in 2 diffrent sections) to another resolution? In they don't go well. I'll recalc (remember there are 3 different methods) so you can see what works best. Since this is Christmas eve...

---

### Post by nhasan on 2011-12-25
Merry Christmas MAFoElffen! Please enjoy the time with your family.

I am going to be busy as well so cannot really troubleshoot this one too :)

I just wanted to check the Xorg.0.log and as it turns out it did had a couple of errors in (related to memory). Please take a look (when you get a chance) and also the resolution on hte monitor looks like it is being set to 800x600.

---

### Post by nhasan on 2011-12-27
Ok, I am back to try to troubleshoot this thing :)

Here is the latest Xorg.0.log and the dmesg messages corresponding:

```
toast@Pluto:~$ dmesg | grep alloc
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] allocated 4193728 bytes of page_cgroup
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.026333] ftrace: allocating 24878 entries in 49 pages
[    0.364866] HugeTLB registered 4 MB page size, pre-allocated 0 pages

```

Thanks for any help!

~nhasan

---

### Post by MAFoElffen on 2011-12-28
> **nhasan said:**
> Ok, I am back to try to troubleshoot this thing :)

Here is the latest Xorg.0.log and the dmesg messages corresponding:

```
toast@Pluto:~$ dmesg | grep alloc
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] allocated 4193728 bytes of page_cgroup
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.026333] ftrace: allocating 24878 entries in 49 pages
[    0.364866] HugeTLB registered 4 MB page size, pre-allocated 0 pages

```Thanks for any help!

~nhasan
What happens if you add "vmalloc=192MB" as a kernel boot option. That way it allocates that much memory to graphics...  And you said 800x600?  I saw in the xorg log that is said 1360x768 wasn't recognized as a valid mode?  I have some server (RAID) problems I have to work on tomorrow, but Thursday I'll play with a few things in the xorg.conf.

---

### Post by nhasan on 2011-12-28
Hey MAFoElffen,

I tried adding nomodeset and also the vmalloc and still get the unpleasantly large amount of memory allocation. Just so you know I dont see a bios or grub screen all the way until the final lubuntu screen shows up... this is the behaviour ever since I have installed lubuntu (the monitor just say no supported input)

Here is the Kernel parameter...

```
linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=9afa13cc-68e0-4d20-8c7e-50eb5a0faf8c ro    quiet nomodeset vmalloc=192MB
```

```
oast@Pluto:~$ sudo dmesg | grep alloc
[sudo] password for toast: 
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=9afa13cc-68e0-4d20-8c7e-50eb5a0faf8c ro quiet nomodeset vmalloc=192MB
[    0.000000] allocated 4193728 bytes of page_cgroup
[    0.000000]     vmalloc : 0xf37fe000 - 0xff7fe000   ( 192 MB)
[    0.026345] ftrace: allocating 24878 entries in 49 pages
[    0.364941] HugeTLB registered 4 MB page size, pre-allocated 0 pages
toast@Pluto:~$ 


```

Thanks again!

Regards,
~nhasan

---

### Post by nhasan on 2011-12-30
Ok, a couple of things...

I tried updating the BIOS just in case that made a difference (no improvement - had to plugin another monitor to get it to show me the BIOS / FreeDOS (now that was an adventure :)) screens...)

Also did a bit of research on the exact error. It turns out it *may* have to do with requesting 0 bytes memory or too much memory... I don't know if the following code is included in the module (or even if this thing is included in the system I am running :P)

```
void *
Xrealloc(void *ptr, unsigned long amount)
{
    /*
     * Xrealloc used to return NULL when large amount of memory is requested. In
     * order to catch the buggy callers this warning has been added, slated to
     * removal by anyone who touches this code (or just looks at it) in 2011.
     *
     * -- Mikhail Gusarov
     */
    if ((long)amount <= 0)
	ErrorF("Warning: Xrealloc: "
	       "requesting unpleasantly large amount of memory: %lu bytes.\n",
               amount);

    return realloc(ptr, amount);
}

```

[http://cgit.freedesktop.org/xorg/xserver/commit/?id=e983848ab44b0769f97f6207f1aa8b4f127be6a9]("http://cgit.freedesktop.org/xorg/xserver/commit/?id=e983848ab44b0769f97f6207f1aa8b4f127be6a9")

[http://webcache.googleusercontent.com/search?q=cache:t2eXGH6knJcJ:cgit.freedesktop.org/xorg/xserver/commit/%3Fid%3De983848ab44b0769f97f6207f1aa8b4f127be6a9+Xrealloc:+%22requesting+unpleasantly+large+amount+of+memory%22&cd=1&hl=en&ct=clnk&gl=ca]("http://webcache.googleusercontent.com/search?q=cache:t2eXGH6knJcJ:cgit.freedesktop.org/xorg/xserver/commit/%3Fid%3De983848ab44b0769f97f6207f1aa8b4f127be6a9+Xrealloc:+%22requesting+unpleasantly+large+amount+of+memory%22&cd=1&hl=en&ct=clnk&gl=ca")

Thanks again for any assistance.

Regards,
~nhasan

---

### Post by nhasan on 2011-12-31
A gentle *bump*

~nhasan

---

### Post by MAFoElffen on 2011-12-31
> **nhasan said:**
> A gentle *bump*

~nhasan
Sorry, my server has been down a few days and has been giving me my own adventures.  When I get back tonight, I have to post some of my own threads on that.

On the memory issue- I think it's time to file a bug on that at launchpad.  They should tell you how to do a backtrace to submit.

I'm really curious myself what this might be, so I hope you stay in touch and let me in on this.... I'll follow those links you posted and see if another set of eyes does any good.

EDIT-- Read through. Straight forward, except where it's called from.. Let me see...

---

### Post by GeorgeVita on 2012-01-01
:-({|= **[COLOR="Navy"]Happy New Year![/COLOR]**

Take a look at [http://www.mythtv.org/wiki/Modeline_Database#Sanyo](http://www.mythtv.org/wiki/Modeline_Database#Sanyo)
and the manual of your LCD26E3: [http://ca.sanyo.com/dynamic/product/Downloads/19-26-32-42-USA-0410%20final-21905799.pdf](http://ca.sanyo.com/dynamic/product/Downloads/19-26-32-42-USA-0410%20final-21905799.pdf)
At page 26 mentions the maximum PC mode "WXGA" 1360x768, V-Freq=60Hz, H-Freq=47.712KHz, pixels clock 85.5MHz

I think that a proper "modeline" with **xrandr** command can fix it.

G

---

### Post by MAFoElffen on 2012-01-01
> **GeorgeVita said:**
> :-({|= **[COLOR=Navy]Happy New Year![/COLOR]**

Take a look at [http://www.mythtv.org/wiki/Modeline_Database#Sanyo](http://www.mythtv.org/wiki/Modeline_Database#Sanyo)
and the manual of your LCD26E3: [http://ca.sanyo.com/dynamic/product/Downloads/19-26-32-42-USA-0410%20final-21905799.pdf]("http://ca.sanyo.com/dynamic/product/Downloads/19-26-32-42-USA-0410%20final-21905799.pdf")
At page 26 mentions the maximum PC mode "WXGA" 1360x768, V-Freq=60Hz, H-Freq=47.712KHz, pixels clock 85.5MHz

I think that a proper "modeline" with **xrandr** command can fix it.

G
Which you are saying- use the pixel clock value to calculate the modeline?  If so, then his modeline for 1360x768@85.50mHz would be:

"1360x768"  125.85  1360 1448 1592 1824  768 769 772 807  -HSync +Vsync

There's another factor in this... There's 3 ways to calculate modelines. 2 are calculative... The third is specific to nvidia.  The one specific to nvidia is that some of their cards ignore modelines that are not specific to that card. Those internal modelines are found through a lookup table, queried through hwinfo and tested with xrandr...

---

### Post by GeorgeVita on 2012-01-01
> **MAFoElffen said:**
> Which you are saying- use the pixel clock value to calculate the modeline?  If so, then his modeline for 1360x768@85.50mHz would be:
"1360x768"  125.85  1360 1448 1592 1824  768 769 772 807  -HSync +Vsync
Hi MAFoElffen, as I don't have the experience to calculate xrandr modeline parameters I used the terminal command **cvt** resulting to the following:
```
g@LL:~$ cvt 1360 768 60
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
g@LL:~$ 
```
Assuming that data from the TV users manual is correct:
1360x768, V-Freq=60Hz, H-Freq=47.712KHz, pixels clock 85.5MHz

Below are the closer timings from [MythTV wiki modeline database]("www.mythtv.org/wiki/Modeline_Database"):
```
1360   768   60Hz   47.7121kHz	85.50 1360 1424 1536 1792 768 771 778 795 -HSync -VSync
1360   768   59.8Hz 47.70kHz	84.75 1360 1432 1568 1776 768 771 776 798 +Hsync -Vsync 
1360   768   60Hz   47.70kHz	84.72 1360 1424 1568 1776 768 769 772 795 -HSync +Vsync 

```

As I do not have the hardware to test my opinion is to use:
1360   768   60Hz   47.7121kHz	**85.50 1360 1424 1536 1792 768 771 778 795 -HSync -VSync**

Regards,
George

[SIZE="1"]P.S. the "closest" data are from a Sharp LC-37D65E (in case of service manuals comparison)[/SIZE]

---

### Post by MAFoElffen on 2012-01-01
> **GeorgeVita said:**
> Hi MAFoElffen, as I don't have the experience to calculate xrandr modeline parameters I used the terminal command **cvt** resulting to the following:
```
g@LL:~$ cvt 1360 768 60
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
g@LL:~$ 
```Assuming that data from the TV users manual is correct:
1360x768, V-Freq=60Hz, H-Freq=47.712KHz, pixels clock 85.5MHz

Below are the closer timings from [MythTV wiki modeline database]("http://www.mythtv.org/wiki/Modeline_Database"):
```
1360   768   60Hz   47.7121kHz    85.50 1360 1424 1536 1792 768 771 778 795 -HSync -VSync
1360   768   59.8Hz 47.70kHz    84.75 1360 1432 1568 1776 768 771 776 798 +Hsync -Vsync 
1360   768   60Hz   47.70kHz    84.72 1360 1424 1568 1776 768 769 772 795 -HSync +Vsync 

```As I do not have the hardware to test my opinion is to use:
1360   768   60Hz   47.7121kHz    **85.50 1360 1424 1536 1792 768 771 778 795 -HSync -VSync**

Regards,
George

[SIZE=1]P.S. the "closest" data are from a Sharp LC-37D65E (in case of service manuals comparison)[/SIZE]
```
[FONT=monospace]
[/FONT]Modeline "1360x768_60"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

```
From the Xorg.conf file I created from him in post 6 of this thread was through cvt and the same manual
```

Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

```
Is what comes out using gtf.
The the MythTV modeline:
```

ModeLine "1360x768" 85.50 1360 1424 1536 1792 768 771 778 795 -HSync -VSync 

```
Listed is from a tweeked HDTV mode.  If your look for the same in the NVidia section (which he has an old NVidia card... theres a bit skip between 1280xXXX and 1400xXXX. 

The Xorg log says that 1360 is not a recognised resolution and gets kicked down to 800x600, then gets an Xalloc error. 800x600 is native in the card, but not the Monitor. True if it would go into a native to the display... I'm thinking rather maybe  something like 1280x768.  There is a native nvidia modeline:
```

ModeLine "1280x768" 80.14 1280 1344 1480 1680 768 769 772 795 +HSync +VSync 

```

---

### Post by nhasan on 2012-01-01
Thanks guys for all the help! and Happy New Year.

I feel guilty for taking up so much of your time / effort. I tried the setting suggested 1024x768 and it resulted in the same 800x600 resolution with the re-alloc error. I have attached the modified xorg.conf file along wit the log file.

Please let me know where to go to file the launchpad bug and I will be glad to fill it out.

Thanks again,
~nhasan

---

### Post by MAFoElffen on 2012-01-01
> **nhasan said:**
> Thanks guys for all the help! and Happy New Year.

I feel guilty for taking up so much of your time / effort. I tried the setting suggested 1024x768 and it resulted in the same 800x600 resolution with the re-alloc error. I have attached the modified xorg.conf file along wit the log file.

Please let me know where to go to file the launchpad bug and I will be glad to fill it out.

Thanks again,
~nhasan
I never asked if you are using an vga port or if your connected HDMI... Looks like in the Xorg log that it's the standard vga.

Writing you another xorg.conf file.

---

### Post by MAFoElffen on 2012-01-02
Here you go. You know from the one I did for your other box, how to change the modes... Happy testing.
```

# nvidia-xconfig: X configuration file generated by MAFoElffen (custom)
# Revised As Of: 2012.1.1
# Not generated by nvidia-xconfig:
# 


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
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
    Identifier     "Monitor0"
    VendorName     "Sanyo LCD TV 26"
    ModelName      "LCD26E3"
    DisplaySize     575.759 323.712 
    HorizSync       31.47 - 41.78
    VertRefresh     59.94 - 60
    Option         "DPMS"
    ## Valid PC Modes = 1360x768, 1280x768, 1024x768, 800x600, 640x640 all @ 60 Hz
    UseModes        "Sanyo_Native"
    Option "PreferredMode"   "1360x768"
EndSection

Section "Modes"
    Identifier    "CVT_Calc"
    # Thes were calcculated using the linux cvt utility.
    Modeline "1360x768"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
    Modeline "1280x768"   93.75  1280 1360 1488 1696  768 771 781 802 -hsync +vsync
    Modeline "1024x768"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
    Modeline "800x600"    38.25  800   832  912 1024  600 603 607 624 -hsync +vsync
EndSection

Section "Modes"
    Identifier    "GTF_Calc"
    #These were calculated using the Linux gft utility.
    Modeline "1360x768"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
    Modeline "1280x768"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
    Modeline "1024x768"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
    Modeline "600x600"   28.96   600  624  688  776  600 601 604 622  -HSync +Vsync    
EndSection 

Section "Modes"
    Identifier    "NV_Calc"
    ## Nvida Recognised Internal Modes. The NVidia Techs say that some of there calds 
    # ignore add modes except for the internal modes in their card. These modelines are 
    # from NVidia, saying they will recognise these...
    ModeLine "1360x768" 85.50 1360 1424 1536 1792 768 771 778 795 -HSync -VSync
    ModeLine "1280x768" 80.14 1280 1344 1480 1680 768 769 772 795 +HSync +VSync
    ModeLine "1024x768" 65.00 1024 1048 1184 1344 768 771 777 806 -HSync -VSync
    ModeLine "800x600"  40.00  800  840  968 1056 600 601 605 628 +HSync +VSync
EndSection

Section "Modes"
    Identifier     "Sanyo_Native"
    Modeline "1360x768" 85.500 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
    Modeline "1280x768" 79.464 1280 1360 1488 1664 768 771 778 798 -hsync +vsync
    Modeline "1024x768" 74.871 1024 1064 1200 1344 768 771 777 806 -hsync -vsync
    Modeline "800x600"  40.025  800  856  984 1056 600 601 605 628 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NVIDIA GeForcee2 MX/MX 400 (NV11)"
    Option         "UseEDID" "FALSE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection
        Depth       24
        Mode        "1360x768"
    EndSubSection
EndSection

```
File is also attached as usual.

---

### Post by topsites on 2012-01-02
Rule of Unix:
Never, ever install anything that is not absolutely essential.
Now if a program requires it, fine, but otherwise this is not Windows, every piece of hardware does not have to have the latest and greatest driver and that's probably mostly because when something goes wrong, you can't call 1-800 support to walk you through the procedure over the phone.

Give you Nvidia users a clue concerning Linux and what have you:
Unless you specifically have to install some driver because a program that you absolutely must use requires it, my advice is if it works, don't fix it!

Now Ubuntu has come a long ways since the days of Gutsy, back then us Nvidia users could be found hacking at the X-server for HOURS and I mean hours would turn into DAYS of black boxing and rebooting which...

One eventually learns:
If you think you need it, don't install it.
If it works, don't fix it.

---

### Post by nhasan on 2012-01-02
Thanks MAFoElffen and George... really appreciated it. I will be trying out the settings tomorrow and will post an update hopefully. 

Too many ppl over so couldnt get to it together.

I have created a launchpad account (actually apparently had it for a long time :) ). Let me know if there is any pointers to consider (or a good post to read) before creating a bug report I will post it up.

~nhasan

---

### Post by MAFoElffen on 2012-01-04
> **nhasan said:**
> Thanks MAFoElffen and George... really appreciated it. I will be trying out the settings tomorrow and will post an update hopefully. 

Too many ppl over so couldnt get to it together.

I have created a launchpad account (actually apparently had it for a long time :) ). Let me know if there is any pointers to consider (or a good post to read) before creating a bug report I will post it up.

~nhasan
Report wirh
```

sudo ubuntu-bug xorg

```
And report "xserver-xorg-core" as the affected package... They'll change it from there after the determine what is what.  Please tell me the bug number so I can join it a jump in where needed.

---

