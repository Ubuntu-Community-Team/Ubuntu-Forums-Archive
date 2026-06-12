---
title: "Setting up Video Surveillance Camera on Zoneminder"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by omariusa on 2010-03-23
I currently have eight surveillance cameras setup that used to connect to a windows pc. I decided to throw away the old computer, take the dvr card from the old computer and use it in a new computer with ubuntu 9.10. However, till now I can't get the cameras to work. 

I installed Zoneminder, and followed instructions from here and there with no useful results. What I currently have are monitors showing black screens, with the fps showing.

[IMG]http://img406.imageshack.us/img406/5610/screenshotoja.png[/IMG]

I am pretty much still a noob, so I am not sure where I went wrong. I do not get anything when i run XawTV (or maybe i don't know how to run it right).

when i run "lspci | grep Bt878" I get this
```
0b:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0b:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0b:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0b:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0b:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0b:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0b:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0b:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0b:0c.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0b:0c.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0b:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0b:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0b:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0b:0e.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0b:0f.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0b:0f.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```Following instructions from various places, this is what I have for the following files

 /etc/modules :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
bttv
options
``` /etc/modprobe.d/bttv :
```
alias char-major-81 videodev
alias char-major-81-0 bttv
```/etc/modprobe.d/options :
```
options bttv card=77,77,77,77,77,77,77,77,77
```I followed the instructions for installing Zoneminder on Ubuntu 9.10:
[http://www.zoneminder.com/wiki/index.php/Ubuntu_9.10_Desktop](http://www.zoneminder.com/wiki/index.php/Ubuntu_9.10_Desktop)

I also get some tips for setting up the tv card:
[http://ubuntuforums.org/showthread.php?t=153935](http://ubuntuforums.org/showthread.php?t=153935)

What is confusing is I get a fps rate, which is a sign that the camera is working, but all i get is a black screen. The cameras used to work in the original windows setup, so i doubt that the cameras are not working.

 Thanks in advance.

---

### Post by djchandler on 2010-03-23
I'm as much in the dark as you are with this, pun not intended. But I would download one of the "live" CDs and see if any of those will recognize your hardware properly.

[http://www.zoneminder.com/downloads.html](http://www.zoneminder.com/downloads.html)

and scroll down to **Other Downloads**. ZoneMinder LiveCD v1.22.2 looks like what I would try. I see nothing wrong in your setup, unless it is this line in options:

options bttv card=77,77,77,77,77,77,77,77,77

What I'm reading says that's the options for a 4 port card. Don't you have 8 ports? Or are two cameras attached somehow to each port?

> What is confusing is I get a fps rate, which is a sign that the camera is working, but all i get is a black screen. The cameras used to work in the original windows setup, so i doubt that the cameras are not working.

Yes, that is confusing. A black screen with composite video cable input (not RF) would give a black screen if the camera is not functional or connected.

---

### Post by carlexpc on 2010-06-10
@omariusa

it seems like you are using an 8-channel 8-chip bttv card. try to enter the following in /etc/modprobe.d/bttv.conf

options i2c-algo-bit bit_test=1
options bttv gbuffers=32 card=102,102,102,102,102,102,102,102 tuner=0 radio=0 coring=1 full_luma_range=1 chroma_agc=1 pll=1 combfilter=1 autoload=0 triton1=0

---

