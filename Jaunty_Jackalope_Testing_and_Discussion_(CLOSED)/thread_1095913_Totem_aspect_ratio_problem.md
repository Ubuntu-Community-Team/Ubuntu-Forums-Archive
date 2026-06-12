---
title: "Totem aspect ratio problem"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lamborghiniwang on 2009-03-14
It seems totem can't get the aspect ratio right for some 4:3 video, including both MPEG2 and Xvid .avi files. I have a 4:3 screen and but it has two black columns on both side of the screen when playing 512x384 avi files in totem at full screen mode. It seems the problem only appears in Totem Jaunty. 

Does anyone else have the same problem?

---

### Post by Nullack on 2009-03-14
It might be encoded anomorphically

Host a sample online so I can look at it if you want to me look deeper at it. You can use DD command to cut the file size down into a sample.

---

### Post by lamborghiniwang on 2009-03-14
The sample file is uploaded [here]("http://www.myricci.com/sample.avi").
Thanks for spending time looking into this. :D

---

### Post by Nullack on 2009-03-14
My friend go into totem preferences and tick the box for automatically adjusting video size and that will fix it :) It works fine then in Totem.

---

### Post by lamborghiniwang on 2009-03-14
> **Nullack said:**
> My friend go into totem preferences and tick the box for automatically adjusting video size and that will fix it :) It works fine then in Totem.

er... I tried both check and uncheck the option for automatically adjust video size but the problem remains. btw, not sure if it is related, but I get this msg when playing the video from CLI:
```

$ totem sample.avi
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

```

---

### Post by Nullack on 2009-03-14
What gstreamer plugins do you have installed?

You are using the gstreamer backend?

---

### Post by lamborghiniwang on 2009-03-14
The only plugins I've enabled is the BBC viewer and the Youtube browser, and yes gstreamer is the backend.

---

### Post by Nullack on 2009-03-14
Install the ffmpeg gstreamer plugin and it should be fixed

---

### Post by lamborghiniwang on 2009-03-14
ok, here are the plugins that I installed(in my previous reply I thought u meant the ones in the "plugins" menu in totem):

```

$ dpkg --get-selections| grep gstreamer
bluez-gstreamer					install
gstreamer0.10-alsa				install
gstreamer0.10-ffmpeg				install
gstreamer0.10-gnomevfs				install
gstreamer0.10-plugins-bad			install
gstreamer0.10-plugins-bad-multiverse		install
gstreamer0.10-plugins-base			install
gstreamer0.10-plugins-base-apps			install
gstreamer0.10-plugins-good			install
gstreamer0.10-plugins-ugly			install
gstreamer0.10-plugins-ugly-multiverse		install
gstreamer0.10-pulseaudio			install
gstreamer0.10-schroedinger			install
gstreamer0.10-tools				install
gstreamer0.10-x					install
libgstreamer-plugins-base0.10-0			install
libgstreamer0.10-0				install
phonon-backend-gstreamer			install
totem-gstreamer					install

```

I tried reinstall ffmpeg gstreamer plugin but still the same problem. Any suggestions? Would this be related to the fact that I'm running a 64-bit os?

---

### Post by Nullack on 2009-03-14
I cant replicate the problem, but for you, to narrow down the debugging install the gstreamer tools and run a command similar to this to remove totem from the situation and just use gstreamer to see if its still a problem:

gst-launch -v playbin uri=file:////home/nullack/Downloads/sample.avi

---

### Post by lamborghiniwang on 2009-03-15
Help! I just realize that this problem now also appears in Intrepid. I tried the gst-lauch method and attached is the output. I think the following line has something to do with the problem. It seems Totem just automatically set the aspect ratio into 1:1 even it detects the movies is 512x384.

```

/GstPlayBin:playbin0/GstBin:vbin/GstIdentity:id.GstPad:sink: caps = video/x-raw-yuv, width=(int)512, height=(int)384, framerate=(fraction)2997003/100000, format=(fourcc)I420, pixel-aspect-ratio=(fraction)1/1

```

My monitor is the default 1400x1050 LCD screen on a Thinkpad T61p, with Nvidia 180.37 driver. I tried manually set the aspect ratio to 4:3 in totem, but it doesn't do anything at all.
Any suggestion?

---

### Post by lamborghiniwang on 2009-03-15
OK, I found the solution myself. :D
It seems I need to add a line specify the DPI into /etc/X11/xorg.conf, the device section for the nvidia card looks like this:

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation" 
**    Option      "DPI"   "96x96"**
EndSection

```

I guess it has to do with the fact that I set the DPI for font of Gnome to 96 in the first place. 

:D

---

