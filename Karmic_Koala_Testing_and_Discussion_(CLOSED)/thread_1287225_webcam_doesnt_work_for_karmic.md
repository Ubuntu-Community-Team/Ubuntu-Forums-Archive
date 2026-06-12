---
title: "webcam doesnt work for karmic"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by libihero on 2009-10-09
my webcam used to work in intrepid... but now it dont work on karmic :(
anything i can do to fix it?
funny thing is my mic used to not work on intrepid and now it does here haha

---

### Post by taavikko on 2009-10-10
Is system really up-to-date (using main-server)
what kind of an webcam (lspci; lsusb)

does "gstreamer-properties" video-tab show any images?

---

### Post by libihero on 2009-10-10
here's my lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```
how do i tell if it's updated from the main server? i just do the normal updates from update manager
and gstreamer just shows colors n static

---

### Post by libihero on 2009-10-10
on cheese here's what it gives me on the options for choosing webcam

---

### Post by libihero on 2009-10-13
bump :(

---

### Post by VMC on 2009-10-13
> **libihero said:**
> bump :(

You didn't output "lsusb".

Also, did you do the video test of "gstreamer-properties" as per Taav request.

---

### Post by andresmh on 2009-10-14
You should submit it as a bug to launchpad. Not sure what package though.

---

### Post by emarkay on 2009-10-14
> **andresmh said:**
> You should submit it as a bug to launchpad. Not sure what package though.

I wouldn't recommend it - there is still info the OP never gave - for all we know it's not plugged in...  :)

---

### Post by libihero on 2009-10-14
oops sorry!
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device

```

---

### Post by hewbert on 2009-10-17
> **libihero said:**
> oops sorry!
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device

```

Have you tried pointing it at a lamp or something else bright?  Seriously.  Mine is a completely black screen, but if I point it at a lamp, I can see it.

I resolved this somehow a couple of weeks ago, but can't remember how.

If this is the issue you're having, I'll post back here once I remember :)

---

### Post by hewbert on 2009-10-17
Well, I'm not sure if we had similar problems, but you might try installing 'v4l2ucp' and playing with the settings in there.  If your camera is detected (looks like it), just a black screen, you may need to mess with the exposure.  Try the lamp thing.

---

### Post by libihero on 2009-10-17
my problem is it says "no camera found" :(

---

### Post by libihero on 2009-10-19
under gstreamer-properties, it says "Could not open device "/dev/video0" for reading and writing"

---

### Post by the.lost.one on 2009-10-19
i could not get my ricoh webcam to work on karmic no matter how many tutorials i tried.

it worked on jaunty for one or two apps but the video was way too dark to be useful

this problem everyone is having who has the same built in ricoh webcams in hp laptops (or several sony viao cams). i dont understand why they havent fixed it for such a long time. even VISTA worked out of the box for me when i bought it in february 2007

---

### Post by libihero on 2009-10-23
bump... :(
i was hoping the rc would have this fixed

---

### Post by libihero on 2009-10-27
I actually got it to work for a second.  i was here: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) and i tried putting this in terminal:
mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0
and my webcam turned on.  I then went onto cheese and that worked too.  i closed it, and i tried both afteerwards and it stopped working :(

---

### Post by libihero on 2009-10-27
ok i restarted again, and i got it to work
here is the output on my terminal, hope this can help somehow...
```
hamza@hamza-laptop:~$ mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: Gateway USB 2.0 Webcam
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
[VO_XV] Could not grab port 57.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...

```

---

### Post by jblackhall on 2009-10-27
Sounds like you've got a linux bug.  I had something similar happen to me after Ubuntu 8.10 was released.  Searching by your device id (04f2:b027) your product is supported with Linux UVC, so it looks like there's some sort of bug.  I'd Alt+F2 and run: "ubuntu-bug linux" (without quotes).  This will help you report the bug to launchpad and you can explain your situation and see if anyone can help.  My webcam finally started working correctly (and better than before) on Karmic, and it hadn't worked correctly since Ubuntu 8.04.  Hopefully yours doesn't take quite so long to sort out...  (Mainly I just had to wait for incremental fixes in the Linux kernel)

---

