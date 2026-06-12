---
title: "1680x1050 mode doesn't work, but did in FC4,5 and 6 !"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by elmerfud on 2007-03-17
I have an HP ZD7280.  I am running kubuntu 6.10.  I am a long time Linux user and I previously ran Fedora Core 4/5/6 on this machine.

I've got a problem in that Kubuntu won't properly drive the 17 inch 1680x1050 LCD monitor on the ZD7280, but it does properly drive an external Dell FPW2005 at 1680x1050.

Kubuntu drives the built in monitor at 1440x900 @ 60HZ.  The xorg.conf has modlines for 1680x1050 and they are identical to the xorg.conf that was used in Fedora, but yet it doesn't work. 

If I use the "detect monitor" in the hardware->configure in "Monitor and Display" in System Settings, it comes up with Plug and Play.  In FC, I could use either a generic 1680x1050 monitor or actually the Dell 2005 FPW device and the laptop monitor worked correctly. 

What do I do to get the laptop monitor working properly ?

Thanks

---

### Post by bulldog on 2007-03-17
I'm not an expert on this thing,but I have a monitor with the 1680X1050 resolution too..................only it's a 20inch widescreen and not a 17inch.

Are you absolutely sure your 17inch has the capability for that resolution???
The 1440X900 is the native resolution for a 17inch widescreen I presume.

---

### Post by elmerfud on 2007-03-17
Yes, I am absolutely sure.  I ran it for 2 years at 1680x1050 in FC.

They don't sell the zd7280 anymore, but there are still some for sale frm time to time.
[http://www.shopping.com/xPO-Hewlett-Packard-Pavilion-Notebook-with-Intel-Pentium-4-Processor-3-2GHz-zd7280us](http://www.shopping.com/xPO-Hewlett-Packard-Pavilion-Notebook-with-Intel-Pentium-4-Processor-3-2GHz-zd7280us)

You can get multiple screens on the ZD line, the highest end one is WSXGA+, 1680 x 1050.

Its a great screen.  My laptop has been excellent.  I love the big, high resolution screen and the full sized keyboard with number pad.  Its heavy and the battery life isn't great, but its a great desktop replacement machine.  I highly recommend them.

Here is a replacement screen for it.  Notice the 1680x1050 resolution. 
[http://www.lcds4less.com/HPLaptop__HP_Pavilion_ZD7200_Series_ZD7280__laptop-screens.html](http://www.lcds4less.com/HPLaptop__HP_Pavilion_ZD7200_Series_ZD7280__laptop-screens.html)

---

### Post by hal8000 on 2007-03-17
Can you post your /etc/X11/xorg.conf file.

At a guess it could possibly be the default colour depth, if for example your graphic card cant supply your desired resolution at default colour depth this may be why. I would
also have a look in /var/log/messages and /var/log/Xorg.0.log for clues.

State also your graphics carda and amount of onboard Video RAM please.

---

### Post by elmerfud on 2007-03-19
Here is my Xorg.conf file.  I get the same problem if I use a Generic flat panel, plug and play or the Dell FPW 2005.  I've got the same modline for 1680x1050 that worked fine in FC4,5 and 6.

My Xorg.0.log file has this in it:

========================================================================
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX Go5700 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.36.20.31.a2
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX Go5700 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Dell 2005FPW (CRT-0)
(--) NVIDIA(0):     LGP (DFP-0)
(--) NVIDIA(0): Dell 2005FPW (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): LGP (DFP-0): 300.0 MHz maximum pixel clock
(--) NVIDIA(0): LGP (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1920x1200@60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050@60"
(II) NVIDIA(0):     "1600x1024@60"
(II) NVIDIA(0):     "1280x768@60"
(II) NVIDIA(0):     "800x600@60"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(**) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce FX Go5700 at PCI:1:0:0
(--) NVIDIA(1): VideoRAM: 131072 kBytes
(--) NVIDIA(1): VideoBIOS: 04.36.20.31.a2
(II) NVIDIA(1): Detected AGP rate: 8X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce FX Go5700 at
(--) NVIDIA(1):     PCI:1:0:0:
(--) NVIDIA(1):     Dell 2005FPW (CRT-0)
(--) NVIDIA(1):     LGP (DFP-0)
(--) NVIDIA(1): Dell 2005FPW (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): LGP (DFP-0): 300.0 MHz maximum pixel clock
(--) NVIDIA(1): LGP (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(1): Assigned Display Device: DFP-0
(WW) NVIDIA(1): No valid modes for "1680x1050@60"; removing.
(WW) NVIDIA(1): No valid modes for "1920x1200@60"; removing.
(WW) NVIDIA(1): No valid modes for "1600x1024@60"; removing.
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "1280x768@60"
(II) NVIDIA(1):     "800x600@60"
(II) NVIDIA(1): Virtual screen size determined to be 1280 x 768
(--) NVIDIA(1): DPI set to (115, 115); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
=====================================================================================

Apparently it can't find a valid mode for 1680x1050.  Any ideas ?

---

### Post by elmerfud on 2007-04-23
I installed Feisty over the weekend and I still have the same problem.

However, I noticed that the laptop display worked fine if I used driver "nv" in xorg.conf instead of "nvidia".  However, the "nv" driver won't drive the external monitor. :( 

I reported this as a bug.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108210](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108210)

---

### Post by ariel on 2007-04-24
Hi, I have a Dell D820 with the same display as yours. Both Edgy and Feisty default installs used 1280x1024 resolution, and System > Preferences > Screen Resolution did not show the option to increase that.

To fix it, all I had to do was open Synaptics, and then install the package called 915resolution

Then reboot the laptop and voila.

Hope this helps.

---

### Post by elmerfud on 2007-04-24
The 915Resolution package is for Intel video cards.  I'm running an nvidia card.  

-------------------------------------------------------------------------------------------------------------------------
Intel video BIOS hack to support certain resolutions. 
 915resolution is a tool to modify the video BIOS of the 800 and 900 series Intel graphics chipsets. This includes the 845G, 855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets. This modification is necessary to allow the display of certain graphics resolutions for an Xorg or XFree86 graphics server.

 
 915resolution's modifications of the BIOS are transient. There is no risk of permanent modification of the BIOS. This also means that 915resolution must be run every time the computer boots inorder for it's changes to take effect.

 
 915resolution is derived from the tool 855resolution. However, the code differs substantially. 915resolution's code base is much simpler. 915resolution also allows the modification of bits per pixel.
--------------------------------------------------------------------------------------------------------------------------

[http://dag.wieers.com/rpm/packages/915resolution/](http://dag.wieers.com/rpm/packages/915resolution/)

---

### Post by m3741 on 2007-04-24
Try commenting out all of the other modelines except the "1680x1050@60" under both monitor sections (just to be sure). Also comment out the old modes line under each screen section and replace them with modes "1680x1050@60" . I've had similar issues before and it seems like sometimes you have to give it only one option.

Also, when you are using the 15pin VGA connector, the nvidia driver makes that the primary display device with no way to specify otherwise. It's highly annoying.

Attached is my Xorg.conf file. I used to run two monitors (hence the commented out sections) but the problem that I stated above made me go back to one. YMMV.

---

