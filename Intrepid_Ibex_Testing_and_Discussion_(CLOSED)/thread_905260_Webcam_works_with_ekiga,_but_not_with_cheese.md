---
title: "Webcam works with ekiga, but not with cheese"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TaTaE on 2008-08-30
Hi, 
   After upgrading to Intrepid, my webcam works OK with Ekiga, which detects the webcam as V4L2, channel 1, PAL.
   It doesn't work anymore with gstreamer, cheese, skype, camorama. When I had Hardy H., it needed some configuration, but I can't remember what were they.
   
   Here is my /var/log/messages:

Aug 30 12:39:51 apollo kernel: [12867.860026] usb 2-2: new full speed USB device using uhci_hcd and address 7
Aug 30 12:39:51 apollo kernel: [12868.044006] usb 2-2: configuration #1 chosen from 1 choice
Aug 30 12:39:51 apollo kernel: [12868.069488] gspca: probing 046d:08aa
Aug 30 12:39:52 apollo kernel: [12869.055075] zc3xx: probe sensor -> 0e
Aug 30 12:39:52 apollo kernel: [12869.055085] zc3xx: Find Sensor HDCS2020
Aug 30 12:39:52 apollo kernel: [12869.059354] gspca: probe ok
Aug 30 12:39:53 apollo pulseaudio[27906]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Aug 30 12:39:53 apollo pulseaudio[27906]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.

    I have a nvidia Geforce, using nvidia module. Compiz is disabled.
    Also:

$ ls -ls /dev/video0 
0 crw-rw----+ 1 root video 81, 0 2008-08-30 13:59 /dev/video0

---

### Post by TaTaE on 2008-08-30
Testing with gstreamer:


$ gst-launch-0.10 v4l2src device=/dev/video0 ! xvimagesink
Setting pipeline to PAUSED ...

(gst-launch-0.10:16970): GStreamer-WARNING **: pad v4l2src0:src returned caps which are not a real subset of its template caps
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Could not negotiate format
Additional debug info:
gstbasesrc.c(2436): gst_base_src_start (): /pipeline0/v4l2src0:
Check your filtered caps, if any
Setting pipeline to NULL ...
FREEING pipeline ...

$

---

### Post by TaTaE on 2008-08-31
bump

---

### Post by TaTaE on 2008-09-07
bump.

---

### Post by TaTaE on 2008-09-07
I found a bug recently opened, which describes perfectly this situation:

[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/266879](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/266879)

---

### Post by TaTaE on 2008-09-09
bump?
(this is the last bump)

---

### Post by RAOF on 2008-09-09
> **TaTaE said:**
> Testing with gstreamer:


$ gst-launch-0.10 v4l2src device=/dev/video0 ! xvimagesink
Setting pipeline to PAUSED ...
...
$

This here isn't likely to work; chances are your webcam doesn't have the ability to output video in a size/format/colourspace that xvimagesink can handle.  You could try adding a "! videoscale ! ffmpegcolorspace !" between the source and the sink; that might give better results.

---

### Post by TaTaE on 2008-09-12
that doesnt work either. I rather suspect something related to the kernel and drivers

---

### Post by TaTaE on 2008-09-28
if it worked in hardy , and not in intrepid , IT IS certainly a bug.

---

