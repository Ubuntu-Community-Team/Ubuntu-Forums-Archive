---
title: "DVI not working with NVIDIA card and ASUS mainboard"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by marciano#1 on 2016-12-03
I moved from an old computer with dual DVI GeForce card I used with two VGA adapters to use dual monitors to a new one with

[LIST]
[*]ASUS H110M-R mainboard with VGA and DVI inputs
[*]GeForce GT-730 graphics card with VGA and DVI inputs
[/LIST]

I've installed 16.04 on it.

If I connect both VGA displays to each of VGA ports (mainboard and video card) I get a regular dual monitor configuration but none of DVI-D ports (with VGA adapters) output signal to respective displays.

I tried several things I've read, installing new drivers, dealing with X, nouveau and other stuff at the point I only got single monitor.
So I reinstalled 16.04 to start over.

So my question is how to enable DVI output at least in my GT-730

---

### Post by #&amp;thj^% on 2016-12-03
Just curious if you have tried adding the "[COLOR=#333333][FONT=&amp]`nomodeset`[/FONT][/COLOR]" to grub yet?
I had the same problem with 14.04 (Trusty) and that worked for me.
Now I just use HDMI and all is good.
Regards
```
inxi -M -G
Machine:   Device: desktop Mobo: ASUSTeK model: M3A32-MVP DELUXE v: Rev 1.xx
           BIOS: American Megatrends v: 2104 date: 07/05/2010
Graphics:  Card: NVIDIA GF106 [GeForce GTS 450]
           Display Server: X.Org 1.18.4 driver: nvidia
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTS 450/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 375.20

```

---

### Post by marciano#1 on 2016-12-03
No, I don't know anything about nomodeset.

> Machine:   Mobo: ASUSTeK model: H110M-R v: Rev X.0x
           Bios: American Megatrends v: 1802 date: 05/26/2016
Graphics:  Card-1: Intel Sky Lake Integrated Graphics
           Card-2: NVIDIA GK208 [GeForce GT 730]
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa) [COLOR="#FF0000"]FAILED[/COLOR]: nouveau
           Resolution: 1366x768@59.79hz, 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 11.2.0


---

### Post by #&amp;thj^% on 2016-12-03
> **marciano#1 said:**
> No, I don't know anything about nomodeset.
Yikes! I have no experince with hybrid Graphics...and without the nvidia driver installed, it is kind of a mute point here. 
Sorry about that.

---

### Post by marciano#1 on 2016-12-03
I inserted "nomodeset" between "ro" and "splash" in grub but only got one monitor.

I have to dig about [COLOR="#FF0000"]Failed[/COLOR] Nouveau.

I didn's have change anything in system settings.   That's what I get after a fresh ubuntu install

Thanks

---

### Post by #&amp;thj^% on 2016-12-03
Well it would look like this:
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR=#ff0000]**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**[/COLOR]
GRUB_CMDLINE_LINUX=""

```Followed by
```
sudo update-grub

```But you **really should have** the Nvidia Proprietary driver installed.

---

### Post by marciano#1 on 2016-12-03
With nomodeset I also lose nvidia VGA output.
The same happens if I change the drivers from nouveau to nvidia 340 or 367 that are already installed

> Machine:   Mobo: ASUSTeK model: H110M-R v: Rev X.0x
           Bios: American Megatrends v: 1802 date: 05/26/2016
Graphics:  Card-1: Intel Sky Lake Integrated Graphics
           Card-2: NVIDIA GK208 [GeForce GT 730]
           Display Server: X.Org 1.18.3 driver: **nvidia**
           Resolution: 1366x768@59.79hz
           GLX Renderer: GeForce GT 730/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 367.57


---

### Post by marciano#1 on 2016-12-04
I remembered I have a VGA - HDMI adapter I used to use with my Apple TV and a VGA monitor.
I put back nemodeset and now both displays are good using Nvidia VGA and HDMI port (your configuration)
DVI is still missing

---

