---
title: "Failed to load nVidia Driver after kernel upgrade (Feisty Fawn 2.6.20-16)"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by soma4me on 2007-09-03
Hi,

Need help with nVidia Driver failure in X Server startup.   First, some background:

[LIST=1]
[*]I've installed Feisty Fawn with kernel version 2.6.20-15 couple of months ago.
[*]Video card is nVidia GeForce 7300 GT
[*]Installation of Feisty Fawn under kernel 2.6.20-15 went flawless.   The video card was recognized and configured properly without any tweaking at all
[*]System worked perfectly until last night when Update Manager prompted to upgrade to kernel 2.6.20-16.
[*]From GRUB menu, I can still use 2.6.20-15 without any issue (what I'm using now :)).  However, I'm getting the following error when 2.6.20-16 kernel is selected (from Xorg.0.log):
[/LIST]

> 
[FONT="Courier New"](II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/FONT]

On the other hand, under kernel 2.6.20-15, the nVidia driver is loaded correctly (from Xorg.0.log):

> [FONT="Courier New"](II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.07
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:1:0:0:
(--) NVIDIA(0):     Gateway FPD2275W (CRT-0)
(--) NVIDIA(0): Gateway FPD2275W (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0):     "1400x1050"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (88, 88 ); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp[/FONT]

Is this a kernel bug? do I need to get new nVidia driver? I can only get in 2.6.20-16 Recovery mode, how do I install nVidia driver if needed?

Thanks for any help!

---

### Post by Pumalite on 2007-09-03
With each new kernel you have to recompile your driver.

---

### Post by soma4me on 2007-09-03
> **Pumalite said:**
> With each new kernel you have to recompile your driver.

Pumalite,

Thanks.   Would you mind be more specific on how do I recompile the nVidia driver?    Thanks again.  :confused:

---

### Post by Pumalite on 2007-09-03
If I were you I would use a proprietary driver ( which is what I do ). If you have Nvidia, go to Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) Follow the instructions; if you get lost come back for help.

---

### Post by soma4me on 2007-09-03
> **Pumalite said:**
> If I were you I would use a proprietary driver ( which is what I do ). If you have Nvidia, go to Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) Follow the instructions; if you get lost come back for help.

Pumalite,

Thanks for the additional information.   I've briefly browsed the information on the nVidia site, now I'm a bit skittish about installing the driver directly.

There are 3 version under Linux IA32: 100.14.11, 1.0-71xx series and 1.0-96xx series, I've searched the ReadME file of each, GeForce 7300GT appeared only in the 100.14.11 version, it also listed possibility of needing proper kernel header files and such.....Here are some additional questions before I jump into the pool -- hope you don't mind :):

[LIST=1]
[*]With Feisty (2.6.20-15), I'm able to execute nvidia-settings and have no issues configuring refresh rate and OpenGL, and the driver version is 1.0-9631.    This mean the nVidia driver is configured and running correctly, no?
[*]What are the advantages of using nVidia driver from nVidia vs. Ubuntu Repository?   I always thought Ubuntu put in quite a bit of effort to make sure hardware compatibility, especially video cards.....
[*]is 2.6.20-15 upgrade to 2.6.20-16 considered a kernel upgrade or just a patch?
[*]Now the most important question:  If the installation of nVidia 100.14.11 driver failed, what's the risk of leaving a totally unusable system?
[/LIST]

I know this is asking a lot....But hopefully you can understand I am not accustom in changing/playing with system drivers and such.....mainly, I'm doing web development in my box...

Thanks again for your help.

---

### Post by Pumalite on 2007-09-03
Look; it's a matter of personal opinion what to use. I believe the latest Nvidia drivers from the site give you more latitude (LCD Monitors and others). To install Nvidia driver from the site you need to have build-essential (at the terminal: sudo apt-get install build-essential), this gives you 'make', 'automake' and I think the headers too. The other thing you can do at your terminal is: sudo apt-get install nvidia-glx-new (in your new kernel). Finally 15 to 16 is an upgrade not a patch. Hope it helps.

---

### Post by soma4me on 2007-09-03
Pumalite,

I've tried 'sudo apt-get install nvidia-glx-new' in the new kernel (use recovery mode from grub menu and verified kernel version with 'cat /proc/version').   After the upgrade, I do see the driver was updated to 1.0.9755 (from 1.0.9631), unfortunately, the same error occurred when trying to start X server in the new kernel :(, but fortunately, I am still able to get into the old kernel :)

I guess I'll try to install the driver directly from nVidia site.   Or may be trying to post to LaunchPad first to see if I get lucky.....

Thanks a bunch!!

---

### Post by Pumalite on 2007-09-03
You are welcome. Come back if you need more detailed instructions on how to install the driver.

---

### Post by soma4me on 2007-09-07
Just to close out the loop for anyone happens to read this thread.   I finally fixed the problem by re-installing the restricted modules for 2.6.20-16.   Here is what I learned:

If nVidia driver is giving you trouble and you 'need' to get into GDM, you can simply change the driver definition in xorg.conf file from 'nvidia' to 'nv'.   Here is how:

(I'm using root terminal, if you are using regular terminal then you need to add 'sudo' in front of every command except 'cd')

```
cd /etc/X11/
cp xorg.conf xorg.conf.backup
vi xorg.conf
```

Then find the following section:

S```
ection "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7300 GT]"
    Driver         "nvidia"
    Busid          "PCI:1:0:0"
EndSection
```

and change it to:

```
Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7300 GT]"
    Driver         "[COLOR="Red"]nv[/COLOR]"
    Busid          "PCI:1:0:0"
EndSection
```

You now should be able to boot into the new kernel in normal mode.   NOTE: since you are now not using restricted module, your OpenGL application (such as the screen saver) will not work properly, and you refresh rate may be limited.

To permanently fix the driver issue, you need to first boot into the recovery mode from GRUB menu.    At command line, do the following:

```
apt-get update
apt-get install --reinstall linux-restricted-modules-2.6.20-16-generic
```

now you can boot into the new kernel normally :)

Hope this help some frustrated people out there -- Ubuntu is great, but without the helping people in this forum, Ubuntu is nothing!

Enjoy!

---

