---
title: "webcam problem and skype"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by blucenere on 2009-12-27
well i must install a Webcam and a sort of Usb-Phone for Skype

**My PC:**
Intel Core 2Duo 3Ghz 64bit
2Gb Ram
graphic card: G86 [GeForce 8500 GT] NVIDIA
audio device: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)

**OS:**
Ubuntu 9.10

**what i must install:**
Webcam Easy Touch Lotus ET-464
Internet Phone Easy Touch Traction ET-660

the command "lsusb" see only the webcam: *Bus 005 Device 003: **ID 0ac8:301b** Z-Star Microelectronics Corp. ZC0301 Webcam*

Skype can't see anything. If i go in the option and try to prove the webcam, skype exit and close itself
can't find a way to use the cam
pls can you help me?
thx:(

---

### Post by gradinaruvasile on 2009-12-27
First, press alt+f2, type gstreamer-properties, press enter. Go to the video tab, select at the "default input" "video for linux 2 (v4l2)", select device "pc camera", press test.
Is that working? If yes, follow the instructions below.

Launch Skype in a terminal with the following syntax:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

It should work if your camera can be seen with gstreamer-properties.

Make sure you have the latest Skype (2.1.0.47 beta). Its really stable, dont worry about the beta status.

As for the other thing, i have no idea, never used it such stuff.
What options do you have if you right-click on the system's sound icon in the tray, select preferences, and go to the input or output tab? There is a default sound device (internal) and if you connect a supported sound device by usb, bluetooth it should show up and you can route audio through it. But it has to have a driver in the kernel to work.

---

### Post by cozski on 2009-12-29
> **gradinaruvasile said:**
> First, press alt+f2, type gstreamer-properties, press enter. Go to the video tab, select at the "default input" "video for linux 2 (v4l2)", select device "pc camera", press test.
Is that working? If yes, follow the instructions below.

Launch Skype in a terminal with the following syntax:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

It should work if your camera can be seen with gstreamer-properties.

Make sure you have the latest Skype (2.1.0.47 beta). Its really stable, dont worry about the beta status.

As for the other thing, i have no idea, never used it such stuff.
What options do you have if you right-click on the system's sound icon in the tray, select preferences, and go to the input or output tab? There is a default sound device (internal) and if you connect a supported sound device by usb, bluetooth it should show up and you can route audio through it. But it has to have a driver in the kernel to work.

Hey, thanks for that... it at least confirmed that my webcam is working (even though the picture is upside down for some reason). I know that this has been a recurring problem when installing Skype with Ubuntu 9.10 for some people and it's been no different for me... which is basically that with my headset/mic I can hear people but they cant hear me. I've tried all sorts of suggestion from other posts, primarily related to the Pulse Sound Sever, OSS and ALSA configuration but still not resolved the problem. I downloaded the Debian Lenny version of Skype and bar sound/webcam (which is just alot of static in the image) not working, everything else appears fine. Any suggestions/signposts? 

Using Ubuntu 9.10
Webcam: Phillips SPC315NC

Thanks

---

