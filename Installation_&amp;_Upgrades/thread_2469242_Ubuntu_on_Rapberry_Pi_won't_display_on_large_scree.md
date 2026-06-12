---
title: "Ubuntu on Rapberry Pi won't display on large screen TV"
date: 2021-11-23
forum: Installation &amp; Upgrades
---

### Post by Yoodle on 2021-11-23
I have setup Ubutnu Desktop v21.10 on my Rapberry Pi 4.
On my 24" monitor using an HDMI cable, it works fine.
I'd like to set it up on my 65" Samsung TV, but the TV is not recognizing it.  When I boot the Pi, the rainbow screen appears on the TV, but then it goes black, and the TV says it cannot find the source.

I've tried adding these settings to /boot/firmware/config.txt in various combinations, but none of them have helped:
disable_overscan=1
hdmi_drive=2
hdmi_force_hotplug=1
hdmi_enable_4kp60=1

I was previously running the Raspberry PI OS with this same hardware and TV, and it worked, so I don't think it's a hardware issue.

Any ideas for anything else I can try?

---

### Post by MAFoElffen on 2021-11-26
This thread and this post may help you... Instead of retyping and reposting everything I answered there. 
[https://ubuntuforums.org/showthread.php?t=2466200&p=14055389#post14055389](https://ubuntuforums.org/showthread.php?t=2466200&p=14055389#post14055389)

Read through it and ask if you have any questions... it continued on past that.

What is boils down to, is that the Raspberry Pi cannot always find what is the preferred mode in a TV's EDID table... It can possibly show a lot of different resolution ranges, but that is not always appropriate for the Display. It tries... But sometimes fails and selects something that is out of range of the display.

This is how I setup my own my own Raspberry Pi4 8GB...

---

### Post by Yoodle on 2021-12-01
Thanks for the response.  I checked out the other thread you referenced, and it looks like he was having a problem very similar to mine, but it doesn't look like he ever resolved it.  I tried some of the different HDMI settings you had listed in your usercfg.txt, but none of the ones I tried worked.

Do you have anything else I can try?  Should I continue posting here or add to the other thread?

---

### Post by MAFoElffen on 2021-12-02
What is the Brand and model of the Target Large Screen TV?

Still on HDMI1?

What is your target Resolution or mode?

---

### Post by Yoodle on 2021-12-02
My TV is a Samsung 65" NU740D Smart 4K UHD TV

This is the manual for it.  The picture sizes and input signals are listed on page 134.
[https://downloadcenter.samsung.com/content/UM/202011/20201116153100517/KM2ATSCN-3.1.0_EM_Kant-M2_USA_ENG_201023.0.pdf](https://downloadcenter.samsung.com/content/UM/202011/20201116153100517/KM2ATSCN-3.1.0_EM_Kant-M2_USA_ENG_201023.0.pdf)

In case you can't get to it, it lists these input signals for a 16:9 picture size:
HDMI (720p)
HDMI (1080i, 1080p)
HDMI (3840 x 2160p)
HDMI (4096 x 2160p) 
*HDMI (7680 x 4320p @ 30 Hz)

On page 136, it says this:
> Read Before Connecting a Computer (Supported Resolutions)
Check the resolutions supported for PC input signals.
When you connect your TV to a computer, set the computer's video card to one of the standard resolutions listed in 
the tables below or on the next page. The TV will automatically adjust to the resolution you choose. Note that the 
optimal and recommended resolution is 3840 x 2160 at 60 Hz. Choosing a resolution not included in the tables can 
result in a blank screen or just the power indicator turning on. Refer to the user manual of your graphics card for 
compatible resolutions

So, here is my /boot/firmware/config.txt and the beginning part of /boot/firmware/usercfg.txt:
```
[pi4]
max_framebuffers=2

[all]
kernel=vmlinuz
cmdline=cmdline.txt
initramfs initrd.img followkernel

# Enable the audio output, I2C and SPI interfaces on the GPIO header
dtparam=audio=on
dtparam=i2c_arm=on
dtparam=spi=on

# Enable the KMS ("full" KMS) graphics overlay, and allocate 128Mb to the GPU
# memory. The full KMS overlay is required for X11 application support under
# wayland
dtoverlay=vc4-kms-v3d
gpu_mem=128

# Uncomment the following to enable the Raspberry Pi camera module firmware.
# Be warned that there *may* be incompatibilities with the "full" KMS overlay
#start_x=1

# Comment out the following line if the edges of the desktop appear outside
# the edges of your display
disable_overscan=1

# If you have issues with audio, you may try uncommenting the following line
# which forces the HDMI output into HDMI mode instead of DVI (which doesn't
# support audio output)
#hdmi_drive=2

# If you have a CM4, uncomment the following line to enable the USB2 outputs
# on the IO board (assuming your CM4 is plugged into such a board)
#dtoverlay=dwc2,dr_mode=host

# Config settings specific to arm64
arm_64bit=1
dtoverlay=dwc2
include usercfg.txt

```

```
# Place "config.txt" changes (dtparam, dtoverlay, disable_overscan, etc.) in
# this file. Please refer to the README file for a description of the various
# configuration files on the boot partition.
## Custom Slot is hdmi_grpoup=1 & hdmi_mode=65
### For this define, it uses mode 87, which is 1 above the defined modes...
#### Custom mode define ####
# hdmi_cvt=<width> <height> <framerate> <aspect> <margins> <interlace> <rb>
# width        width in pixels
# height       height in pixels
# framerate    framerate in Hz
# aspect       aspect ratio 1=4:3, 2=14:9, 3=16:9, 4=5:4, 5=16:10, 6=15:9
# margins      0=margins disabled, 1=margins enabled
# interlace    0=progressive, 1=interlaced
# rb           0=normal, 1=reduced blanking
###
hdmi_cvt=3840 2160 60 3 0 0 0    # Custom mode definition
#hdmi_group=2
#hdmi_mode=87    #1 mode above defines in AEC
### Normal Mode Sets
#hdmi_group=2     # 0:Autodetect EDID, 1:AEC, 2:DMT
#hdmi_mode=86     # 1366x768, 60Hz,16:9, reduced blanking
### For sound through HDMI ###
#hdmi_drive=1     # hdmi without soundhdmi_group=2     # 0:Autodetect EDID, 1:AEC, 2:DMT
### For sound through HDMI ###
#hdmi_drive=2    # hdmi with sound
```

---

### Post by MAFoElffen on 2021-12-04
In your last post, I saw the link in the config.txt to the usercfg.txt file, but didn't see anything in the usercfg.txt file that was 'un-commented' for it to apply(???) I mean, I can see where you edited that to create a 'custom mode', but it is commented out, so would not have applied it or tried it... Just saying... That's what I see there.

Recommends: Looking at your TV... As a best guess in probabilities, if it were me, I would probably use 
```

hdmi_mode=1
## Set to      4096x2160     60Hz     256:135     Pi 4
hdmi_mode=102

```

---

### Post by Yoodle on 2021-12-04
I had the custom definition uncommented to match what it listed in the TV manual for a PC input:

```
hdmi_cvt=3840 2160 60 3 0 0 0    # Custom mode definition
```

Is that a supported way of defining the mode, or do I need to use one of the standard mode sets?
I also tried using these:

```
hdmi_group=2
hdmi_mode= 96
hdmi_mode= 97
hdmi_mode= 98
hdmi_mode= 99
hdmi_mode= 100
hdmi_mode= 101
```

---

### Post by ActionParsnip on 2021-12-04
Are you using Wayland or Xorg? If it's Xorg then you can make an xorg.conf and setup the display manually (old school)

---

### Post by MAFoElffen on 2021-12-04
@ActionParsnip:
Talking FrameBuffer on Raspberry Pi(x)... I originally thought the same also,... Until i got one. Is sort of a different animal. There is no Grub, and it needs to set the video before it even gets to the Graphical Boot Manager (DM before DE). Wayland and XServer happens after that, so for this device, that is too late.

They have text files that set the onboard chip initialization...

@Yoodle...
??? Yes... But... In my instructions that came with my display, that is for Rasp Pi, Any custom modes, for example, the one suggested for my 13" portable 1920x1080 screen...
```

### For this define, it uses mode 87, which is 1 above the defined modes...
#### Custom mode define ####
# hdmi_cvt=<width> <height> <framerate> <aspect> <margins> <interlace> <rb>
# width        width in pixels
# height       height in pixels
# framerate    framerate in Hz
# aspect       aspect ratio 1=4:3, 2=14:9, 3=16:9, 4=5:4, 5=16:10, 6=15:9
# margins      0=margins disabled, 1=margins enabled
# interlace    0=progressive, 1=interlaced
# rb           0=normal, 1=reduced blanking
###
hdmi_cvt=1920 1080 60 3 0 0 0    # Custom mode definition
hdmi_group=2 
hdmi_mode=87

```
Note that this is documented in my usercfg.txt file that I had linked you to... That is from the manual on my display... The rest of the modes are from the Raspberry Pi Graphics documentation.

Note that the Rasp Pi graphics documentation only has hdmi_group=2 going up to hdmi_mode=86 as presets... So When you define a custom mode, you set it to hdmi_mode=87, which is 'one above' the supported predefined modes...

Which means, what you posted in the second half of post #7... none of those modes are predefined in hdmi_group=2... Those modes are predefined for hdmi_group=1. Is that what you meant? Or maybe you are just a bit confused how that works(?)

Let me make a few examples to try to explain that better. Refere to my own usercfg.txt file that I posted here: [https://ubuntuforums.org/showthread.php?t=2466200&p=14055389#post14055389](https://ubuntuforums.org/showthread.php?t=2466200&p=14055389#post14055389)

Lets pick a mode that is one both hdmi_group's, lets say randomly, out of the blue 'mode 77'...
```

hdmi_group=1
hdmi_mode=77

```
Results in a preset mode resolution of 1080p     100Hz     64:27     on Pi 4...

Whereas:
```

hdmi_group=2
hdmi_mode=77

```
Would be a preset of resolution 2560x1600     75Hz     16:10...

So in your last post, 
> **Yoodle said:**
> 
```

hdmi_group=2
hdmi_mode= 96
hdmi_mode= 97
hdmi_mode= 98
hdmi_mode= 99
hdmi_mode= 100
hdmi_mode= 101
```

- anything from hdmi_group=2 and above hdmi_mode=86, is not predefined.
- you have a spaces between the equals sign and the number. It looks for the first character after that equals sign, so as you had it, it would have failed, even if it had been a lower, valid mode number, just because there are extra spaces in there...
- I know you probably had that written as an example, but if more than one line is uncommented, for the same variable name, then it takes whatever it the last assignment for that variable as the current value of.

Now if you had used
```

hdmi_group=1
hdmi_mode=96   # 2160p     50Hz     16:9     Pi 4
# hdmi_mode=97   # 2160p     60Hz     16:9     Pi 4
# hdmi_mode=98   # 4096x2160     24Hz     256:135     Pi 4
# hdmi_mode=99   # 4096x2160     30Hz     256:135     Pi 4
# hdmi_mode=100   # 4096x2160     50Hz     256:135     Pi 4
# hdmi_mode=101   # 4096x2160     60Hz     256:135     Pi 4

```

EDIT:
Note that in the Raspberry Pi Doc's for Graphics, that
```

hdmi_group=1
hdmi_mode=65

```
...says that mode preset is "CUSTOM"... But I have not been able to get an answer from 'anyone'. 'anywhere' to answer what that actually means.

---

### Post by Yoodle on 2021-12-04
> **ActionParsnip said:**
> Are you using Wayland or Xorg? If it's Xorg then you can make an xorg.conf and setup the display manually (old school)

I'm not sure which one I'm using, I just used the Raspberry Pi imager to create an SD card and booted, according to these instructions:
[https://ubuntu.com/tutorials/how-to-install-ubuntu-desktop-on-raspberry-pi-4#1-overview](https://ubuntu.com/tutorials/how-to-install-ubuntu-desktop-on-raspberry-pi-4#1-overview)

---

### Post by tea for one on 2021-12-04
To establish if you are using Wayland or Xorg, open a terminal and enter:-
```
echo $XDG_SESSION_TYPE
```

---

### Post by Yoodle on 2021-12-04
Sorry, I think in my previous post I put in hdmi_group=2, but when I tried it I was actually using hdmi_group=1.

But, just to make sure, I ran through all the combinations again.  To avoid possible confusion, I removed everything else from my usercfg.txt, except for these settings.  This is an exact copy of the settings I tried in my usercfg.txt:

```
hdmi_cvt=3840 2160 60 3 0 0 0
hdmi_group=2
hdmi_mode=87
```

```
hdmi_cvt=3840 2160 60 3 0 0 0
hdmi_group=1
hdmi_mode=108
```

For this one, I tried values of 96 - 102 for the hdmi_mode:
```
hdmi_group=1
hdmi_mode=102
```


All of these gave the same result.
I read through your post multiple times, so hopefully I'm understanding correctly.  Do the settings I listed above look like they were done correctly?

If it helps at all, here is the /var/log/Xorg.0.log  (this is after booting with the first setting):
```
[    23.794] (--) Log file renamed from "/var/log/Xorg.pid-1147.log" to "/var/log/Xorg.0.log"
[    23.799]
X.Org X Server 1.20.13
X Protocol Version 11, Revision 0
[    23.799] Build Operating System: linux Ubuntu
[    23.799] Current Operating System: Linux ubuntu-pi 5.13.0-1010-raspi #12-Ubuntu SMP PREEMPT Tue Nov 9 15:30:22 UTC 2021 aarch64
[    23.799] Kernel command line: coherent_pool=1M 8250.nr_uarts=0 snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 video=HDMI-A-1:3840x2160M@30 smsc95xx.macaddr=DC:A6:32:C4:25:E1 vc_mem.mem_base=0x3ec00000 vc_mem.mem_size=0x40000000  dwc_otg.lpm_enable=0 console=tty1 root=LABEL=writable rootfstype=ext4 elevator=deadline rootwait fixrtc quiet splash
[    23.799] Build Date: 10 August 2021  09:32:48AM
[    23.800] xorg-server 2:1.20.13-1ubuntu1 (For technical support please see http://www.ubuntu.com/support)
[    23.800] Current version of pixman: 0.40.0
[    23.800]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    23.800] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.801] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  4 17:22:27 2021
[    23.806] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.813] (==) No Layout section.  Using the first Screen section.
[    23.813] (==) No screen section available. Using defaults.
[    23.813] (**) |-->Screen "Default Screen Section" (0)
[    23.813] (**) |   |-->Monitor "<default monitor>"
[    23.814] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    23.814] (==) Automatically adding devices
[    23.814] (==) Automatically enabling devices
[    23.814] (==) Automatically adding GPU devices
[    23.815] (==) Automatically binding GPU devices
[    23.815] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    23.828] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.828]    Entry deleted from font path.
[    23.828] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.828]    Entry deleted from font path.
[    23.828] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.828]    Entry deleted from font path.
[    23.829] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.830]    Entry deleted from font path.
[    23.830] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.830]    Entry deleted from font path.
[    23.830] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    23.830] (==) ModulePath set to "/usr/lib/xorg/modules"
[    23.830] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.830] (II) Loader magic: 0xaaaab9d0e010
[    23.830] (II) Module ABI versions:
[    23.830]    X.Org ANSI C Emulation: 0.4
[    23.830]    X.Org Video Driver: 24.1
[    23.830]    X.Org XInput driver : 24.1
[    23.830]    X.Org Server Extension : 10.0
[    23.833] (++) using VT number 2

[    23.841] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_33
[    23.848] (II) xfree86: Adding drm device (/dev/dri/card1)
[    23.850] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 12 paused 0
[    23.851] (II) xfree86: Adding drm device (/dev/dri/card0)
[    23.854] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 13 paused 0
[    23.856] (II) no primary bus or device found
[    23.856]    falling back to /sys/devices/platform/gpu/drm/card1
[    23.857] (II) LoadModule: "glx"
[    23.860] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.870] (II) Module glx: vendor="X.Org Foundation"
[    23.870]    compiled for 1.20.13, module version = 1.0.0
[    23.870]    ABI class: X.Org Server Extension, version 10.0
[    23.870] (==) Matched modesetting as autoconfigured driver 0
[    23.870] (==) Matched fbdev as autoconfigured driver 1
[    23.871] (==) Assigned the driver to the xf86ConfigLayout
[    23.871] (II) LoadModule: "modesetting"
[    23.872] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.877] (II) Module modesetting: vendor="X.Org Foundation"
[    23.877]    compiled for 1.20.13, module version = 1.20.13
[    23.877]    Module class: X.Org Video Driver
[    23.877]    ABI class: X.Org Video Driver, version 24.1
[    23.877] (II) LoadModule: "fbdev"
[    23.878] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.880] (II) Module fbdev: vendor="X.Org Foundation"
[    23.880]    compiled for 1.20.13, module version = 0.5.0
[    23.880]    Module class: X.Org Video Driver
[    23.880]    ABI class: X.Org Video Driver, version 24.1
[    23.880] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.880] (II) FBDEV: driver for framebuffer: fbdev
[    23.881] (II) modeset(0): using drv /dev/dri/card1
[    23.881] (WW) Falling back to old probe method for fbdev
[    23.881] (II) Loading sub module "fbdevhw"
[    23.881] (II) LoadModule: "fbdevhw"
[    23.882] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.883] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.884]    compiled for 1.20.13, module version = 0.0.2
[    23.884]    ABI class: X.Org Video Driver, version 24.1
[    23.884] (EE) open /dev/fb0: No such file or directory
[    23.884] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[    23.884] (II) modeset(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    23.884] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[    23.885] (==) modeset(0): RGB weight 888
[    23.885] (==) modeset(0): Default visual is TrueColor
[    23.885] (II) Loading sub module "glamoregl"
[    23.885] (II) LoadModule: "glamoregl"
[    23.885] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    23.900] (II) Module glamoregl: vendor="X.Org Foundation"
[    23.900]    compiled for 1.20.13, module version = 1.0.1
[    23.901]    ABI class: X.Org ANSI C Emulation, version 0.4
[    25.648] (II) modeset(0): glamor X acceleration enabled on V3D 4.2
[    25.653] (II) modeset(0): glamor initialized
[    25.654] (II) modeset(0): Output HDMI-1 has no monitor section
[    25.655] (II) modeset(0): Output HDMI-2 has no monitor section
[    25.676] (II) modeset(0): EDID for output HDMI-1
[    25.676] (II) modeset(0): EDID for output HDMI-2
[    25.676] (II) modeset(0): Output HDMI-1 disconnected
[    25.676] (II) modeset(0): Output HDMI-2 disconnected
[    25.676] (WW) modeset(0): No outputs definitely connected, trying again...
[    25.676] (II) modeset(0): Output HDMI-1 disconnected
[    25.676] (II) modeset(0): Output HDMI-2 disconnected
[    25.676] (WW) modeset(0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[    25.676] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.677] (==) modeset(0): DPI set to (96, 96)
[    25.677] (II) Loading sub module "fb"
[    25.677] (II) LoadModule: "fb"
[    25.680] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.685] (II) Module fb: vendor="X.Org Foundation"
[    25.685]    compiled for 1.20.13, module version = 1.0.0
[    25.685]    ABI class: X.Org ANSI C Emulation, version 0.4
[    25.685] (II) UnloadModule: "fbdev"
[    25.685] (II) Unloading fbdev
[    25.685] (II) UnloadSubModule: "fbdevhw"
[    25.685] (II) Unloading fbdevhw
[    25.880] (==) modeset(0): Backing store enabled
[    25.880] (==) modeset(0): Silken mouse enabled
[    25.937] (II) modeset(0): Initializing kms color map for depth 24, 8 bpc.
[    25.937] (==) modeset(0): DPMS enabled
[    25.938] (II) modeset(0): [DRI2] Setup complete
[    25.938] (II) modeset(0): [DRI2]   DRI driver: vc4
[    25.938] (II) modeset(0): [DRI2]   VDPAU driver: vc4
[    25.938] (II) Initializing extension Generic Event Extension
[    25.939] (II) Initializing extension SHAPE
[    25.939] (II) Initializing extension MIT-SHM
[    25.940] (II) Initializing extension XInputExtension
[    25.943] (II) Initializing extension XTEST
[    25.943] (II) Initializing extension BIG-REQUESTS
[    25.944] (II) Initializing extension SYNC
[    25.944] (II) Initializing extension XKEYBOARD
[    25.945] (II) Initializing extension XC-MISC
[    25.945] (II) Initializing extension SECURITY
[    25.946] (II) Initializing extension XFIXES
[    25.946] (II) Initializing extension RENDER
[    25.947] (II) Initializing extension RANDR
[    25.948] (II) Initializing extension COMPOSITE
[    25.948] (II) Initializing extension DAMAGE
[    25.949] (II) Initializing extension MIT-SCREEN-SAVER
[    25.949] (II) Initializing extension DOUBLE-BUFFER
[    25.950] (II) Initializing extension RECORD
[    25.950] (II) Initializing extension DPMS
[    25.950] (II) Initializing extension Present
[    25.951] (II) Initializing extension DRI3
[    25.951] (II) Initializing extension X-Resource
[    25.952] (II) Initializing extension XVideo
[    25.952] (II) Initializing extension XVideo-MotionCompensation
[    25.953] (II) Initializing extension SELinux
[    25.953] (II) SELinux: Disabled on system
[    25.953] (II) Initializing extension GLX
[    26.441] (II) AIGLX: Loaded and initialized vc4
[    26.441] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.441] (II) Initializing extension XFree86-VidModeExtension
[    26.442] (II) Initializing extension XFree86-DGA
[    26.443] (II) Initializing extension XFree86-DRI
[    26.447] (II) Initializing extension DRI2
[    26.462] (II) modeset(0): Damage tracking initialized
[    27.320] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event0)
[    27.320] (**) USB USB Keykoard: Applying InputClass "libinput keyboard catchall"
[    27.320] (II) LoadModule: "libinput"
[    27.322] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    27.330] (II) Module libinput: vendor="X.Org Foundation"
[    27.330]    compiled for 1.20.13, module version = 1.1.0
[    27.330]    Module class: X.Org XInput Driver
[    27.330]    ABI class: X.Org XInput driver, version 24.1
[    27.331] (II) Using input driver 'libinput' for 'USB USB Keykoard'
[    27.334] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 26 paused 0
[    27.334] (**) USB USB Keykoard: always reports core events
[    27.335] (**) Option "Device" "/dev/input/event0"
[    27.335] (**) Option "_source" "server/udev"
[    27.375] (II) event0  - USB USB Keykoard: is tagged by udev as: Keyboard
[    27.375] (II) event0  - USB USB Keykoard: device is a keyboard
[    27.376] (II) event0  - USB USB Keykoard: device removed
[    27.377] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:1A2C:0002.0001/input/input0/event0"
[    27.377] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 6)
[    27.377] (**) Option "xkb_model" "pc105"
[    27.377] (**) Option "xkb_layout" "us"
[    27.388] (II) event0  - USB USB Keykoard: is tagged by udev as: Keyboard
[    27.389] (II) event0  - USB USB Keykoard: device is a keyboard
[    27.397] (II) config/udev: Adding input device USB USB Keykoard Consumer Control (/dev/input/event1)
[    27.397] (**) USB USB Keykoard Consumer Control: Applying InputClass "libinput keyboard catchall"
[    27.397] (II) Using input driver 'libinput' for 'USB USB Keykoard Consumer Control'
[    27.401] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 29 paused 0
[    27.401] (**) USB USB Keykoard Consumer Control: always reports core events
[    27.401] (**) Option "Device" "/dev/input/event1"
[    27.401] (**) Option "_source" "server/udev"
[    27.411] (II) event1  - USB USB Keykoard Consumer Control: is tagged by udev as: Keyboard
[    27.412] (II) event1  - USB USB Keykoard Consumer Control: device is a keyboard
[    27.413] (II) event1  - USB USB Keykoard Consumer Control: device removed
[    27.413] (II) libinput: USB USB Keykoard Consumer Control: needs a virtual subdevice
[    27.413] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1A2C:0002.0002/input/input1/event1"
[    27.414] (II) XINPUT: Adding extended input device "USB USB Keykoard Consumer Control" (type: MOUSE, id 7)
[    27.414] (**) Option "AccelerationScheme" "none"
[    27.414] (**) USB USB Keykoard Consumer Control: (accel) selected scheme none/0
[    27.414] (**) USB USB Keykoard Consumer Control: (accel) acceleration factor: 2.000
[    27.414] (**) USB USB Keykoard Consumer Control: (accel) acceleration threshold: 4
[    27.424] (II) event1  - USB USB Keykoard Consumer Control: is tagged by udev as: Keyboard
[    27.425] (II) event1  - USB USB Keykoard Consumer Control: device is a keyboard
[    27.432] (II) config/udev: Adding input device USB USB Keykoard System Control (/dev/input/event2)
[    27.433] (**) USB USB Keykoard System Control: Applying InputClass "libinput keyboard catchall"
[    27.433] (II) Using input driver 'libinput' for 'USB USB Keykoard System Control'
[    27.436] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 30 paused 0
[    27.438] (**) USB USB Keykoard System Control: always reports core events
[    27.438] (**) Option "Device" "/dev/input/event2"
[    27.439] (**) Option "_source" "server/udev"
[    27.449] (II) event2  - USB USB Keykoard System Control: is tagged by udev as: Keyboard
[    27.449] (II) event2  - USB USB Keykoard System Control: device is a keyboard
[    27.450] (II) event2  - USB USB Keykoard System Control: device removed
[    27.450] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1A2C:0002.0002/input/input2/event2"
[    27.450] (II) XINPUT: Adding extended input device "USB USB Keykoard System Control" (type: KEYBOARD, id 8)
[    27.450] (**) Option "xkb_model" "pc105"
[    27.450] (**) Option "xkb_layout" "us"
[    27.461] (II) event2  - USB USB Keykoard System Control: is tagged by udev as: Keyboard
[    27.462] (II) event2  - USB USB Keykoard System Control: device is a keyboard
[    27.469] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
[    27.469] (**) Logitech USB Optical Mouse: Applying InputClass "libinput pointer catchall"
[    27.469] (II) Using input driver 'libinput' for 'Logitech USB Optical Mouse'
[    27.533] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 31 paused 0
[    27.533] (**) Logitech USB Optical Mouse: always reports core events
[    27.534] (**) Option "Device" "/dev/input/event3"
[    27.534] (**) Option "_source" "server/udev"
[    27.543] (II) event3  - Logitech USB Optical Mouse: is tagged by udev as: Mouse
[    27.544] (II) event3  - Logitech USB Optical Mouse: device is a pointer
[    27.544] (II) event3  - Logitech USB Optical Mouse: device removed
[    27.544] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.4/1-1.4:1.0/0003:046D:C00C.0003/input/input3/event3"
[    27.544] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 9)
[    27.545] (**) Option "AccelerationScheme" "none"
[    27.545] (**) Logitech USB Optical Mouse: (accel) selected scheme none/0
[    27.545] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    27.545] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    27.554] (II) event3  - Logitech USB Optical Mouse: is tagged by udev as: Mouse
[    27.555] (II) event3  - Logitech USB Optical Mouse: device is a pointer
[    27.561] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    27.561] (II) No input driver specified, ignoring this device.
[    27.561] (II) This device may have been added with another device file.
[    27.565] (II) config/udev: Adding input device vc4 (/dev/input/event4)
[    27.565] (**) vc4: Applying InputClass "libinput keyboard catchall"
[    27.565] (II) Using input driver 'libinput' for 'vc4'
[    27.568] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 32 paused 0
[    27.569] (**) vc4: always reports core events
[    27.569] (**) Option "Device" "/dev/input/event4"
[    27.569] (**) Option "_source" "server/udev"
[    27.574] (II) event4  - vc4: is tagged by udev as: Keyboard Pointingstick
[    27.575] (II) event4  - vc4: device is a pointer
[    27.575] (II) event4  - vc4: device is a keyboard
[    27.576] (II) event4  - vc4: device removed
[    27.577] (II) libinput: vc4: needs a virtual subdevice
[    27.577] (**) Option "config_info" "udev:/sys/devices/platform/soc/fef00700.hdmi/rc/rc0/input5/event4"
[    27.577] (II) XINPUT: Adding extended input device "vc4" (type: MOUSE, id 10)
[    27.577] (**) Option "AccelerationScheme" "none"
[    27.577] (**) vc4: (accel) selected scheme none/0
[    27.577] (**) vc4: (accel) acceleration factor: 2.000
[    27.578] (**) vc4: (accel) acceleration threshold: 4
[    27.582] (II) event4  - vc4: is tagged by udev as: Keyboard Pointingstick
[    27.583] (II) event4  - vc4: device is a pointer
[    27.583] (II) event4  - vc4: device is a keyboard
[    27.587] (II) config/udev: Adding input device vc4 (/dev/input/event5)
[    27.587] (**) vc4: Applying InputClass "libinput keyboard catchall"
[    27.587] (II) Using input driver 'libinput' for 'vc4'
[    27.590] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 33 paused 0
[    27.590] (**) vc4: always reports core events
[    27.590] (**) Option "Device" "/dev/input/event5"
[    27.590] (**) Option "_source" "server/udev"
[    27.595] (II) event5  - vc4: is tagged by udev as: Keyboard Pointingstick
[    27.596] (II) event5  - vc4: device is a pointer
[    27.596] (II) event5  - vc4: device is a keyboard
[    27.599] (II) event5  - vc4: device removed
[    27.599] (II) libinput: vc4: needs a virtual subdevice
[    27.599] (**) Option "config_info" "udev:/sys/devices/platform/soc/fef05700.hdmi/rc/rc1/input6/event5"
[    27.599] (II) XINPUT: Adding extended input device "vc4" (type: MOUSE, id 11)
[    27.600] (**) Option "AccelerationScheme" "none"
[    27.600] (**) vc4: (accel) selected scheme none/0
[    27.600] (**) vc4: (accel) acceleration factor: 2.000
[    27.600] (**) vc4: (accel) acceleration threshold: 4
[    27.605] (II) event5  - vc4: is tagged by udev as: Keyboard Pointingstick
[    27.606] (II) event5  - vc4: device is a pointer
[    27.606] (II) event5  - vc4: device is a keyboard
[    27.823] (**) USB USB Keykoard Consumer Control: Applying InputClass "libinput keyboard catchall"
[    27.823] (II) Using input driver 'libinput' for 'USB USB Keykoard Consumer Control'
[    27.823] (II) systemd-logind: returning pre-existing fd for /dev/input/event1 13:65
[    27.823] (**) USB USB Keykoard Consumer Control: always reports core events
[    27.823] (**) Option "Device" "/dev/input/event1"
[    27.823] (**) Option "_source" "_driver/libinput"
[    27.823] (II) libinput: USB USB Keykoard Consumer Control: is a virtual subdevice
[    27.823] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1A2C:0002.0002/input/input1/event1"
[    27.824] (II) XINPUT: Adding extended input device "USB USB Keykoard Consumer Control" (type: KEYBOARD, id 12)
[    27.824] (**) Option "xkb_model" "pc105"
[    27.824] (**) Option "xkb_layout" "us"
[    27.825] (**) vc4: Applying InputClass "libinput keyboard catchall"
[    27.825] (II) Using input driver 'libinput' for 'vc4'
[    27.825] (II) systemd-logind: returning pre-existing fd for /dev/input/event4 13:68
[    27.825] (**) vc4: always reports core events
[    27.825] (**) Option "Device" "/dev/input/event4"
[    27.825] (**) Option "_source" "_driver/libinput"
[    27.825] (II) libinput: vc4: is a virtual subdevice
[    27.825] (**) Option "config_info" "udev:/sys/devices/platform/soc/fef00700.hdmi/rc/rc0/input5/event4"
[    27.826] (II) XINPUT: Adding extended input device "vc4" (type: KEYBOARD, id 13)
[    27.826] (**) Option "xkb_model" "pc105"
[    27.826] (**) Option "xkb_layout" "us"
[    27.826] (**) vc4: Applying InputClass "libinput keyboard catchall"
[    27.827] (II) Using input driver 'libinput' for 'vc4'
[    27.827] (II) systemd-logind: returning pre-existing fd for /dev/input/event5 13:69
[    27.827] (**) vc4: always reports core events
[    27.827] (**) Option "Device" "/dev/input/event5"
[    27.827] (**) Option "_source" "_driver/libinput"
[    27.827] (II) libinput: vc4: is a virtual subdevice
[    27.827] (**) Option "config_info" "udev:/sys/devices/platform/soc/fef05700.hdmi/rc/rc1/input6/event5"
[    27.827] (II) XINPUT: Adding extended input device "vc4" (type: KEYBOARD, id 14)
[    27.828] (**) Option "xkb_model" "pc105"
[    27.828] (**) Option "xkb_layout" "us"
```

---

### Post by MAFoElffen on 2021-12-04
Yes. Those modes were correct...
> **Yoodle said:**
> If it helps at all, here is the /var/log/Xorg.0.log  (this is after booting with the first setting):
```

[    25.676] (II) modeset(0): EDID for output HDMI-1
[    25.676] (II) modeset(0): EDID for output HDMI-2
[    25.676] (II) modeset(0): Output HDMI-1 disconnected
[    25.676] (II) modeset(0): Output HDMI-2 disconnected
[    25.676] (WW) modeset(0): No outputs definitely connected, trying again...
[    25.676] (II) modeset(0): Output HDMI-1 disconnected
[    25.676] (II) modeset(0): Output HDMI-2 disconnected
[    25.676] (WW) modeset(0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[    25.676] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.677] (==) modeset(0): DPI set to (96, 96)
[    25.677] (II) Loading sub module "fb"
[    25.677] (II) LoadModule: "fb"

```

That is the part that worries me... That it does NOT see anything connected.

Here is mine for comparison... Heading off to work, so cannot go into it in more detail yet...
```

[    40.224] 
X.Org X Server 1.20.11
X Protocol Version 11, Revision 0
[    40.224] Build Operating System: linux Ubuntu
[    40.224] Current Operating System: Linux ubuntu 5.4.0-1046-raspi #50-Ubuntu SMP PREEMPT Thu Oct 28 05:32:10 UTC 2021 aarch64
[    40.224] Kernel command line:  coherent_pool=1M 8250.nr_uarts=1 snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 bcm2708_fb.fbwidth=1920 bcm2708_fb.fbheight=1080 bcm2708_fb.fbswap=1 smsc95xx.macaddr=DC:A6:32:ED:0B:03 vc_mem.mem_base=0x3ec00000 vc_mem.mem_size=0x40000000  net.ifnames=0 dwc_otg.lpm_enable=0 console=ttyS0,115200 console=tty1 root=LABEL=writable rootfstype=ext4 elevator=deadline rootwait fixrtc quiet splash
[    40.224] Build Date: 06 July 2021  10:17:51AM
[    40.224] xorg-server 2:1.20.11-1ubuntu1~20.04.2 (For technical support please see http://www.ubuntu.com/support) 
[    40.224] Current version of pixman: 0.38.4
[    40.224]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    40.224] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    40.225] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 30 15:11:14 2021
[    40.250] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    40.262] (==) No Layout section.  Using the first Screen section.
[    40.262] (==) No screen section available. Using defaults.
[    40.262] (**) |-->Screen "Default Screen Section" (0)
[    40.262] (**) |   |-->Monitor "<default monitor>"
[    40.269] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    40.269] (==) Automatically adding devices
[    40.269] (==) Automatically enabling devices
[    40.269] (==) Automatically adding GPU devices
[    40.269] (==) Automatically binding GPU devices
[    40.269] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    40.290] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    40.290]     Entry deleted from font path.
[    40.290] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    40.290]     Entry deleted from font path.
[    40.290] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    40.290]     Entry deleted from font path.
[    40.293] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    40.293]     Entry deleted from font path.
[    40.293] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    40.293]     Entry deleted from font path.
[    40.293] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    40.293] (==) ModulePath set to "/usr/lib/xorg/modules"
[    40.293] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    40.293] (II) Loader magic: 0xaaaad95d9010
[    40.293] (II) Module ABI versions:
[    40.293]     X.Org ANSI C Emulation: 0.4
[    40.293]     X.Org Video Driver: 24.1
[    40.293]     X.Org XInput driver : 24.1
[    40.293]     X.Org Server Extension : 10.0
[    40.296] (++) using VT number 7

[    40.296] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    40.298] (II) no primary bus or device found
[    40.298] (II) LoadModule: "glx"
[    40.313] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    40.416] (II) Module glx: vendor="X.Org Foundation"
[    40.416]     compiled for 1.20.11, module version = 1.0.0
[    40.416]     ABI class: X.Org Server Extension, version 10.0
[    40.416] (==) Matched modesetting as autoconfigured driver 0
[    40.416] (==) Matched fbdev as autoconfigured driver 1
[    40.416] (==) Assigned the driver to the xf86ConfigLayout
[    40.416] (II) LoadModule: "modesetting"
[    40.417] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    40.425] (II) Module modesetting: vendor="X.Org Foundation"
[    40.425]     compiled for 1.20.11, module version = 1.20.11
[    40.425]     Module class: X.Org Video Driver
[    40.425]     ABI class: X.Org Video Driver, version 24.1
[    40.425] (II) LoadModule: "fbdev"
[    40.426] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    40.438] (II) Module fbdev: vendor="X.Org Foundation"
[    40.438]     compiled for 1.20.1, module version = 0.5.0
[    40.438]     Module class: X.Org Video Driver
[    40.438]     ABI class: X.Org Video Driver, version 24.0
[    40.438] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    40.438] (II) FBDEV: driver for framebuffer: fbdev
[    40.451] (WW) Falling back to old probe method for modesetting
[    40.452] (EE) open /dev/dri/card0: No such file or directory
[    40.452] (WW) Falling back to old probe method for fbdev
[    40.452] (II) Loading sub module "fbdevhw"
[    40.452] (II) LoadModule: "fbdevhw"
[    40.452] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    40.456] (II) Module fbdevhw: vendor="X.Org Foundation"
[    40.456]     compiled for 1.20.11, module version = 0.0.2
[    40.456]     ABI class: X.Org Video Driver, version 24.1
[    40.456] (II) FBDEV(0): using default device
[    40.456] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[    40.456] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    40.456] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    40.456] (==) FBDEV(0): RGB weight 888
[    40.456] (==) FBDEV(0): Default visual is TrueColor
[    40.456] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    40.456] (II) FBDEV(0): hardware: simple (video memory: 8100kB)
[    40.456] (DB) xf86MergeOutputClassOptions unsupported bus type 0
[    40.456] (II) FBDEV(0): checking modes against framebuffer device...
[    40.457] (II) FBDEV(0): checking modes against monitor...
[    40.457] (II) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    40.457] (**) FBDEV(0):  Built-in mode "current"
[    40.457] (==) FBDEV(0): DPI set to (96, 96)
[    40.457] (II) Loading sub module "fb"
[    40.457] (II) LoadModule: "fb"
[    40.457] (II) Loading /usr/lib/xorg/modules/libfb.so
[    40.468] (II) Module fb: vendor="X.Org Foundation"
[    40.468]     compiled for 1.20.11, module version = 1.0.0
[    40.468]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.469] (**) FBDEV(0): using shadow framebuffer
[    40.469] (II) Loading sub module "shadow"
[    40.469] (II) LoadModule: "shadow"
[    40.469] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    40.476] (II) Module shadow: vendor="X.Org Foundation"
[    40.476]     compiled for 1.20.11, module version = 1.1.0
[    40.476]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.476] (II) UnloadModule: "modesetting"
[    40.476] (II) Unloading modesetting
[    40.477] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    40.506] (==) FBDEV(0): Backing store enabled
[    40.512] (==) FBDEV(0): DPMS enabled
[    40.513] (II) Initializing extension Generic Event Extension
[    40.514] (II) Initializing extension SHAPE
[    40.514] (II) Initializing extension MIT-SHM
[    40.514] (II) Initializing extension XInputExtension
[    40.521] (II) Initializing extension XTEST
[    40.522] (II) Initializing extension BIG-REQUESTS
[    40.522] (II) Initializing extension SYNC
[    40.522] (II) Initializing extension XKEYBOARD
[    40.523] (II) Initializing extension XC-MISC
[    40.523] (II) Initializing extension SECURITY
[    40.524] (II) Initializing extension XFIXES
[    40.524] (II) Initializing extension RENDER
[    40.524] (II) Initializing extension RANDR
[    40.525] (II) Initializing extension COMPOSITE
[    40.528] (II) Initializing extension DAMAGE
[    40.528] (II) Initializing extension MIT-SCREEN-SAVER
[    40.528] (II) Initializing extension DOUBLE-BUFFER
[    40.529] (II) Initializing extension RECORD
[    40.529] (II) Initializing extension DPMS
[    40.529] (II) Initializing extension Present
[    40.530] (II) Initializing extension DRI3
[    40.530] (II) Initializing extension X-Resource
[    40.530] (II) Initializing extension XVideo
[    40.530] (II) Initializing extension XVideo-MotionCompensation
[    40.530] (II) Initializing extension SELinux
[    40.531] (II) SELinux: Disabled on system
[    40.531] (II) Initializing extension GLX
[    40.531] (II) AIGLX: Screen 0 is not DRI2 capable
[    42.024] (II) IGLX: Loaded and initialized swrast
[    42.024] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    42.024] (II) Initializing extension XFree86-VidModeExtension
[    42.024] (II) Initializing extension XFree86-DGA
[    42.025] (II) Initializing extension XFree86-DRI
[    42.026] (II) Initializing extension DRI2
[    42.426] (II) config/udev: Adding input device   mini keyboard (/dev/input/event0)
[    42.427] (**)   mini keyboard: Applying InputClass "libinput keyboard catchall"
[    42.427] (II) LoadModule: "libinput"
[    42.428] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    42.453] (II) Module libinput: vendor="X.Org Foundation"
[    42.453]     compiled for 1.20.4, module version = 0.29.0
[    42.453]     Module class: X.Org XInput Driver
[    42.453]     ABI class: X.Org XInput driver, version 24.1
[    42.453] (II) Using input driver 'libinput' for '  mini keyboard'
[    42.453] (**)   mini keyboard: always reports core events
[    42.453] (**) Option "Device" "/dev/input/event0"
[    42.455] (**) Option "_source" "server/udev"
[    42.496] (II) event0  -   mini keyboard: is tagged by udev as: Keyboard
[    42.496] (II) event0  -   mini keyboard: device is a keyboard
[    42.497] (II) event0  -   mini keyboard: device removed
[    42.520] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:1997:2433.0001/input/input0/event0"
[    42.520] (II) XINPUT: Adding extended input device "  mini keyboard" (type: KEYBOARD, id 6)
[    42.520] (**) Option "xkb_model" "pc105"
[    42.520] (**) Option "xkb_layout" "us"
[    42.529] (II) event0  -   mini keyboard: is tagged by udev as: Keyboard
[    42.529] (II) event0  -   mini keyboard: device is a keyboard
[    42.534] (II) config/udev: Adding input device   mini keyboard Mouse (/dev/input/event1)
[    42.534] (**)   mini keyboard Mouse: Applying InputClass "libinput pointer catchall"
[    42.534] (II) Using input driver 'libinput' for '  mini keyboard Mouse'
[    42.534] (**)   mini keyboard Mouse: always reports core events
[    42.534] (**) Option "Device" "/dev/input/event1"
[    42.534] (**) Option "_source" "server/udev"
[    42.544] (II) event1  -   mini keyboard Mouse: is tagged by udev as: Mouse
[    42.544] (II) event1  -   mini keyboard Mouse: device is a pointer
[    42.545] (II) event1  -   mini keyboard Mouse: device removed
[    42.584] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1997:2433.0002/input/input1/event1"
[    42.584] (II) XINPUT: Adding extended input device "  mini keyboard Mouse" (type: MOUSE, id 7)
[    42.584] (**) Option "AccelerationScheme" "none"
[    42.584] (**)   mini keyboard Mouse: (accel) selected scheme none/0
[    42.584] (**)   mini keyboard Mouse: (accel) acceleration factor: 2.000
[    42.584] (**)   mini keyboard Mouse: (accel) acceleration threshold: 4
[    42.593] (II) event1  -   mini keyboard Mouse: is tagged by udev as: Mouse
[    42.594] (II) event1  -   mini keyboard Mouse: device is a pointer
[    42.599] (II) config/udev: Adding input device   mini keyboard Mouse (/dev/input/mouse0)
[    42.599] (II) No input driver specified, ignoring this device.
[    42.599] (II) This device may have been added with another device file.
[    42.605] (II) config/udev: Adding input device   mini keyboard System Control (/dev/input/event2)
[    42.605] (**)   mini keyboard System Control: Applying InputClass "libinput keyboard catchall"
[    42.605] (II) Using input driver 'libinput' for '  mini keyboard System Control'
[    42.605] (**)   mini keyboard System Control: always reports core events
[    42.605] (**) Option "Device" "/dev/input/event2"
[    42.605] (**) Option "_source" "server/udev"
[    42.614] (II) event2  -   mini keyboard System Control: is tagged by udev as: Keyboard
[    42.614] (II) event2  -   mini keyboard System Control: device is a keyboard
[    42.614] (II) event2  -   mini keyboard System Control: device removed
[    42.644] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1997:2433.0002/input/input2/event2"
[    42.644] (II) XINPUT: Adding extended input device "  mini keyboard System Control" (type: KEYBOARD, id 8)
[    42.644] (**) Option "xkb_model" "pc105"
[    42.644] (**) Option "xkb_layout" "us"
[    42.653] (II) event2  -   mini keyboard System Control: is tagged by udev as: Keyboard
[    42.653] (II) event2  -   mini keyboard System Control: device is a keyboard
[    42.659] (II) config/udev: Adding input device   mini keyboard Consumer Control (/dev/input/event3)
[    42.659] (**)   mini keyboard Consumer Control: Applying InputClass "libinput keyboard catchall"
[    42.659] (II) Using input driver 'libinput' for '  mini keyboard Consumer Control'
[    42.659] (**)   mini keyboard Consumer Control: always reports core events
[    42.659] (**) Option "Device" "/dev/input/event3"
[    42.659] (**) Option "_source" "server/udev"
[    42.668] (II) event3  -   mini keyboard Consumer Control: is tagged by udev as: Keyboard
[    42.668] (II) event3  -   mini keyboard Consumer Control: device is a keyboard
[    42.669] (II) event3  -   mini keyboard Consumer Control: device removed
[    42.692] (II) libinput:   mini keyboard Consumer Control: needs a virtual subdevice
[    42.692] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1997:2433.0002/input/input3/event3"
[    42.692] (II) XINPUT: Adding extended input device "  mini keyboard Consumer Control" (type: MOUSE, id 9)
[    42.692] (**) Option "AccelerationScheme" "none"
[    42.692] (**)   mini keyboard Consumer Control: (accel) selected scheme none/0
[    42.692] (**)   mini keyboard Consumer Control: (accel) acceleration factor: 2.000
[    42.692] (**)   mini keyboard Consumer Control: (accel) acceleration threshold: 4
[    42.701] (II) event3  -   mini keyboard Consumer Control: is tagged by udev as: Keyboard
[    42.702] (II) event3  -   mini keyboard Consumer Control: device is a keyboard
[    42.708] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
[    42.708] (**) Logitech USB Optical Mouse: Applying InputClass "libinput pointer catchall"
[    42.708] (II) Using input driver 'libinput' for 'Logitech USB Optical Mouse'
[    42.708] (**) Logitech USB Optical Mouse: always reports core events
[    42.708] (**) Option "Device" "/dev/input/event4"
[    42.708] (**) Option "_source" "server/udev"
[    42.716] (II) event4  - Logitech USB Optical Mouse: is tagged by udev as: Mouse
[    42.716] (II) event4  - Logitech USB Optical Mouse: device is a pointer
[    42.716] (II) event4  - Logitech USB Optical Mouse: device removed
[    42.760] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.4/1-1.4:1.0/0003:046D:C077.0003/input/input4/event4"
[    42.760] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 10)
[    42.760] (**) Option "AccelerationScheme" "none"
[    42.761] (**) Logitech USB Optical Mouse: (accel) selected scheme none/0
[    42.761] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    42.761] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    42.767] (II) event4  - Logitech USB Optical Mouse: is tagged by udev as: Mouse
[    42.768] (II) event4  - Logitech USB Optical Mouse: device is a pointer
[    42.772] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
[    42.773] (II) No input driver specified, ignoring this device.
[    42.773] (II) This device may have been added with another device file.
[    42.934] (**)   mini keyboard Consumer Control: Applying InputClass "libinput keyboard catchall"
[    42.934] (II) Using input driver 'libinput' for '  mini keyboard Consumer Control'
[    42.934] (**)   mini keyboard Consumer Control: always reports core events
[    42.934] (**) Option "Device" "/dev/input/event3"
[    42.934] (**) Option "_source" "_driver/libinput"
[    42.934] (II) libinput:   mini keyboard Consumer Control: is a virtual subdevice
[    42.934] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1997:2433.0002/input/input3/event3"
[    42.934] (II) XINPUT: Adding extended input device "  mini keyboard Consumer Control" (type: KEYBOARD, id 11)
[    42.934] (**) Option "xkb_model" "pc105"
[    42.934] (**) Option "xkb_layout" "us"
[   203.056] (II) config/udev: Adding input device ZealPC Zeal60 System Control (/dev/input/event6)
[   203.057] (**) ZealPC Zeal60 System Control: Applying InputClass "libinput keyboard catchall"
[   203.057] (II) Using input driver 'libinput' for 'ZealPC Zeal60 System Control'
[   203.057] (**) ZealPC Zeal60 System Control: always reports core events
[   203.057] (**) Option "Device" "/dev/input/event6"
[   203.057] (**) Option "_source" "server/udev"
[   203.068] (II) event6  - ZealPC Zeal60 System Control: is tagged by udev as: Keyboard
[   203.068] (II) event6  - ZealPC Zeal60 System Control: device is a keyboard
[   203.068] (II) event6  - ZealPC Zeal60 System Control: device removed
[   203.088] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:FEED:6060.0005/input/input6/event6"
[   203.088] (II) XINPUT: Adding extended input device "ZealPC Zeal60 System Control" (type: KEYBOARD, id 12)
[   203.088] (**) Option "xkb_model" "pc105"
[   203.088] (**) Option "xkb_layout" "us"
[   203.088] (WW) Option "xkb_variant" requires a string value
[   203.088] (WW) Option "xkb_options" requires a string value
[   203.097] (II) event6  - ZealPC Zeal60 System Control: is tagged by udev as: Keyboard
[   203.097] (II) event6  - ZealPC Zeal60 System Control: device is a keyboard
[   203.102] (II) config/udev: Adding input device ZealPC Zeal60 (/dev/input/event5)
[   203.102] (**) ZealPC Zeal60: Applying InputClass "libinput keyboard catchall"
[   203.102] (II) Using input driver 'libinput' for 'ZealPC Zeal60'
[   203.102] (**) ZealPC Zeal60: always reports core events
[   203.102] (**) Option "Device" "/dev/input/event5"
[   203.102] (**) Option "_source" "server/udev"
[   203.110] (II) event5  - ZealPC Zeal60: is tagged by udev as: Keyboard
[   203.110] (II) event5  - ZealPC Zeal60: device is a keyboard
[   203.111] (II) event5  - ZealPC Zeal60: device removed
[   203.140] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:FEED:6060.0004/input/input5/event5"
[   203.140] (II) XINPUT: Adding extended input device "ZealPC Zeal60" (type: KEYBOARD, id 13)
[   203.140] (**) Option "xkb_model" "pc105"
[   203.140] (**) Option "xkb_layout" "us"
[   203.140] (WW) Option "xkb_variant" requires a string value
[   203.140] (WW) Option "xkb_options" requires a string value
[   203.148] (II) event5  - ZealPC Zeal60: is tagged by udev as: Keyboard
[   203.149] (II) event5  - ZealPC Zeal60: device is a keyboard
[   203.154] (II) config/udev: Adding input device ZealPC Zeal60 (/dev/input/event8)
[   203.154] (**) ZealPC Zeal60: Applying InputClass "libinput keyboard catchall"
[   203.154] (II) Using input driver 'libinput' for 'ZealPC Zeal60'
[   203.154] (**) ZealPC Zeal60: always reports core events
[   203.154] (**) Option "Device" "/dev/input/event8"
[   203.154] (**) Option "_source" "server/udev"
[   203.163] (II) event8  - ZealPC Zeal60: is tagged by udev as: Keyboard
[   203.163] (II) event8  - ZealPC Zeal60: device is a keyboard
[   203.164] (II) event8  - ZealPC Zeal60: device removed
[   203.192] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:FEED:6060.0007/input/input8/event8"
[   203.192] (II) XINPUT: Adding extended input device "ZealPC Zeal60" (type: KEYBOARD, id 14)
[   203.192] (**) Option "xkb_model" "pc105"
[   203.192] (**) Option "xkb_layout" "us"
[   203.192] (WW) Option "xkb_variant" requires a string value
[   203.192] (WW) Option "xkb_options" requires a string value
[   203.201] (II) event8  - ZealPC Zeal60: is tagged by udev as: Keyboard
[   203.201] (II) event8  - ZealPC Zeal60: device is a keyboard
[   203.206] (II) config/udev: Adding input device ZealPC Zeal60 Consumer Control (/dev/input/event7)
[   203.206] (**) ZealPC Zeal60 Consumer Control: Applying InputClass "libinput keyboard catchall"
[   203.206] (II) Using input driver 'libinput' for 'ZealPC Zeal60 Consumer Control'
[   203.206] (**) ZealPC Zeal60 Consumer Control: always reports core events
[   203.206] (**) Option "Device" "/dev/input/event7"
[   203.206] (**) Option "_source" "server/udev"
[   203.214] (II) event7  - ZealPC Zeal60 Consumer Control: is tagged by udev as: Keyboard
[   203.214] (II) event7  - ZealPC Zeal60 Consumer Control: device is a keyboard
[   203.215] (II) event7  - ZealPC Zeal60 Consumer Control: device removed
[   203.244] (II) libinput: ZealPC Zeal60 Consumer Control: needs a virtual subdevice
[   203.244] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:FEED:6060.0005/input/input7/event7"
[   203.245] (II) XINPUT: Adding extended input device "ZealPC Zeal60 Consumer Control" (type: MOUSE, id 15)
[   203.246] (**) Option "AccelerationScheme" "none"
[   203.246] (**) ZealPC Zeal60 Consumer Control: (accel) selected scheme none/0
[   203.246] (**) ZealPC Zeal60 Consumer Control: (accel) acceleration factor: 2.000
[   203.246] (**) ZealPC Zeal60 Consumer Control: (accel) acceleration threshold: 4
[   203.261] (II) event7  - ZealPC Zeal60 Consumer Control: is tagged by udev as: Keyboard
[   203.261] (II) event7  - ZealPC Zeal60 Consumer Control: device is a keyboard
[   203.262] (**) ZealPC Zeal60 Consumer Control: Applying InputClass "libinput keyboard catchall"
[   203.262] (II) Using input driver 'libinput' for 'ZealPC Zeal60 Consumer Control'
[   203.262] (**) ZealPC Zeal60 Consumer Control: always reports core events
[   203.262] (**) Option "Device" "/dev/input/event7"
[   203.262] (**) Option "_source" "_driver/libinput"
[   203.262] (II) libinput: ZealPC Zeal60 Consumer Control: is a virtual subdevice
[   203.262] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:FEED:6060.0005/input/input7/event7"
[   203.263] (II) XINPUT: Adding extended input device "ZealPC Zeal60 Consumer Control" (type: KEYBOARD, id 16)
[   203.263] (**) Option "xkb_model" "pc105"
[   203.263] (**) Option "xkb_layout" "us"
[   203.263] (WW) Option "xkb_variant" requires a string value
[   203.263] (WW) Option "xkb_options" requires a string value
[   205.127] (II) config/udev: removing device ZealPC Zeal60
[   205.127] (II) event5  - ZealPC Zeal60: device removed
[   205.151] (II) UnloadModule: "libinput"
[   205.200] (II) config/udev: removing device ZealPC Zeal60 System Control
[   205.201] (II) event6  - ZealPC Zeal60 System Control: device removed
[   205.220] (II) UnloadModule: "libinput"
[   205.238] (II) config/udev: removing device ZealPC Zeal60 Consumer Control
[   205.239] (II) UnloadModule: "libinput"
[   205.239] (II) config/udev: removing device ZealPC Zeal60 Consumer Control
[   205.240] (II) event7  - ZealPC Zeal60 Consumer Control: device removed
[   205.267] (II) UnloadModule: "libinput"
[   205.295] (II) config/udev: removing device ZealPC Zeal60
[   205.296] (II) event8  - ZealPC Zeal60: device removed
[   205.323] (II) UnloadModule: "libinput"
[   206.100] (II) config/udev: Adding input device ZealPC Zeal60 System Control (/dev/input/event6)
[   206.100] (**) ZealPC Zeal60 System Control: Applying InputClass "libinput keyboard catchall"
[   206.100] (II) Using input driver 'libinput' for 'ZealPC Zeal60 System Control'
[   206.100] (**) ZealPC Zeal60 System Control: always reports core events
[   206.100] (**) Option "Device" "/dev/input/event6"
[   206.100] (**) Option "_source" "server/udev"
[   206.108] (II) event6  - ZealPC Zeal60 System Control: is tagged by udev as: Keyboard
[   206.109] (II) event6  - ZealPC Zeal60 System Control: device is a keyboard
[   206.109] (II) event6  - ZealPC Zeal60 System Control: device removed
[   206.128] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:FEED:6060.0009/input/input10/event6"
[   206.128] (II) XINPUT: Adding extended input device "ZealPC Zeal60 System Control" (type: KEYBOARD, id 12)
[   206.128] (**) Option "xkb_model" "pc105"
[   206.128] (**) Option "xkb_layout" "us"
[   206.128] (WW) Option "xkb_variant" requires a string value
[   206.128] (WW) Option "xkb_options" requires a string value
[   206.138] (II) event6  - ZealPC Zeal60 System Control: is tagged by udev as: Keyboard
[   206.138] (II) event6  - ZealPC Zeal60 System Control: device is a keyboard
[   206.143] (II) config/udev: Adding input device ZealPC Zeal60 (/dev/input/event8)
[   206.143] (**) ZealPC Zeal60: Applying InputClass "libinput keyboard catchall"
[   206.143] (II) Using input driver 'libinput' for 'ZealPC Zeal60'
[   206.143] (**) ZealPC Zeal60: always reports core events
[   206.143] (**) Option "Device" "/dev/input/event8"
[   206.143] (**) Option "_source" "server/udev"
[   206.151] (II) event8  - ZealPC Zeal60: is tagged by udev as: Keyboard
[   206.151] (II) event8  - ZealPC Zeal60: device is a keyboard
[   206.152] (II) event8  - ZealPC Zeal60: device removed
[   206.180] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:FEED:6060.000B/input/input12/event8"
[   206.180] (II) XINPUT: Adding extended input device "ZealPC Zeal60" (type: KEYBOARD, id 13)
[   206.180] (**) Option "xkb_model" "pc105"
[   206.180] (**) Option "xkb_layout" "us"
[   206.180] (WW) Option "xkb_variant" requires a string value
[   206.180] (WW) Option "xkb_options" requires a string value
[   206.194] (II) event8  - ZealPC Zeal60: is tagged by udev as: Keyboard
[   206.194] (II) event8  - ZealPC Zeal60: device is a keyboard
[   206.200] (II) config/udev: Adding input device ZealPC Zeal60 (/dev/input/event5)
[   206.200] (**) ZealPC Zeal60: Applying InputClass "libinput keyboard catchall"
[   206.200] (II) Using input driver 'libinput' for 'ZealPC Zeal60'
[   206.200] (**) ZealPC Zeal60: always reports core events
[   206.200] (**) Option "Device" "/dev/input/event5"
[   206.200] (**) Option "_source" "server/udev"
[   206.208] (II) event5  - ZealPC Zeal60: is tagged by udev as: Keyboard
[   206.208] (II) event5  - ZealPC Zeal60: device is a keyboard
[   206.209] (II) event5  - ZealPC Zeal60: device removed
[   206.228] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:FEED:6060.0008/input/input9/event5"
[   206.228] (II) XINPUT: Adding extended input device "ZealPC Zeal60" (type: KEYBOARD, id 14)
[   206.228] (**) Option "xkb_model" "pc105"
[   206.228] (**) Option "xkb_layout" "us"
[   206.228] (WW) Option "xkb_variant" requires a string value
[   206.229] (WW) Option "xkb_options" requires a string value
[   206.243] (II) event5  - ZealPC Zeal60: is tagged by udev as: Keyboard
[   206.243] (II) event5  - ZealPC Zeal60: device is a keyboard
[   206.249] (II) config/udev: Adding input device ZealPC Zeal60 Consumer Control (/dev/input/event7)
[   206.249] (**) ZealPC Zeal60 Consumer Control: Applying InputClass "libinput keyboard catchall"
[   206.249] (II) Using input driver 'libinput' for 'ZealPC Zeal60 Consumer Control'
[   206.249] (**) ZealPC Zeal60 Consumer Control: always reports core events
[   206.249] (**) Option "Device" "/dev/input/event7"
[   206.249] (**) Option "_source" "server/udev"
[   206.257] (II) event7  - ZealPC Zeal60 Consumer Control: is tagged by udev as: Keyboard
[   206.257] (II) event7  - ZealPC Zeal60 Consumer Control: device is a keyboard
[   206.258] (II) event7  - ZealPC Zeal60 Consumer Control: device removed
[   206.280] (II) libinput: ZealPC Zeal60 Consumer Control: needs a virtual subdevice
[   206.280] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:FEED:6060.0009/input/input11/event7"
[   206.280] (II) XINPUT: Adding extended input device "ZealPC Zeal60 Consumer Control" (type: MOUSE, id 15)
[   206.281] (**) Option "AccelerationScheme" "none"
[   206.282] (**) ZealPC Zeal60 Consumer Control: (accel) selected scheme none/0
[   206.282] (**) ZealPC Zeal60 Consumer Control: (accel) acceleration factor: 2.000
[   206.282] (**) ZealPC Zeal60 Consumer Control: (accel) acceleration threshold: 4
[   206.297] (II) event7  - ZealPC Zeal60 Consumer Control: is tagged by udev as: Keyboard
[   206.297] (II) event7  - ZealPC Zeal60 Consumer Control: device is a keyboard
[   206.298] (**) ZealPC Zeal60 Consumer Control: Applying InputClass "libinput keyboard catchall"
[   206.298] (II) Using input driver 'libinput' for 'ZealPC Zeal60 Consumer Control'
[   206.298] (**) ZealPC Zeal60 Consumer Control: always reports core events
[   206.298] (**) Option "Device" "/dev/input/event7"
[   206.298] (**) Option "_source" "_driver/libinput"
[   206.298] (II) libinput: ZealPC Zeal60 Consumer Control: is a virtual subdevice
[   206.298] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:FEED:6060.0009/input/input11/event7"
[   206.298] (II) XINPUT: Adding extended input device "ZealPC Zeal60 Consumer Control" (type: KEYBOARD, id 16)
[   206.298] (**) Option "xkb_model" "pc105"
[   206.298] (**) Option "xkb_layout" "us"
[   206.298] (WW) Option "xkb_variant" requires a string value
[   206.298] (WW) Option "xkb_options" requires a string value

```

---

### Post by Yoodle on 2021-12-05
> **MAFoElffen said:**
> 
That is the part that worries me... That it does NOT see anything connected.


Ok, that is bizarre.  It's definitely connected, because the rainbow splash screen comes up, and then I get a blinking cursor for a bit before the TV just goes to "can't find source".

---

### Post by Yoodle on 2021-12-05
> **tea for one said:**
> To establish if you are using Wayland or Xorg, open a terminal and enter:-
```
echo $XDG_SESSION_TYPE
```

When I do that, it just comes back with "tty".
I'm guessing it's because I'm SSH'd into the Pi.  The screen never comes up, so SSH is the only way I can manage the box.

---

### Post by tea for one on 2021-12-05
> **Yoodle said:**
> When I do that, it just comes back with "tty".
I'm guessing it's because I'm SSH'd into the Pi.  The screen never comes up, so SSH is the only way I can manage the box.

If you use your monitor (mentioned in post no. 1), I expect the info would display successfully?

---

### Post by MAFoElffen on 2021-12-05
Since it is creating an Xorg.0.log file, it is using XServer... Besides, I and everyone I know has problems running Wayland on Raspberry Pi, because it is just a FrameBuffer, with Vulkan V3DV graphics in the Mesa graphic stack for Raspberry Pi 4's...

The default on the RaspPi Images from Ubuntu is XServer. Most people do not realize that HDMI port 1 is the only port that supports 4k @ 60 Hz, where both HDMI ports support 4k @ 30Hz.

I know. it's almost 2am here... But I just got off work. Let me look at a few things here on my Pi4, that TV, and a few other things. I just finished a new update to my Forums 'system-info' script and that update is in Test, before pushing those changes to Stable, so I have a few... After I get off work, it takes me a bit to wind down enough to sleep.

In the meanwhile, please post your current boot.txt and usercfg.txt files, wrapped within code tags.I want to ensure your link from your config.txt file is hitting your usercfg.txt file and including it.

---

### Post by Yoodle on 2021-12-05
When you say boot.txt, I assume you mean config.txt, right?

Here it is:
```
yoodle@ubuntu-pi:~$ cat /boot/firmware/config.txt
[pi4]
max_framebuffers=2

[all]
kernel=vmlinuz
cmdline=cmdline.txt
initramfs initrd.img followkernel

# Enable the audio output, I2C and SPI interfaces on the GPIO header
dtparam=audio=on
dtparam=i2c_arm=on
dtparam=spi=on

# Enable the KMS ("full" KMS) graphics overlay, and allocate 128Mb to the GPU
# memory. The full KMS overlay is required for X11 application support under
# wayland
dtoverlay=vc4-kms-v3d
gpu_mem=128

# Uncomment the following to enable the Raspberry Pi camera module firmware.
# Be warned that there *may* be incompatibilities with the "full" KMS overlay
#start_x=1

# Comment out the following line if the edges of the desktop appear outside
# the edges of your display
disable_overscan=1

# If you have issues with audio, you may try uncommenting the following line
# which forces the HDMI output into HDMI mode instead of DVI (which doesn't
# support audio output)
#hdmi_drive=2

# If you have a CM4, uncomment the following line to enable the USB2 outputs
# on the IO board (assuming your CM4 is plugged into such a board)
#dtoverlay=dwc2,dr_mode=host

# Config settings specific to arm64
arm_64bit=1
dtoverlay=dwc2
include usercfg.txt
```


```
yoodle@ubuntu-pi:/boot/firmware$ cat usercfg.txt
hdmi_cvt=3840 2160 60 3 0 0 0
hdmi_group=2
hdmi_mode=87
```


Today I spent way too much time trying some other things (it's personal now :x).
Some background:  As I mentioned in my first post, I previously had Raspian working on this Pi and TV, and it worked for about a year.  But, the file system got corrupted, and it will no longer boot.  But, the boot output still comes up on the screen before it dies telling me the file system is corrupt.  So, today, I tried to see if I could fix that just to see what resolutions I had used for that, but I had absolutely zero luck there.

So, I tried installing Raspian to another SD card to see if maybe I could get that to work again.  Unfortunately, I had the same results as I did with Ubuntu.  So, I don't know how I ever got this working with Raspian in the first place.  I thought I did the initial config on a monitor, and then moved it to the TV, because I remember the resolution being so high that I couldn't read the text on the screen, so I had to lower the resolution.  But, I did all that while it was connected to the TV.

Let me know if you have any more ideas, and thank you for taking all the time to help me through all of this.

---

### Post by MAFoElffen on 2021-12-06
LMAO!!! Understood. A year ago on Black Friday, I got a screaming deal on a 43" 4K TV, and connected my Desktop to it. As my Desktop has high-end NVidia, I was excited... Until I could not read what was there, and I kept loosing track of the mouse cursor, because at that resolution, it was so small!!! I can do it... But settled on a lower resolution.

I do the same. I have about 10 micro sd cards setup with different systems for my Pi4. One is with Ubuntu 22.04 Dev, CentOS Stream 8, Debian 11, Ubuntu MATE, etc. My daily on my Pi4 is Ubuntu 20.04, which I installed from the Ubuntu 20.04 LTS Server Edition Image. It is far from being out-of-the box.

I'll probably be slammed or scolded for saying this, but the most stable out-of-the-box for Pi is Ubuntu MATE. The founder is a Pi enthusiast, so included a lot of hacks from Raspbian into MATE, as well as a lot of his own work. He is very proud of what he has accomplished and rightly so. He personally takes pride and  ownership of what is his own. My son somehow knows him, and talks very highly of his work on MATE. That says a lot, since my son is also involved with 'Computers', as a Senior Systems Engineer... third generation in our family, in this Industry.

I can see that the include line in your file points correctly 'to' your usercfg.txt file, so have no idea why that is not honoring those settings yet... This is just weird. My 4K is not a Samsung, nor the same model. I might have to try a few things tomorrow to see what mine does, connected to my 4K TV. LOL

Maybe when I wake up tomorrow. I have the next two days off...

---

### Post by Yoodle on 2021-12-14
> **MAFoElffen said:**
> 
I'll probably be slammed or scolded for saying this, but the most stable out-of-the-box for Pi is Ubuntu MATE. The founder is a Pi enthusiast, so included a lot of hacks from Raspbian into MATE, as well as a lot of his own work.

YES!!!!!!  MATE did the trick!!!!  I downloaded 20.04.1 and it recognized the TV on first boot and configured beautifully.  I did have some issues with there being no sound when I first started up, but I played around with it a bit, and it started working (honestly, not sure what actually fixed it).  I really wish I would have tried MATE before I went through trying, literally, 53 different hdmi/group settings in my usercfg.txt file on the standard Ubuntu without any success.

I am also going to try setting up another SD card with Ubuntu 20.04.3 and see if that works.  Since the MATE 20.04.1 worked, I'm wondering if it may just be a thing with 21.10.  I'll update here with my findings.

Thanks again for all your help!

---

### Post by MAFoElffen on 2021-12-17
How I installed 20.04 on my Raspberry Pi4... I download the Ubuntu Server 20.04 LTS image. I installed package 'ubuntu-desktop'. The I installed gnome-sessions. Then for sound tweaks, I installed Dmitry Kann's PPA at  [https://launchpad.net/~yktooo/+archive/ubuntu/ppa](https://launchpad.net/~yktooo/+archive/ubuntu/ppa)  to install package 'indicator-sound-switcher', which is a sound fix package from MATE. the my user.cfg file.

I use the same recipe for my testing of 22.04, which I started out as 20.04 from above, then converted / release upgraded to... for testing and verifying the DEV/TEST.

---

