---
title: "Latest 8.04.1/ 9.1 auto-updates break CHEEZE"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by nss0000 on 2010-02-20
Gents:

I run x64_U_8.04.1LTS & x32U_9.1 on different kit. The older U_8.04.1 installation uses an NV7600 vidcard, while U_9.1 uses an NV9800gtx+. Both systems have been stable, performed well and regularly auto.updated. Both kits include LogiTek WebCams which have always worked without issue.    

The latest < FireFox+stuff > auto.updates killed both webcam video-functions while <PHOTO> is preserved on the U_8.04.1 system. So I can take a "still" on one system & motion_video on neither. I nominally use both Camorama & Cheeze ... both now misfunction.

Entering  a <LSUSB> command shows the presence of a webcam on both systems. Advice for restoring webcam function ?? 

**BTW** U_9.1 has something of a snarky reputation; I've been lucky with mine. OTOH the U_8.04.1_LTS system is my "production" box &  has been rock-solid for years. Whatever serious work I do at home gets done on that box and I depend on it. I am not happy whatsoever that an update broke one of its functions @@@ it's cavalier behavior by the maintainers  & I am not happy at all.

---

### Post by gordintoronto on 2010-02-20
I run 64-bit 9.04 and keep it up to date.  Cheese records videos just fine.  My cam:
Bus 006 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam 

Video is 9400 GT.

---

### Post by nss0000 on 2010-02-21
This morning trying to <run> CHEESE I get "fuzzed" pic_frame & the error message:


** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/ME/.gnome2/cheese/media/0004.ogg'
Reason: Stream contains no data..

---

### Post by no2498 on 2010-02-24
try getting the program ( wxcam )
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2click the bottom test button 
after you get a pic set the top of the window to xwindow (no xv)
and do not open cheese

---

### Post by nss0000 on 2010-03-08
> **no2498 said:**
> try getting the program ( wxcam )
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2click the bottom test button 
after you get a pic set the top of the window to xwindow (no xv)
and do not open cheese

The segfault occurs when I hit the <TEST> button: 

gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
Segmentation fault

I immediately ran CHEESE ... for 3-seconds I got proper images ... then BSOD and subsequent attempts fail to provide any image whatsoever. How very weird.

---

