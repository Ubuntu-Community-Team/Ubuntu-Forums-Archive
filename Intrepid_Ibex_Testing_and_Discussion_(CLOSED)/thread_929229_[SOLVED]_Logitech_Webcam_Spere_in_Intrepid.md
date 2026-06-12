---
title: "[SOLVED] Logitech Webcam Spere in Intrepid"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2008-09-24
I tried plugging one of these in to see if it would get picked up. Sure enough it showed up as /dev/video0 and it works fine through VLC. One thing I was wondering. Under Windows, the Logitech software includes a little applet that allows you to control the camera, pan, tilt, zoom etc. Is there an equivalent for Ubuntu.

---

### Post by bruce89 on 2008-09-24
Not to my knowledge. Anyway, it's not real panning, as I have one of these devices as well. The image is moved around digitally, so a program could be made quite simply.

---

### Post by alphacrucis2 on 2008-09-24
> **bruce89 said:**
> Not to my knowledge. Anyway, it's not real panning, as I have one of these devices as well. The image is moved around digitally, so a program could be made quite simply.

The one I have is motorised. It actually pans and tilts for real. The zoom is probably digital though as a real motorised optical zoom would probably make them a bit more expensive

---

### Post by marmuta on 2008-09-25
There is luvcview in Intrepids repository, but it I like guvcview better.
[http://guvcview.berlios.de/]("http://guvcview.berlios.de/")

To get the zoom/tilt working you would need to start guvcview as root once after each reboot, or install libwebcam 
[http://www.quickcamteam.net/software/libwebcam]("http://www.quickcamteam.net/software/libwebcam"). 
libwebcam uses udev to enable the pan/tilt/focus and many more controls automatically. Then just start up luvcview or guvcview and the extended controls should work. 
libwebcam also comes with uvcdynctrl which lets you control pan/tilt/etc. from the command line.

The libwebcam+guvcview combo works quite well, at least with the Quickcam Sphere AF, not sure about the older Sphere MP though.

---

### Post by alphacrucis2 on 2008-09-25
:cool: Will give this a try tomorrow

---

### Post by alphacrucis2 on 2008-09-25
> **alphacrucis2 said:**
> :cool: Will give this a try tomorrow


Installed guvcview and tried it. Gave error:

Guvcview error:

Can't set MJPG or YUV stream for guvcview

Make sure you have a UVC compliant camera and that you have the linux UVC driver installed

According to this article it should be included with 7.10 and higher but maybe not with alpha versions? An lsmod showed no sign of it.

[https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

I followed the procedure for compiling and installing the module. lsmod now shows it but I still get the same error. VLC runs fine with the camera openning video0 but I presume it is working at a lower level interface. Any ideas?

---

### Post by marmuta on 2008-09-26
Interesting, VLC doesn't work for me. I believe it's because VLC 0.8.6 supports only VL1 devices and the uvcvideo driver might provide only VL2.

This should give an image, though YUV lowres (how do you ask mplayer for an mjpeg stream?):
```
mplayer tv:// -fps 15 -tv driver=v4l2:width=800:height=600:device=/dev/video0
```

If not, then maybe you should revert to Intrepids uvcvideo module. I've tried the svn version too but didn't really get it working.

This is mine:

```
$ modinfo uvcvideo
filename:       /lib/modules/2.6.27-4-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
version:        v0.1.0
license:        GPL
description:    USB Video Class driver
author:         Laurent Pinchart <laurent.pinchart@skynet.be>
srcversion:     F2CC7107729CB7FD81FD16A
...
depends:        usbcore,videodev,v4l1-compat,compat_ioctl32
vermagic:       2.6.27-4-generic SMP mod_unload modversions 586 
parm:           quirks:Forced device quirks (uint)
parm:           trace:Trace level bitmask (uint)

```

Oh and be sure to 
```
guvcvideo -d /dev/videoX
```
if you have multiple video devices, because it seems to pick the wrong one on occasion.

Or use this udev rule in /etc/udev/rules.d/50-mystuff.rules to
```
# give logitech sphere af a fixed device name
SUBSYSTEM=="video4linux", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="0994", NAME="video%n", SYMLINK+="webcam"

```
with 

```
guvcvideo -d /dev/webcam

```
.

Unplugging/replugging the camera after cheese/ekiga/vlc might help too.

---

### Post by Nerd_bloke on 2008-09-27
There are a number of different revisions of the Orbit/Sphere webcam, only the latest fully UVC compatible.
See listing here
[http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices)

---

### Post by alphacrucis2 on 2008-09-28
> **Nerd_bloke said:**
> There are a number of different revisions of the Orbit/Sphere webcam, only the latest fully UVC compatible.
See listing here
[http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices)

Thanks. My camera appears to be on the supported list. I have raised the issue with the guvcview dev and provided diagnostic info. Will report back here with the outcome. The issue appears to be related to v4l2.

EDIT: It turns out that it is an issue with my camera being an older one. The guvcview developer has informed me that the camera pixelformats are not currently supported. The good news is that he will be adding this support over the next couple of weeks. The bad news is that as Nerd_bloke implied my camera does an issue with UVC. So the updated guvcview will only support my camera in the same way that VLC does but the controls will not be available. I guess none of this has anything to do with 8.10 so I will mark as solved.

---

